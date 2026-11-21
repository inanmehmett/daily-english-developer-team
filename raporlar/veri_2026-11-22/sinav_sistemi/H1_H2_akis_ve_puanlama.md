# H1 ve H2 – Üç ölçmenin akışı, puanlama ve seviye kararı (koddan)

**Tarih:** 22 Kasım 2026 · **Kimden:** editör · **Kime:** Charles
**Bakılan kod:** sunucu `master` (5881a30), uygulama `feat/journey-core` (0039a0ac). Dosya yolları sunucu deposuna göre; uygulama dosyaları `lib/` ile başlar.

## Önce: üç değil iki test var
| Uygulamadaki ad | Sunucudaki motor | Nereden açılır |
|---|---|---|
| **İlk yerleştirme (onboarding)** | Ayrı bir test **yok**. Kullanıcı seviyesini bir listeden **kendisi seçer** (`step_05_level.dart`). Altında "emin değilsen ölçelim" bağlantısı var; o da aşağıdaki "yeniden ölç" testini açar | Onboarding seviye adımı |
| **"Seviyeni yeniden ölç"** | Yerleştirme (`Services/Placement/`) | Profil satırı; ana sayfadaki seviye ölçüm kartı; onboarding bağlantısı |
| **"Seviyeni belgele"** | Değerlendirme (`Services/Assessment/`) | Yalnız profil satırı |

Sunucuda başlangıç sorulu eski bir yerleştirme yolu da duruyor (`POST /api/Placement/start`: "beginner / some / good" → A1 / A2 / B1). Uygulamada onu çağıran yer yok; kullanılmıyor.

Her iki test de seviyeyi **aynı kapıdan** profile yazar (`LevelReadinessService.RecordMeasuredLevelAsync`) ve ikisi de seviyeyi **düşürebilir**. Tek istisna aşağıda ("yalnız yükselt").

---

## A. "Seviyeni yeniden ölç" (yerleştirme)

### Akış
1. **Tanıtım ekranı** (uygulama, `level_measure_view.dart`). "Başla"ya basınca tur açılır.
2. **Kelime taraması** (`PlacementService.StartRemeasureAsync`, `PickVocabItemsAsync`): 30 kelime tek tek gösterilir; her biri için "biliyorum / bilmiyorum".
   - 5 banttan (A1, A2, B1, B2, C1) **4'er gerçek kelime** = 20, artı **10 sözde kelime**; hepsi rastgele seçilir ve karıştırılır. Havuz: bant başına 12 gerçek kelime, 35 sözde kelime.
   - Başlangıç sorusu yok; kullanıcının beyanı ya da mevcut seviyesi kullanılmaz (tarama havuzu boşsa mevcut seviyeden başlar; bugün boş değil).
3. **Boşluk doldurma parçaları** (`AnswerVocabularyAsync`, `AnswerAsync`): taramanın kestirdiği banttan bir parça gelir. Parça 3 boşluk içerir; her boşluk 3 şıklı. En çok **3 parça**.
   - Parça seçimi: o seviyeden, bu turda ve kullanıcının önceki turunda sunulmamış rastgele bir parça. Seviye başına 6 etkin parça var (A1–B2). Havuz o kadar daralmışsa önceki turun elemesi kalkar.
4. **Sonuç ekranı:** yeni seviye, öncekiyle karşılaştırma ("Seviyen yükseldi / Aynı seviyedesin / Seviyeni güncelledik").

### Yarıda çıkarsa
Tur açık kalır (`InProgress`). Kullanıcı yeniden girince **kaldığı yerden** sürer; yeni tur açılmaz. Zaman aşımı yok. Açık tur hak yakmaz.

### Puanlama ve seviye kararı
**Kelime taraması** (`VocabularyScanScorer.cs`):
- Yanlış alarm = sözde kelimelere "biliyorum" denen oran.
- Bir bant "biliniyor" sayılır ⇔ o banttaki "biliyorum" oranı − yanlış alarm **≥ 0,5**.
- Bantlar kolaydan zora yürünür, **ilk düşen bantta durulur** (bitişik karar): üstteki bir bandı bilmek alttakini kurtarmaz.
- Yanlış alarm **≥ 0,5** ise tarama güvenilmez: başlangıç A1.
- Hiç bant geçilmezse Pre-A1 kestirilir; parça yine A1'den başlar (Pre-A1 parçası yok). C1 kestirilirse parça B2'den başlar (tavan B2).
- Tarama yalnız **başlangıcı** seçer; sonucu parçalar belirler.

