# Metin seviyeleri, seviye testleri, günün quizi, güncelleme düzeni (veri)

**Tarih:** 21 Kasım 2026 · **Görev:** `ortak/editor_gorevi_2026-11-21_seviye_quiz_guncelleme_verisi.md` · **Hazırlayan:** editör
**Yöntem:** canlıdaki sunucu kodu (`origin/master` c8497c6), uygulama kodu (`feat/journey-core`) ve canlı veritabanı (salt okuma, yalnız müşteri hesapları, kişisel bilgi yok). Kanal ve bildirim verisi ayrı raporda: `2026-11-21_kanal_ve_bildirim_verisi.md`.

**Ekler** (`raporlar/veri_2026-11-21/`): `A1_metinleri.md` (24 metin), `A2_metinleri.md` (60 metin), `metin_basina_kullanici_verisi.md`, `soru_ornekleri.md`.

**Yapılmayan:** iki testin SE 3 ekran görüntüleri. Akışlar metinle anlatıldı; görüntü için uygulamayı yerel sunucuda sürmek gerekiyor, sıradaki derlemenin sürüşüne ekleyeceğim.

## Özet

1. **Okuma üç metinde toplanıyor.** A1–A2'deki 84 metnin 61'ini hiçbir müşteri açmamış. Başlangıçların %73'ü üç metne ait: Two Cups, The Island Where Rabbits Won, Thirty-One Mornings. Seviye denetimi için kullanıcı verisi yalnız 8 metinde yeterli.
2. **A1 metinlerini A2 ve üstü kullanıcılar da yoğun okuyor** (Two Cups'ı başlayanların %42'si); bitirenlerin ortanca hızı dakikada 30–50 kelime.
3. **"Seviyeni belgele"de boşluk doldurma yok;** hepsi dört şıklı. Ama herkes aynı altı ısınma sorusuyla başlıyor ve üçü B1–B2 düzeyinde. Boşluk doldurma öbür testte ("Seviyeni yeniden ölç").
4. **Ölçüm, kullanıcının seçtiği seviyeyi çoğunlukla aşağı çekiyor:** seviyesini kendi seçmiş 16 kişinin 8'i aşağı, 2'si yukarı. Az veri.
5. **Günün quizi herkese aynı ve skorlar yüksek:** ortanca 8/10, 5'in altı 173 turda 4. "Zor geldi, dönmedi" sorusu bu veriyle sınanamıyor (ilk quizinde 5'in altında alan 1 kişi).
6. **Müşterilerin %98'i onboarding taşma hatasını taşıyan sürümlerde** (derleme 46 ve öncesi); son 7 günde etkin 186 kişinin 179'u.

## 1. A1 ve A2 metinleri

### 1.1 Gövdeler

`veri_2026-11-21/A1_metinleri.md` (24 metin, 7.250 kelime) ve `A2_metinleri.md` (60 metin, 69.091 kelime). Her metinde kimlik, seviye, kelime sayısı, süre, dizi/bölüm ve tür (başlangıç paketi, günlük havuz). A2'de 7 metin bölümlü; bölümleriyle döküldü.

### 1.2 Metin başına kullanıcı verisi

Tam tablo: `veri_2026-11-21/metin_basina_kullanici_verisi.md` (84 satır).

| | A1 | A2 |
|---|---|---|
| Etkin metin | 24 | 60 |
| Müşterinin hiç açmadığı | 13 | 48 |
| Toplam başlama | 231 | 126 |
| Toplam bitirme | 187 (%81) | 95 (%75) |
| En az 5 bitireni olan metin | 6 | 2 |

En çok okunanlar (hız ve dokunma yalnız bitirenlerden):