**Parçalar** (`PlacementDecisionEngine.cs`; B = parça başına boşluk = 3):
| Parça puanı | Ne olur |
|---|---|
| 3/3 | Bir üst seviye. Tavandaysa (B2) ya da 3. parçaysa orada biter |
| 0/3, turun **ilk** parçası | Bir alt seviyeden **teyit parçası**. Teyitte ≥ 2/3 → o alt seviye; altı → bir daha alt. (A1'de teyit yine A1'den gelir; geçilemezse sonuç **Pre-A1**) |
| 0/3, sonraki parça | Bir alt seviye, biter |
| 1/3 ya da 2/3 | Aynı seviyeden **ikinci parça**. İki parçanın toplamı ≥ 4/6 → o seviye; altı → bir alt |

- Sonucun aralığı: **Pre-A1 – B2**. C1 ve C2 ölçülmez.
- En kısa tur: 1 parça (B2'de 3/3). Tipik: 2–3 parça.
- Kod içi yorumların bir kısmı eski 2 boşluklu döneme ait sayılar taşıyor ("≥3/4", "0/2"); geçerli olan yukarıdaki tablo. Eşikler ayar dosyasından okunuyor ve birbirleriyle tutarlılığı açılışta denetleniyor (`PlacementOptionsValidator`).

**Süre koruması** (`AnswerAsync`):
- Parçanın alt sınırı = kelime sayısı ÷ 300 kelime/dk + boşluk başına 3 sn. Altında kalan parça **puanlanmaz**, aynı seviyeden yenisi gelir ("çok hızlı" uyarısıyla).
- İkinci kez olursa tur **güvenilmez** biter: seviye yazılmaz, hak yanmaz.
- Alt sınırın 5 katından uzun süren parça ya da metinde kelimeye dokunma yalnız **iz** bırakır (`Suspicious`); sonuç yine yazılır.

**Hak** (`GetRemeasureAvailabilityAsync`): 7 günde en çok 3 tamamlanmış ölçüm; iki ölçüm arası en az 24 saat.

**"Yalnız yükselt" kuralı** (`FinishAsync`): tur `Offer` işaretiyle başladıysa (uygulamanın ana sayfada teklif ettiği ölçüm) sonuç mevcut seviyenin altındaysa **mevcut seviye korunur**. Kullanıcının kendi başlattığı turda (`User`) sonuç neyse o yazılır. Bugüne kadar uygulama hep `User` gönderdi; ana sayfa kartının `Offer` göndermesi derleme 50 ile geliyor. Canlıdaki 118 müşteri turunun hepsi `User`.

### Kayıt
`PlacementSessions.Raw` (JSON): sunulan kelimeler, kestirilen bant, yanlış alarm, sunulan parçalar, **her boşluk için** seçilen şık, doğru mu, süre; reddedilen parçalar. **Kelime bazında cevap kaydedilmiyor.**

---

## B. "Seviyeni belgele" (değerlendirme)

### Akış (`AssessmentService.cs`)
1. **Tanıtım ekranı** (`assessment_page.dart`); "Başla" denemeyi açar.
2. **Isınma (yönlendirme):** 6 kısa tek soru, **tek sayfada**. Seviyeler: A1, A2, A2, B1, B1, B2 (kolaydan zora). Her seviyenin havuzundan (6'şar soru) rastgele; son 3 denemede görülenler elenir.
   - Yayını bekleyen değişiklik (PR açık): seviyesi A1–A2 olan okurda B2 sorusu yerine bir A1 sorusu gelir (A1, A1, A2, A2, B1, B1).
3. **Üç metin**, her biri 4 soru (ana fikir, ayrıntı, çıkarım, bağlamda kelime, bağlaşıklık, amaç ve ton türlerinden). İlk metnin seviyesi ısınmadan; sonrakiler bir önceki metnin puanından (aşağıda). Bir metnin 4 sorusu karışık sırayla gelir.
4. **Sınır adımı:** kestirilen seviyenin bir altından 2, bir üstünden 2 kısa soru (uçta tek taraf).
5. **Sonuç:** seviye, 0–100 puan, güven; ardından rapor ve (koşul tutarsa) belge.

Toplam: 6 + 12 + en çok 4 = **en çok 22 soru**, yaklaşık 10 dakika.

### Yarıda çıkarsa
Deneme açık kalır; yeniden girince **kaldığı adımdan** sürer (Mehmet'in denemesi 00:34'te açıldı, 02:58'de sürdü). Eski adıma cevap reddedilir.

### Yönlendirme kuralları (`AssessmentRouter.cs`)
- **Isınmadan başlangıç seviyesi:** k doğru → alttan (k−1). seviye; yani 0–1 doğru A1, 2 doğru A2, 3 doğru B1, 4 ve üstü B2. (Bekleyen değişiklikle: başlangıç, ısınmada sorulan en yüksek seviyeyi geçmez.)
- **Metinden sonra:** 4 soruda ≥ 3 doğru → bir üst; ≤ 1 doğru → bir alt; 2 doğru → aynı. Taban A1, tavan B2.
- **Süre koruması:** metin, kelime ÷ 300 kelime/dk + soru başına 3 sn'den kısa sürede geçildiyse soruları kaydedilir ama **karara girmez**; ikincisinde deneme **geçersiz** biter.

### Seviye kararı (`AssessmentDecisionEngine.cs`)
Bütün cevaplar seviyeye göre toplanır (ısınma + metin + sınır).
- **L seviyesi kazanılır** ⇔ L'de en az 2 soru var **ve** L'deki doğruluk ≥ **%70**, **ve** L'nin altındaki bütün sorularda doğruluk ≥ **%80** ya da en çok **bir** yanlış.
- Sonuç = kazanılan **en yüksek** seviye.
- **Kesin değil** (seviye yazılmaz, belge yok) sayılan durumlar:
  - sonuç seviyesinde 4'ten az soru (yetersiz kanıt);
  - kazanılmamış daha üst bir seviyede ≥ 3 soruda ≥ %75 doğruluk (tutarsız desen);
  - sınır adımında alttaki iki soru yanlış, üstteki iki soru doğru (sınır çelişkisi);
  - ≥ 12 cevabın %75'i aynı şık konumunda.
- Hiçbir seviye kazanılmadıysa ve A1'de yeterli soru varsa sonuç **"A1 altı"**; profile A1 yazılır.
- **Güven:** sonuç seviyesinde ≥ 6 soru ve üst seviyede doğruluk ≤ %50 ise Yüksek; yoksa Orta.

### Puan (0–100)
Puan seviyenin **içinde** kalır; aynı puan iki seviyeye karşılık gelmez.
| Sonuç | Puan aralığı |
|---|---|
| A1 altı | 0–9 |
| A1 | 10–24 |
| A2 | 25–39 |
| B1 | 40–54 |
| B2 | 55–69 |
| (C1 70–84, C2 85–100: havuzda yok) | |

Aralığın içindeki yer: üst seviyeden soru sorulduysa **oradaki doğruluk**; sorulmadıysa sonuç seviyesinde %70 eşiğinin ne kadar üstünde kalındığı. Örnek: Mehmet B2, puan 62 = B2 aralığının (55–69) ortası.
Sonuç: v1'de en yüksek puan 69'dur; "100 üzerinden 62" kullanıcıya düşük görünebilir ama B2'nin içinde orta demektir.

### Belge
Koşul: sonuç **yerleşti** (kesin değil ya da A1 altı değil) **ve** güven Orta ya da Yüksek. Yani **A1, A2, B1, B2'nin her birine belge veriliyor**; yalnız "A1 altı" ve "kesin değil" belgesiz. Belgede yalnız kazanılan seviye yazıyor.

### Hak
Tamamlanan deneme 30 gün boyunca hakkı kullanır. Kesin olmayan ya da geçersiz deneme hak yakmaz; 7 gün içinde ikiden fazlasına izin verilmez.

### Profil seviyesine etkisi
Yerleşti + güven ≥ Orta → profil seviyesi **sonuca eşitlenir (düşebilir de)**. A1 altı → A1 yazılır. Kesin değil → dokunulmaz. "Yalnız yükselt" kuralı bu testte **yok**.

### Kayıt
`AssessmentResponses`: her soru için seçilen şık, doğru mu, süre (adımın süresi soru sayısına bölünerek). `AssessmentSkillResults`: puan, sonuç, güven, seviye ve tür bazında döküm.

---

## Charles'ın dikkatine: koddan çıkan beş nokta
1. **İki test de seviyeyi düşürebiliyor**, belge testi dahil. Belge almak için giren kullanıcının okuma seviyesi düşebilir.
2. **Belge testinin ısınması kullanıcının seviyesini kullanmıyor** (bekleyen değişiklik dışında); 4 doğruyla ilk metin B2'den geliyor.
3. **Isınma eşlemesi sayıya bakıyor, seviyeye değil:** hangi soruların bilindiği önemli değil, kaç tane bilindiği önemli.
4. **Yeniden ölçmede kelime bazında cevap tutulmuyor;** kelimelerin bantlara doğru yerleşip yerleşmediği veriyle sınanamıyor.
5. **Soru metni yayından sonra değişirse eski cevaplar yeni soruya bağlanır:** belge soruları anahtarla güncelleniyor (`AssessmentSeed.cs`). "…" ile biten 29 soru yeniden yazılacaksa bugün müşteri cevabı olmadığı için sorun yok; cevap birikince yeni anahtar gerekir.