| Metin | Seviye | Kelime | Başlayan | Bitiren | 100 kelimede dokunma | Hız (kelime/dk) | Başlayanların seviyesi A1 / A2 / B1+ |
|---|---|---|---|---|---|---|---|
| Two Cups | A1 | 217 | 123 | 97 (%79) | 7,7 | 47 | 70 / 35 / 16 |
| The Island Where Rabbits Won | A2 | 287 | 93 | 72 (%77) | 11,7 | 43 | 9 / 64 / 19 |
| Thirty-One Mornings | A1 | 254 | 46 | 32 (%70) | 10,5 | 42 | 20 / 14 / 11 |
| First Ramadan in London | A1 | 137 | 20 | 20 | 9,0 | 31 | 4 / 11 / 4 |
| Breakfast in New York | A1 | 104 | 17 | 16 | 4,9 | 43 | 5 / 8 / 4 |
| Ali's First Snow | A2 | 121 | 11 | 11 | 6,3 | 41 | 2 / 8 / 1 |
| Sunday Lunch with Grandma | A1 | 89 | 9 | 9 | 5,7 | 19 | 5 / 4 / 0 |
| The Bench | A1 | 251 | 7 | 5 | 10,1 | 32 | 5 / 0 / 2 |

- Kullanıcı her 100 kelimede 5–12 kelimeye dokunuyor. En yüksek oran A2'nin ücretsiz metninde (11,7) ve A1'in üçüncü hikâyesinde (10,5).
- "Başlayanların seviyesi" bugünkü seviyedir, okuma anındaki değil.
- Hız dakikada 30–50 kelime: dokunup bakma ve dinleme süresi içinde. Akıcı okumada beklenen hızın çok altında; bu, metnin zor olduğunu da uygulamanın yavaş okutacak biçimde tasarlandığını da gösterebilir, ayıramıyorum (1.4).

### 1.3 Etiketler neye göre verildi

- **6 Eylül (`KatalogSeviyeOlcumu`):** yalnız ortalama cümle uzunluğu ölçüldü (hedef A1 ~8, A2 ~10, B1 ~13, B2 ~17 kelime). Kelime zorluğu ölçülmedi. Salt ölçümdü; etiket değiştirmedi. 48 metinlik inceleme listesi çıktı, o gün karara bağlanmadı.
- **15 Ekim (`RelabelTextLevels`):** üç ölçüt birlikte: nadir kelime oranı (sıklık sözlüğüyle), ortalama cümle uzunluğu ve okunabilirlik puanı. Üçünün ortalaması etiketten 1,5 basamak ve üstü sapan metinler örnek bölüm okunarak karara bağlandı. 24 metnin etiketi değişti: B1→B2 9, A2→B1 6, B2→B1 4, B1→A2 5.
- **A2'den çıkanlar (B1 oldu):** Grandma's Soup, The Girl with the Yellow Umbrella, Black Beauty ve üç kültür yazısı (İstanbul çarşısı, Japon köyü, suşi).
- **A2'ye girenler (B1'di):** The Third Ring, The Deposit, Thirty-Six Instalments, Salt, The Bowl (dizi bölümleri).
- A1 etiketine o gün dokunulmadı. 1–1,5 basamak sapan 52 metin tek tek okunmadı.
- Ölçümün göremediği: örtük anlam (kısa cümleli ama alt metinli öykü kolay görünür) ve kültürel kelimeler (nadir oranını şişirir).

### 1.4 Okuma hızında dokunup bakma süresi ayrılabiliyor mu

**Hayır.** Oturum başına toplam süre, kelime dokunma sayısı, cümle dokunma sayısı ve dinleme süresi tutuluyor; bir dokunuşun ne kadar sürdüğü tutulmuyor. Yapılabilecek dolaylı karşılaştırma: hiç dokunmadan bitirenlerin hızı ile dokunanların hızı (bu raporda yapmadım; istenirse eklerim).

## 2. Seviye ölçümü ve seviye belgesi

İki ayrı test var ve birbirine benzemiyorlar. **Boşluk doldurma yalnız "Seviyeni yeniden ölç"te var; "Seviyeni belgele"nin 176 sorusunun hepsi dört şıklı çoktan seçmeli.** Mehmet'in gördüğü "doğrudan zor bir boşluk doldurma" belge testinden değil, ölçüm testinden geliyor olabilir; ya da belge testinin ısınma sorularını öyle algıladı. Hangisi olduğu ekran görüntüsüyle netleşmeli.

### 2.1 "Seviyeni yeniden ölç" (yerleştirme)

**Nereden açılır:** profildeki satır ve ana sayfadaki "Seviyeni 3 dakikada ölçelim" kartı (en az 2 hikâye bitirince; daha önce ölçtürdüyse 3). Onboarding'de artık test yok; orada kullanıcı seviyesini kendi seçiyor.

**Akış:**
1. Alt sayfa: "Seviyeni ölçelim" · "Birkaç dakika sürer. Sonuç ne çıkarsa okuduğun metinler ona göre ayarlanır." · "Yaklaşık 3 dakika" · "Bu hafta {n} hakkın var" · düğme "Ölçüme başla".
2. Tanıtım: "Nasıl ölçüyoruz" · "30 kelime — biliyor musun, bilmiyor musun" · "3 kısa parça — boşlukları doldur" · "Yaklaşık 3 dakika. Bilmiyorum demek de bir cevap." · "Okuyarak ilerle — hızlı geçilen parça sayılmaz." · düğme "Başla".
3. **Kelime taraması:** "KELİME TARAMASI · 1 / 30". Tek tek İngilizce kelime; iki düğme: "Bilmiyorum", "Biliyorum". Uyarı: "Aralarda İngilizcede olmayan kelimeler var. Emin değilsen “Bilmiyorum” de." 30 kelime = A1, A2, B1, B2, C1'den dörder gerçek kelime (20) + 10 uydurma kelime, karışık.
4. **Parça:** "PARÇA 1 / 3". Kısa İngilizce parça, içinde üç boşluk; altında her boşluk için üç şık. "{n} / 3 boşluk doldu" · "Devam".
5. Sonuç: "OKUMA SEVİYEN", seviye ve bir cümle (A1: "Kısa ve basit cümleleri rahat okursun"; A2: "Günlük konuları anlatan kısa metinleri rahat okursun"; B1: "Hikâyeleri ve fikir yazılarını takip edebilirsin"; B2: "Uzun metinlerde ima ve tutumu yakalarsın"; A1 altı: "En kısa metinlerden başlıyoruz"). Başlık: "Seviyen yükseldi" / "Seviyeni güncelledik" / "Aynı seviyedesin".

**Kurallar:**
- **Testin başladığı seviye kullanıcının bugünkü seviyesine bakmaz.** Kelime taramasından çıkar. A1 kullanıcıyla B1 kullanıcı aynı kurala girer.
- Kelime taraması: uydurma kelimelerin yarısına ya da fazlasına "Biliyorum" denirse tarama güvenilmez sayılır, parça A1'den başlar. Değilse A1'den yukarı yürünür: bir basamaktaki dört kelimenin bilinen oranından uydurma kelime oranı düşülür; sonuç yarının altına indiği ilk basamakta durulur. Parçalar o basamaktan başlar (en düşük A1, en yüksek B2).
- Her parça 3 boşluk, 0–3 puan; en çok 3 parça.
- 3/3 → bir seviye yukarı. 0/3 (ilk parçada) → bir alt seviyeden doğrulama parçası; onda 2/3 ve üstü alt seviyeyi kesinleştirir, altı bir basamak daha indirir. 1/3 ya da 2/3 → aynı seviyeden ikinci parça; iki parçanın toplamı 6'da 4 ve üstüyse o seviye, altıysa bir alt seviye.
- Sonuç "A1 altı" çıkabilir.
- Çok hızlı geçilen parça sayılmaz (okuma hızı dakikada 300 kelimeden hızlıysa); aynı seviyeden yenisi gelir: "Bu parça biraz hızlı geçti". İkincisi de hızlıysa ölçüm geçersiz: "Bu sefer ölçüm alamadık"; hak yanmaz, seviye yazılmaz.
- **Seviye, test tamamlanınca yazılır ve düşebilir.** Haftada 3 hak, iki ölçüm arası en az 24 saat.
- Sunucuda "uygulamanın önerdiği ölçüm seviyeyi yalnız yükseltebilir" kuralı var ama **uygulama bu işareti hiç göndermiyor**; ana sayfa kartından başlatılan ölçüm de seviyeyi düşürebilir.

**İlk üç soru:** kelime taramasının ilk üç kelimesi (rastgele; A1 kullanıcıya da C1 kelimesi ya da uydurma kelime gelebilir). Parça aşamasının "ilk üç sorusu" tek bir parçanın üç boşluğudur. A1 parça örneği: "Ali gets up at six every day. He drinks a glass of ___. Then he walks to the stop on the corner. The ___ comes at seven…" şıklar: (milk / bread / rice), (shop / bus / park).

**Havuz:** 24 parça (A1, A2, B1, B2'den altışar), 72 boşluk; 60 gerçek kelime (seviye başına 12) + uydurma kelimeler.

### 2.2 "Seviyeni belgele" (okuma değerlendirmesi)

**Akış:**
1. Tanıtım: "Seviyeni belgele" · "Okuma seviyeni ölçer ve paylaşabileceğin bir belge verir." · "Yaklaşık 10 dakika, 22–24 soru" · "Kısa sorular, ardından üç metin ve birkaç kontrol sorusu" · "Metinleri gerçekten oku: çok hızlı geçilen metin sayılmaz" · "Ayda bir kez yapılır; sonuç kesin çıkmazsa hakkın yanmaz" · "Yalnız okumayı ölçer; dinleme ve konuşma sonra eklenecek" · düğme "Başla".
2. "ISINMA": 6 kısa soru; her sorunun küçük metni sorunun içinde (tabela, not gibi).
3. "METNİ OKU" (3 kez): bir metin ve 4 soru.
4. "KONTROL": en çok 4 soru.
5. Sonuç: "SONUCUN", seviye, "{puan} / 100 puan", "Karar güveni yüksek/orta", "Belgeni al".

**Kurallar:**
- **Başlangıç kullanıcının seviyesine bakmaz.** Herkes aynı 6 ısınma sorusunu görür: A1, A2, A2, B1, B1, B2 seviyesinden birer soru. Doğru sayısı metinlerin başlangıcını belirler: 0–1 doğru A1, 2 doğru A2, 3 doğru B1, 4 ve üstü B2.
- **Yani ilk altı sorunun üçü B1–B2 düzeyinde; A1 kullanıcı ilk dakikada zor soru görür.** Mehmet'in "zor başlıyor" izleniminin kaynağı bu olabilir.
- Her metinden sonra: 4'te 3 ve üstü doğru → sonraki metin bir üst seviyeden; 1 ve altı → bir alt; 2 → aynı.
- Kontrol: tahmin edilen seviyenin bir altından 2, bir üstünden 2 soru.
- Toplam 22 soru (uçlarda 20). Tanıtımdaki "22–24 soru" fazla söylüyor.
- Seviye kazanılır: o seviyedeki soruların en az %70'i doğru ve altındaki seviyelerde en az %80 (ya da en çok 1 yanlış). Sonuç = kazanılan en yüksek seviye.
- "Net ayıramadık" (hak yanmaz): o seviyede 4'ten az soru, üst seviyede tutarsız yüksek başarı, cevapların çoğu aynı şıkta gibi durumlar.
- Çok hızlı geçilen metin sayılmaz; ikincisinde deneme geçersiz.
- **Seviye yalnız sonuç kesinse yazılır** (güven orta ya da yüksek) ve düşebilir. Tamamlanan deneme 30 gün yeni denemeyi kapatır. Ayrıntılı rapor Premium'da.

**Havuz (176 soru):** seviye başına 44: 8 metin × 4 soru (32) + 6 ısınma + 6 kontrol. Hepsi dört şıklı. Soru türleri: ana fikir, ayrıntı, çıkarım, bağlamda kelime, bağlantı, amaç/ton.

| Seviye | Ayrıntı | Ana fikir | Çıkarım | Bağlamda kelime | Bağlantı | Amaç/ton |
|---|---|---|---|---|---|---|
| A1 | 14 | 10 | – | 10 | 10 | – |
| A2 | 11 | 10 | 10 | 7 | 6 | – |
| B1 | 10 | 10 | 11 | 6 | 7 | – |
| B2 | 10 | 7 | 9 | 6 | 6 | 6 |

### 2.3 Soru örnekleri

`veri_2026-11-21/soru_ornekleri.md`: iki testten, A1–B2 her seviyeden 5'er örnek, doğru şık işaretli.

"Seviyeni belgele"nin A1 ısınma sorusu: *Sign: "Shop open 9:00–17:00, Monday to Saturday." When is the shop closed?* (On Sunday / On Monday / On Friday / On Saturday). Boşluk doldurma değil.

### 2.4 Tamamlanan ve yarıda kalan ölçümler

Bugün 99 tamamlanmış, 10 yarıda kalmış, 1 geçersiz ("iki parça da hızlı geçildi") ölçüm var.

**Sonuç seviyesi (99):** A1 altı 3 · A1 21 · A2 56 · B1 12 · B2 7.

**Kelime taramasının verdiği başlangıç:** A1 36 · A2 24 · B1 33 · B2 4 · C1 2. Uydurma kelimeye "biliyorum" deme oranı ortalama %1–12.

**Kendi seçtiği seviyeyle fark:** yalnız 16 ölçümde, ölçümden önce kayıtlı bir seviye seçimi var. Kalan 83 kişide ölçümden önce kayıtlı bir seçim yok (ölçümü seviye seçmeden yapmış ya da hiç seviye seçmemiş); onlarda karşılaştıracak seçim yok.

| Seçtiği | Ölçüm sonucu | Kişi |
|---|---|---|
| A2 | A1 · A2 | 2 · 5 |
| B1 | A1 · A2 · B1 · B2 | 1 · 4 · 1 · 2 |
| B2 | A2 | 1 |

16 kişinin 8'i aşağı (ikisi iki basamak ve üstü), 6'sı aynı, 2'si yukarı. **Az veri;** yön "kullanıcı kendini yüksek seçiyor ya da test sert" diyor, hangisi olduğu bu sayıyla ayrılamaz.

**Yarıda kalan 10 ölçüm:** 5'i kelime taraması bitmeden · 3'ü ilk parçada (tarama bitmiş, hiç boşluk doldurulmamış) · 2'si ilk parçadan sonra. Yarıda kalan ölçüm sonsuza kadar "sürüyor" görünüyor; kullanıcı dönerse kaldığı yerden devam eder.

### 2.5 "Seviyeni belgele" sunucudan gizlenebiliyor mu

**Hayır.** Satır uygulamada koşulsuz çiziliyor; sunucunun cevabı ancak satıra dokunulduktan sonra okunuyor. Gizlemek uygulama değişikliği: yazıldı (`3e6fd9b9`, T19), sıradaki derlemeyle gider. Sunucu yalnız testi başlatılamaz yapabilir (kullanıcı satırı görür, dokununca "hazırlanıyor" yazısı çıkar); bunu yapmadım, yarım bir görüntü olurdu.

## 3. Günün quizi

### 3.1 Kelimeler ve şıklar

- **Herkese aynı 10 kelime;** seviyeye göre değil. Gün Türkiye saatine göre döner. Çarşamba günleri yalnız phrasal verb.
- Havuz: sözlükte doğrulanmış, Türkçe karşılığı ve örnek cümlesi olan, yalın hâldeki kelimeler; seviye A1–B2. Bir kelime 5 gün içinde tekrar gelmez. Seçim rastgele değil, günün numarasından hesaplanır (herkes aynı sırayı görür).
- Sunucu 30 kelime gönderir: 10'u soru, 20'si yedek.
- **Yanlış şıkları sunucu değil uygulama üretir:** o günkü diğer 29 kelimenin Türkçe karşılıklarından. Karşılık önce kısaltılır: parantez içi atılır, ilk virgül, noktalı virgül ya da eğik çizgide kesilir.
- Var olan süzgeçler: boş olmasın, doğru cevapla aynı olmasın, fiilse fiil olsun, İngilizce kelimeyle aynı kökten görünmesin.
- **Olmayan süzgeç: en az uzunluk ve "bu Türkçe bir kelime mi" denetimi yok.** Karşılığı "a, bir" ya da "a/an" gibi başlayan bir kelime kısaltılınca tek harf "a" olur ve şık olarak çıkar. 
- **"healthy" sorusundaki şık:** havuzda kısaltılınca tam "a" olan bir karşılık yok. En yakını **"an"**: "moment" kelimesinin karşılığı. Türkçe doğru bir kelime ama iki harfli olduğu için İngilizce "an" gibi okunuyor; Mehmet'in gördüğü şık büyük olasılıkla bu. Kesin değil: gösterilen şıklar kaydedilmiyor.
- Günün quizi havuzundaki 1.037 kelimenin 15'inin karşılığı iki harf ya da daha kısa: o (it, she), de (also), ve (and), un (flour), el (hand), ev (house), iş (job), an (moment), ağ (net), iz (trail), oy (vote), ne (what). Hepsi doğru Türkçe; sorun, başka bir kelimenin altında şık olarak anlamsız görünmeleri. "the" kelimesinin karşılığı kısaltılınca boş kalıyor; o zaten şık olamıyor.
- Ayrıca sunucu cevabı "doğru karşılık bu metinle başlıyor mu" diye de kabul ediyor; tek harfli bir şık, doğru cevabın ilk harfiyse doğru sayılır.
- Gösterilen şıklar hiçbir yere kaydedilmiyor; geçmiş bir günün şıkları ancak yeniden hesaplanarak bulunur.

### 3.2 Skor dağılımı

Müşterilerin tamamladığı 173 günün quizi turu (95 kişi), 10 üzerinden:

| Doğru | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|
| Tur | 4 | 16 | 27 | 29 | 42 | 31 | 24 |

| Kullanıcının seviyesi | Tur | Kişi | Ortalama | Çeyrekler | 5'in altı | 8 ve üstü |
|---|---|---|---|---|---|---|
| A1 | 37 | 26 | 7,6 | 6 · 8 · 9 | 1 | 22 |
| A2 | 85 | 46 | 7,6 | 7 · 8 · 9 | 2 | 46 |
| B1 | 29 | 15 | 7,9 | 7 · 8 · 9 | 0 | 21 |
| B2 ve üstü | 20 | 6 | 7,3 | 6 · 7 · 8 | 1 | 8 |

- **Skor seviyeye göre değişmiyor;** A1 kullanıcı da ortalama 7,6 alıyor. Quiz herkese aynı olduğu hâlde A1'e zor gelmiyor görünüyor; ya da zorlananlar turu bitirmeden çıkıyor (yarım turların skoru yok).
- **İlk quizinde 5'in altında alan: 1 kişi** (ertesi gün dönmedi). 5 ve üstü alan 94 kişinin 82'sinin ertesi günü dolmuş; 28'i (%34) ertesi gün uygulamayı açmış, 33'ü sonradan bir kez daha quiz çözmüş. Karşılaştırma yapılamaz: **az veri.**

### 3.3 "Haftalık Şampiyon" rozeti

Koşul: o hafta XP kazanmış en az 10 kullanıcı olacak, kullanıcının haftalık XP'si en az 100 olacak ve kimsenin haftalık XP'si ondan yüksek olmayacak. **Hafta sonunda değil, hafta içinde o an lider olan kişi bir etkinlik bitirdiği anda verilir.** 

Bugüne kadar 11 kez verilmiş; 8'i müşteri. Müşterilerde kazanıldığı andaki haftalık XP: 227 ile 705 arası. Günlere bakınca kural görünüyor: haftanın başında (pazartesi, salı) 227–229 XP ile de alınmış; yani "haftanın şampiyonu" değil, "o an önde olan". Aynı hafta birden çok kişi alabiliyor (14 Kasım'da iki kişi).

### 3.4 Quiz sekmesindeki rozet

- **Ne zaman görünmeli:** (a) ilk hikâye bitince bir kez, sekmeye girilene kadar; (b) hesabın ilk 24 saatinden sonra her gün, günün quizi **bu telefonda** çözülene kadar.
- **Mehmet'in telefonunda neden görünmedi:** kesin kanıt yok, en olası neden bulundu. Rozet uygulama açılırken bir kez hesaplanıyor; o an oturum henüz yüklenmemişse "oturum yok" diye sönük hesaplanıp öyle kalıyordu. Yeniden hesaplama yalnız uygulama arka plandan dönünce ya da quiz çözülünce oluyordu. Düzeltme: oturum yüklendiği an yeniden hesaplanıyor (`3e6fd9b9`, T18).
- İkinci olasılık (düzeltilmedi): uygulama gece yarısı açıkken gün değişirse rozet, uygulama arka plana gidip gelene kadar eski günün durumunda kalır. Mehmet 00:37'de yazdı; bu da olmuş olabilir.
- Rozet her zaman "1" yazar; çözülmemiş quiz sayısı değildir.

## 4. Güncelleme düzeni

### 4.1 Sürüm dağılımı

Müşterinin gönderdiği son olaydaki sürüm (358 müşteri; 41'inin hiç olayı yok):

| Sürüm | Bütün müşteriler | Son 7 günde etkin | iOS | Android |
|---|---|---|---|---|
| 1.0.0 (37, 39, 41) | 39 | 2 | 3 | 36 |
| 1.0.1 (43) | 39 | 1 | 39 | 0 |
| 1.0.2 (45) | 232 | 176 | 154 | 78 |
| 1.0.4 (47) | 6 | 6 | 0 | 6 |
| 1.0.4 (49) | 1 | 1 | 0 | 1 |
| **Toplam** | **317** | **186** | 196 | 121 |

- Etkin kullanıcının %95'i tek sürümde: 1.0.2 (45). Eski sürümlerde kalan 78 kişinin 3'ü son 7 günde açmış; kalanı bırakmış.
- 1.0.4 görünen 7 müşteri Android kapalı test kanalından gelenler.

### 4.2 Sunucudaki güncelleme ayarı ne yapabiliyor

- Platform başına iki sayı: **en düşük desteklenen derleme** ve **en yeni derleme**. Bugün dördü de 0: kimse engellenmiyor, kimseye öneri çıkmıyor. Ayar sunucu yeniden yayınlanmadan değiştirilebilir (ortam değişkeni).
- Uygulamanın derlemesi "en düşük"ten küçükse: **zorunlu**. Tam ekran "Güncelleme gerekli" · "Bu sürüm artık desteklenmiyor. Okumaya devam etmek için uygulamayı güncelle." · "Güncelle". Kapatılamaz.
- "En yeni"den küçükse: **öneri**. Altta şerit "Yeni sürüm hazır" · "Sonra" / "Güncelle"; günde en çok bir kez.
- Yani ikisi de yapılabiliyor. Yapılamayan: özel metin, belirli sürümlere özel kural, bakım kipi.
- Uygulama açılışta ve 30 dakikadan uzun arka plandan dönüşte sorar; ağ hatasında hiçbir şey göstermez.
- **Denetim 1.0.0 derleme 26'dan (1 Ekim) beri uygulamada.** Mağazaya çıkan bütün müşteri sürümleri (42 ve sonrası) bu ayara uyar.
- Toplantıdaki "kapatılabilir kart: Yeni okuma yolculuğun hazır. Güncelle." metni bugünkü şeritle birebir yapılamaz (metin sabit: "Yeni sürüm hazır"); ama öneri şeridi kod yazmadan açılabilir.

### 4.3 Kullanıcıyı kilitleyen bilinen hata

- **Onboarding'in ikinci ekranı (kelimeye dokun adımı):** kelimeye dokununca çıkan açıklama satırı sayfayı uzatıyor, küçük ekranda ya da büyük yazıda "Devam" düğmesi ekranın dışına itiliyor ve kaydırma olmadığı için kullanıcı onboarding'den çıkamıyordu. Aynı türden taşma 15 adımın 8'inde vardı.
- **Hangi derlemeler:** ilk sürümden **1.0.3 derleme 46'ya kadar hepsi.** Düzeltme 15 Kasım'da, ilk düzeltilmiş derleme **1.0.4 derleme 47**. Hata yalnız küçük ekranda ya da büyük yazı ayarında tetikleniyor; her kullanıcıyı etkilemez.
- Müşterilerin bugün kullandığı mağaza sürümleri (42–46) bu hatayı taşıyor. **Bu sürümlerde 310 müşteri var (olayı olanların %98'i); son 7 günde etkin 186 kişinin 179'u.** Ama bu kişiler onboarding'i geçmiş; hata onları artık etkilemez.
- Zorunlu güncelleme bu kullanıcıları kurtarmaz: hata onboarding'de, yani yeni kuran kişiyi etkiliyor; yeni kuran zaten mağazadaki en yeni sürümü alır. Asıl çare 1.0.4'ün mağazaya çıkması.
