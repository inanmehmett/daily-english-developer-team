# Editörden: bilgi isteklerinin cevapları (S1–S9)

**Tarih:** 21 Kasım 2026 gece · **Kimden:** editör · **Kime:** ekip
**Soru dosyası:** `raporlar/2026-11-21_editore_bilgi_istekleri.md`
**Bakılan kod:** uygulama `feat/journey-core` (d2228a73; derleme 49 = c639a389 bunun atası), müşterideki sürüm 1.0.2+45 = 383edc66; sunucu `fix/notification-rules` (10ecd26, `origin/master` + 3 bildirim commit'i).

Canlı veritabanı Mehmet'in izniyle salt okuma kipinde okundu (21 Kas 21:00–21:30). "Müşteri" = `Users.AccountKind = 'customer'` ve `IsTestAccount = false`; developer, tester ve promo hesapları sayılmadı.

| # | Kısa cevap | Karar etkisi |
|---|---|---|
| S1 | Mehmet 00:34'te **"Seviyeni belgele"** testini başlattı. İlk ekrandaki ilk soru "…" ile biten bir tamamlama sorusu; aynı ekranda B2 sorusu da var. 12 saniye sonra açtığı yeniden ölçme kelime taramasında kaldı, hiç parça görmedi | **T19 doğru satırı gizliyor.** Geri almaya gerek yok |
| S2 | Rozet dokunuşu her durumda aynı alt sayfayı açar. Rütbe hiçbir içerik, hak ya da görünüm açmıyor | Ekleme yok |
| S3 | Kariyer sayfasında hiç ekran okuyucu etiketi yok. Yüzde ve bayrak hiç okunmuyor | – |
| S4 | **Toplu ekleme yok.** Tek tek "Ekle" var; 15'te "defter doldu" sayfası çıkıyor | Q4 ana düğmesi "Sıradaki hikâye" |
| S5 | Son 7 günde müşteride 99 tur başladı, 95'i bitti. Yarıda bırakma %4; A1'de 24 turdan 1'i | Belirgin değil, Q1 kapalı kalabilir |
| S6 | İki sürümde de dokunma **ana sayfaya** açılıyor. Sunucu hikâye kimliği koymuyor. Sıradaki hikâyeyi hesaplayan servis sunucuda var | Adlı metin mümkün; kapağa açmak için yeni rota gerekiyor |
| S7 | Dokuz metnin hiçbiri yolculukta ya da başlangıç paketinde yok. **1089 günlük havuzda.** **1063'ü bir müşteri yarıda okuyor** | **1063'e dokunulmaz.** 1089 ekibin kararına |
| S8 | Döküm aşağıda (3 durum) | – |
| S9 | **Yeniden kullanılır**; yeni yazmak gerekmiyor | Derleme 50'yi geciktirmez |
| Doğrulama 1 | **Tutuyor:** 60 A2 metni, 69.091 kelime; altı klasik 46.546 | – |
| Doğrulama 2 | **Tutmuyor (1.0.4'te):** Rabbits, A2 başlangıç yolculuğunun **4.** durağı. 1.0.2'de başlangıç paketindeki üç metinden biri | Ekibin "ilk hikâye" varsayımı düzeltilmeli |

---

## S1 — Hangi test boşluk doldurmayla başlıyor
**Kayıtlar.** 20–21 Kasım'da canlıda 14 yeniden ölçme ve 1 belgeleme denemesi var. Mehmet'in hesabı (misafir, `AccountKind = tester`, `1e736e14…`, 1.0.4+49) bunların ikisinde. Saatler TR, sunucu kaydı:

| Saat | Ne oldu | Kaynak |
|---|---|---|
| 00:28–00:31 | B1 yolculuğunun 1. hikâyesini (1024) okuyor | `UserEvents` |
| **00:34:28** | **"Seviyeni belgele"de "Başla"ya basıldı**; deneme 3 açıldı | `AssessmentAttempts` (deneme yalnız `POST /api/assessment/start` ile açılıyor, `AssessmentService.cs:124-137`) |
| 00:34:40 | "Seviyeni yeniden ölç" turu açıldı (oturum 169; `Trigger = User`, yani profil satırı ya da ana sayfa kartı; ikisi de `user` gönderiyor) | `PlacementSessions` |
| 00:34:41 | `placement_intro_started`: tanıtımdan sonra kelime taramasına geçti | `UserEvents` |
| 00:37 | Mehmet'in mesajı | – |
| 02:58–03:06 | Belgele denemesi kaldığı yerden sürdü ve bitti: B2, puan 62, sertifika | `UserEvents`, `AssessmentResponses` |

**Mehmet'in gördüğü test "Seviyeni belgele".** Gerekçe:
- **Yeniden ölçme turu (169) hiç parça göstermedi.** Kayıtta `VocabDone: false`, `Served: []`, `CurrentPassageId: null` var. Kullanıcı 30 kelimelik "biliyor musun" taramasında kalmış. Boşluk doldurma parçası taramadan sonra geliyor, o noktaya gelinmemiş.
- **Belgelemenin ilk ekranı** (yönlendirme adımı) 6 soruyu tek sayfada gösteriyor. Mehmet'in denemesinde sıra:
  1. *"The water is very hot. Don't drink it now." "Hot" is the opposite of …* (A1; şıklar big / new / cold / fast)
  2. A2
  3. A2
  4. B1
  5. B1
  6. B2: elektrikli arabalar paragrafı, *What is the main point?*

  Yani ilk soru "…" ile biten bir tamamlama sorusu, aynı sayfanın sonunda da bir B2 sorusu duruyor.
- Belgelemede `___` yok, ama **176 sorunun 41'i "…" ile bitiyor**: yönlendirmede 4/24, metin sorularında 33/128, sınır adımında 4/24. Ekranda bunlar boşluk doldurma gibi okunuyor.

**Emin olmadığım yer:** 00:34'teki `assessment_intro_shown` / `assessment_started` olayları olay tablosunda yok; 02:58'deki giriş olayları var. Kayıp büyük ihtimalle olay kuyruğundan. "Başla"ya basıldığını sunucunun deneme kaydı kanıtlıyor.

**Karar etkisi:** Görülen test belgelemeydi; **T19 doğru satırı gizliyor.** "Dur ve yaz" koşulu oluşmadı.

**Kod notları:**
- Yeniden ölçme başlangıç sorusu sormuyor; akış tanıtım → kelime taraması → mevcut seviyeden boşluk doldurma parçası (`PlacementController.cs:81-86`, `level_measure_view.dart`).
- Belgeleme girişi yalnız profilde (`profile_page.dart:1827`, `AppConfig.assessmentEntryEnabled`). Yeniden ölçme girişi profilde, ana sayfa kartında ve onboarding'de.

**Yan bulgu (A6 ile ilgili):** "Yalnız yükselt" işareti sunucuda **zaten var** (`trigger: "offer"`, `PlacementController.cs:93-96`; `PlacementTrigger`: 0 Onboarding, 1 User, 2 Offer). Uygulama hiç göndermiyor: `PlacementApi.startRemeasure` varsayılanı `'user'`, ana sayfa kartı da tetikleyici geçirmiyor (`placement_api.dart:41`). A6 yalnız uygulama tarafında birkaç satırlık bir iş.

**Yan bulgu (A6 ile ilgili):** "Yalnız yükselt" işareti sunucuda **zaten var** (`trigger: "offer"`, `PlacementController.cs:93-96`). Uygulama hiç göndermiyor: `PlacementApi.startRemeasure` varsayılanı `'user'` ve ana sayfa kartı `LevelRemeasurePage.open`'a tetikleyici geçirmiyor (`placement_api.dart:41`). A6 yalnız uygulama tarafında birkaç satırlık bir iş.

## S2 — Rozete dokununca ne oluyor, rütbe ne açıyor
**Dokunma** (`career_page.dart:591-600, 698-878`): kazanılmış, şimdiki ve kilitli (sıradaki dahil) her rozette aynı akış çalışıyor:
1. Analitik olayı: `career_node_tap` {rank, status, is_next}.
2. Alt sayfa açılır: rozet resmi (72 pt), rütbe adı, durum etiketi (Tamamlandı / Şu an / Kilitli).
   - Şimdiki rütbede: ilerleme çubuğu, "2.750 / 4.500 XP · %61" ve kalan XP.
   - Kilitli rütbede: eşik XP'si ve "açmak için kalan XP".
   - Hepsinde: rütbe açıklaması ve **"Okumaya devam et"** düğmesi. Düğme sayfayı kapatıp Keşfet sekmesini açıyor.
   - "Sıradaki" rozetin farkı yalnız haritada (renkli çiziliyor). Alt sayfası kilitli rozetinkiyle aynı.

**Rütbe kazanmak:** içerik, hak ya da görünüm açmıyor. Kodda bu bilinçli olarak yazılmış: *"Rütbenin somut bir karşılığı yok (bilinçli ürün kararı: ilerleme kilit satmaz)"* (`career_page.dart:705-709`). Sunucuda olanlar (`Services/XPGateway/XPGateway.cs:174-226, 393-456`):
- `CurrentSubLevelId` ve `LastLevelUpDate` güncelleniyor.
- SignalR `LevelUp` mesajı gidiyor; uygulama kutlamayı gösteriyor.
- Ayrıca rozet servisi "level" kategorisindeki rozeti veriyor (`BadgeService.cs:219-225`). Bu rozet kendi XP ödülünü getiriyor; rozetler sayfasında da görünüyor. Kilit açan bir şey değil.
- Kariyer şeridinin rengi bölgeye göre değişiyor. Bu ilerlemenin rengi, açılan bir görünüm değil.

**Karar etkisi:** Rozet bir şey açmıyor. Ekleme yapmadım.

## S3 — Ekran okuyucu etiketleri (bugün)
`career_page.dart`, `rank_badge_art.dart` ve `mockup/career-readability` dalındaki E1'de **hiç `Semantics` ya da `semanticsLabel` yok.** Ekran okuyucu yalnız düz metinleri okur:

| Öğe | VoiceOver / TalkBack bugün ne der |
|---|---|
| Rozet durağı | Yalnız rütbe adı ("Meraklı"). "Düğme" demez, çünkü `GestureDetector` düğme rolü taşımıyor. Durumu (kazanıldı / kilitli) ve rozet resmi okunmuyor; kilit simgesi sessiz |
| Yol, dolum, bayrak, yüzde ("%11") | **Hiçbiri okunmuyor**: hepsi `CustomPainter` ile tuvale çiziliyor (`_JourneyPathPainter`, `_HereFlagPainter`) |
| Alt şerit, açık hâl | Parça parça okunuyor: "Okuma Yolculuğun" · "1.234 XP" · "23" · "ort. XP/gün" · "~14" · "gün → Meraklı". Simgeler sessiz |
| Alt şerit, kapalı hâl | "1.234 XP" · "~14 gün" · "→ Meraklı" |
| Sandık, misafir şeridi, Premium şeridi | Yalnız içlerindeki düz metin |

Karşılaştırma için: ana sayfadaki `CareerStrip` seri sayısına etiket veriyor (`career_strip.dart:298`). Kariyer sayfası vermiyor.
Yeni etiket ("Meraklı'ya giden yolun yüzde 11'i. Yaklaşık 5 günlük okuma kaldı.") için birleştirilmiş tek bir `Semantics` gerekiyor. Yüzde tuvalde çizildiği için o metin şu an hiçbir yerde okunmuyor.

## S4 — Günün quizi sonucu: deftere ekleme
- **Toplu ekleme yok.** Kodda "hepsini ekle" yolu yok.
- **Tek tek ekleme** (`daily_quiz_missed_sheet.dart`):
  - Sonuç ekranında "Kaçırdığın kelimeleri çalış" düğmesi yalnız iki koşulda ana düğme oluyor: yanlış varsa ve skor %70'in altındaysa (`vocabulary_quiz_result.dart:329-335`, `DailyQuizResult.shareWorthyRatio = 0.7`). Aksi hâlde ana düğme "Sonucu paylaş", ikincisi "Alıştırmaya geç".
  - Düğme "Kaçırdığın kelimeler" alt sayfasını açıyor. Her satırda kelime, anlam, örnek cümle ve bir **"Ekle"** düğmesi var. Ekleyince satır "✓ Defterde" oluyor.
  - Aynı sayfa günün quizi giriş ekranından da açılıyor (`daily_quiz_landing.dart:230, 252, 340`).
  - Sonuç ekranında bunlardan bağımsız bir **"Sıradaki okuma" kartı** zaten var (`NextReadingCard(surface: 'vocab_quiz_result')`, `vocabulary_quiz_page.dart:361`).
- **Ücretsiz kullanıcı 15'e çarpınca** (`FreemiumLimits.vocabularyMaxWords = 15`): "Ekle"ye basınca kelime eklenmiyor. Yerine "defter doldu" alt sayfası açılıyor:
  - Üst satır: "KELİME DEFTERİ · 15 / 15"
  - Başlık: "Defterin 15 kelimeyle doldu, güzel bir başlangıç."
  - Metin: "Hepsini saklamak istersen Premium'da yer bol."
  - Düğmeler: "Premium'a bak" (ödeme sayfası, tetikleyici `limitReached`) ve "Tamam".
  - Olay: `limit_reached` (vocabulary).

  Emin olmadığım yer: sınır kontrolü önbellekteki hak bilgisinden okunuyor (`EntitlementService.canSaveWords`, bilgi yoksa `true`). Aynı alt sayfada art arda eklerken 15. kelimeden sonra önbellek tazelenmezse 16. ekleme denemesinin ne yaptığını (sunucu reddi mi, sessiz hata mı) cihazda denemedim.

**Karar etkisi:** Toplu ekleme yok → kurala göre Q4'ün ana düğmesi "Sıradaki hikâye" olur.

## S5 — Günün quizi olayları
**Uygulamanın yazdığı olaylar:**

| Olay | Ne zaman | Müşteri sürümünde (1.0.2+45) var mı |
|---|---|---|
| `daily_quiz_started` {first_round} | Her tur başı (9c89f57e, 15 Kas) | **Yok**. Derleme 49'da var |
| `practice_quiz_started` | Alıştırma turu başı | **Yok**. Derleme 49'da var |
| `first_experience: quiz_intro_shown / quiz_intro_started` | Yalnız ilk giriş | Var |
| `daily_quiz_shared` | Sonuç paylaşımı | Var |
| `quiz_question_reported` | Soru bildirimi | Var |
| Soru, bitiş, skor, yarıda bırakma | — | **Hiç yazılmıyor** (uygulama olayı yok) |

**Sunucunun kendi kaydı** (`VocabularyQuizRounds`), olaydan güvenilir:
- Tur başında satır açılıyor. Uygulama soruları `GET /api/ApiVocabulary/daily-quiz` ile yalnız "başla"ya basınca çekiyor (`vocabulary_quiz_cubit.dart:183`). Günün quizinde `DailyQuizNumber` dolu.
- Bitişte (`POST /api/quiz/complete`) `CompletedAt` ve sunucunun saydığı `CorrectCount` yazılıyor (`QuizController.cs:661-709`).
- Yani **başlama, bitiş ve skor tüm sürümlerde ölçülebilir.** 6 saat içinde `CompletedAt` boş kalan tur yarıda bırakılmış sayılır.
- Soru bazında kayıt yok; cevaplar yalnız bitişte toplu gidiyor. Kaçıncı soruda bırakıldığı ölçülemiyor.
- Seviye için `UserProfiles.CurrentCefrLevel` ile birleştirilir.

**Son 7 gün, yalnız müşteri** (`VocabularyQuizRounds`, `DailyQuizNumber` dolu; 21 Kas 21:15'te okundu):

| Seviye | Başladı | Bitti | Yarıda (6 saatten eski, açık) | Kişi | Ort. doğru / 10 |
|---|---|---|---|---|---|
| A1 | 24 | 23 | 1 (%4) | 14 | 7,0 |
| A2 | 49 | 47 | 2 (%4) | 30 | 7,4 |
| B1 | 16 | 15 | 1 (%6) | 14 | 7,8 |
| B2 | 8 | 8 | 0 | 4 | 8,4 |
| PreA1 | 2 | 2 | 0 | 2 | 6,0 |
| **Toplam** | **99** | **95** | **4 (%4)** | **64** | **7,5** |

- "Bitti" yalnız son soruya gelinince yazılıyor (`vocabulary_quiz_cubit.dart:396, 420`); yarıda çıkan tur açık kalıyor.
- "Yarıda" yalnız tura girip çıkanları kapsıyor. Giriş ekranını görüp hiç başlamayanlar burada yok, çünkü tur "Başla"ya basınca açılıyor.
- Seviye, kullanıcının bugünkü seviyesi.

**Karar etkisi:** A1'de yarıda bırakma 24 turdan 1'i (%4). Belirgin yüksek değil; **Q1'i yeniden açmayı gerektirmiyor.** Veri noktası az, A1'de 14 kişi: bu bir hipotez, ders değil.

## S6 — "Geri dön" bildirimine dokununca
- **Sunucu** (`NotificationDispatchService.cs:1162-1203`): veri yalnız `action = "win_back"` ve `daysInactive`. **Hikâye kimliği yok.** Metin 3. günde yarım kitabın adını kullanabiliyor (`LoadUnfinishedBooksAsync`), ama oradan yalnız ad ve bölüm geliyor, kimlik gelmiyor.
- **Uygulama, 1.0.2+45 ve 1.0.4 (derleme 49) aynı:**
  - `win_back` → `/home` (`app_navigator.dart:171-174`).
  - Uygulama bildirimden yalnız `action` alanını okuyor (`fcm_service.dart:345, 366`); öbür alanlar yok sayılıyor.
  - Kapak sayfası rotası (`/book-preview`) kimlik değil hazır `BookModel` bekliyor (`main.dart:543`). Bugün bir hikâyenin kapağına **kimlikle** açan bir rota yok.
  - Bilinmeyen bir `action` gelirse 1.0.2 rotasız açılır (bir sonraki maddede kullanılabilir).
- **Sunucu sıradaki hikâyeyi hesaplayabiliyor mu: evet.**
  - `JourneyService.GetAsync(userId, now)` (`Services/Journey/JourneyService.cs:118`, master'da var) yolculuğun şimdiki durağını veriyor: `ReadingTextId`, `Title`, `EstimatedMinutes`, `Status` (yarın mı açılıyor).
  - Yarım kitap ayrıca `ReadingProgresses`'tan geliyor.
  - **Dikkat:** `GetAsync`'in bir yan etkisi var. Yolculuğu yoksa kullanıcıya yolculuk **atıyor** ve `journey_assigned` olayı yazıyor. Gönderim işinde, atama yapmayan salt okuma bir sürüm gerekir.

**Karar etkisi:** Sunucu sıradaki hikâyeyi bilebiliyor, yani adlı metinler mümkün. Ama dokunmanın o hikâyenin kapağına açılması için iki iş gerekiyor: uygulamada kimlikle açılan yeni bir rota ve sunucunun bildirime kimlik koyması. 1.0.2'de bu bildirim ana sayfaya açılmaya devam eder.

## S7 — Dokuz metin (1096, 1098, 1039, 1097, 1103, 1094, 1063, 1089, 1067)
Canlı veri (`ReadingTexts`, `JourneyStops`, `ReadingProgresses`; hepsi aktif ve bugün A2):

| Id | Metin | Kelime | Yolculuk | Başlangıç paketi | Günlük havuz | Yarıda okuyan (müşteri / diğer) | Bitiren |
|---|---|---|---|---|---|---|---|
| 1096 | The Wonderful Wizard of Oz | 7.558 | – | – | – | 0 / 1 developer | 0 |
| 1098 | The Wind in the Willows | 8.768 | – | – | – | 0 / 2 developer | 0 |
| 1039 | Alice's Adventures in Wonderland | 8.615 | – | – | – | 0 / 1 developer | 0 |
| 1097 | The Secret Garden | 8.259 | – | – | – | 0 / 1 developer | 0 |
| 1103 | The Jungle Book | 5.593 | – | – | – | 0 / 1 developer | 0 |
| 1094 | Anne of Green Gables | 7.753 | – | – | – | 0 / 2 developer | 0 |
| **1063** | The Country That Eats Breakfast Twice | 322 | – | – | – | **1 müşteri (B1)** / 2 tester | 1 |
| 1067 | The See-Through Umbrella | 313 | – | – | – | 0 | 0 |
| **1089** | The Train with No Driver | 321 | – | – | **evet** | 0 | 2 |

- **Yolculuk:** canlıda 6 yolculuk var, hepsi tohumdakiler; ilgi alanına göre yolculuk yok (`Interest` hepsinde boş). Dokuz metnin hiçbiri bir durak değil.
- **1063'ü bir müşteri yarıda okuyor** (bugün B1; 1. bölüm). Kural gereği **1063'e dokunulmaz.**
- **1089 günlük açma havuzunda.** Kuralın "dokunma" listesinde günlük havuz yok. Etiket değişince havuzdan kalkmıyor (havuz etiketten bağımsız), ama A1 okuruna "bugün aç" olarak B1 metni çıkabilir. Karar ekipte.
- Klasiklerde yarım okuyan yalnız geliştirici hesapları; müşteri yok.
- **Etkilenen kitle** (müşteri, bugünkü seviye; parantez içi son 7 günde görülen): A1 135 (75) · A2 150 (102) · B1 62 (34) · B2+ 23 (12).
- **Etiket A2 → B1 olunca kimin önünden kalkar** (`book_list_view_model.dart:322-457`; raf tavanı okurun seviyesi + 1):
  - **A1 okuru:** "Yeni eklenenler" ve vitrinden **kalkar** (tavan A2'ydi, B1 tavanı aşıyor). "Önerilen"de üst seviye cezası ikiye katlanıyor (`_levelOvershootPenalty = 2`), metinler sona iner.
  - **A2 okuru:** raflarda kalır (tavan B1), ama "Önerilen"de seviye farkı 0'dan "bir üst"e çıkar ve aşağı iner.
  - **B1 okuru:** **öne çıkar** (fark 1'den 0'a).
  - **B2 ve üstü:** fark küçülür, biraz yukarı çıkar.
  - Yolculuk ve günlük açma havuzu etiketten bağımsız. Okuyucu ekranı da etiketi kilit için kullanmıyor.

**Karar etkisi:** C-11 betiği **8 metinle** çalışır; 1063 dışarıda kalır. 1089 için ekip "günlük havuzda kalsın mı" diye karar verirse ona göre.

## S8 — Ana sayfa kartları (bugün, `feat/journey-core`)
Kaynak: `lib/features/home/presentation/pages/home_page.dart:1018-1360`. Yukarıdan aşağı:

| # | Kart | Koşul |
|---|---|---|
| 1 | **Kişi kartı** (`HomeHeader`) | Her zaman. Selam; seri ve XP > 0 ise seri ve rütbe satırı ("Meraklı yolundasın · ilerlemeni gör ›"); Premium ise "Premium üye" |
| 2 | **İlk hafta sayacı** (`_WeekPlanStrip`) | Hesap açılışından 7 günden az geçtiyse. Cümle yalnız üç koşul birlikteyse çıkıyor: en az bir hikâye bitmiş, yarım kitap yok, seri isteği yok. Yoksa yalnız yedi daire |
| 3 | **Yolculuk kartı** (`JourneyHomeCard`) | Sunucu yolculuk verdiyse. Sunucu "yolculuk yok" derse → "Okumaya devam et" kartı → o da yoksa seri riski şeridi. Yüklenirken boş |
| 4 | Vitrin (dönen kapaklar) | İlk hafta **değil** **ve** okuma geçmişi var (yarım ya da bitmiş en az bir metin) |
| 5 | Ödeme sorunu uyarısı (`GracePeriodBanner`) | Yalnız mağaza ödeme ek süresindeyse |
| 6 | Seri telafi şeridi | Seri kırık ve telafi hakkı açıksa |
| 7 | İlk okuma kartı (`FirstReadCard`) | **Yalnız yolculuk yoksa** (yolculuk varken hiç çıkmıyor) |
| 8 | **"Bugün" yuvası**, tek kart, sırayla ilk uyan | İlk hafta değil + okuma geçmişi var: ① kelime tekrarı zamanı geldiyse ya da günün quizi bugün çözülmediyse görev kartı → ② **seviye ölçüm kartı**: ölçüm hakkı açık, ilk ölçüm için ≥2, yeniden ölçüm için ≥3 bitmiş metin, kapatıldıysa 7/14 gün susar → ③ kariyer şeridi (seri riski görünürken hiçbir şey) |
| 9 | "Sana özel" rafı | İlgi alanı seçilmişse |
| 10 | Önerilen · Yeni eklenenler · Trend | Her zaman (boşalan raf gizlenir) |
| 11 | Liderlik | Kapalı (`AppConfig.leaderboardEnabled`) |
| 12 | **Premium şeridi** (`SmartPremiumBanner`) | Premium değilse (kendi iç koşulları da var) |
| 13 | Misafir: "hesabını kaydet" / kayıtlı: e-posta doğrulama | Misafirse / e-postası doğrulanmamışsa |

Açılışta ayrıca **oturum başına en çok bir kesinti** penceresi çıkabiliyor: deneme bitiyor, bildirim izni, ertelenmiş ödeme sayfası, kampanya teklifi ya da hesap koruma (`home_page.dart:271-351`). Bunlar kart değil.

**Üç durum:**
- **Yeni kullanıcı (0. gün, hiç okumamış):** 1 kişi kartı (selam; seri ve rütbe satırı yok) → 2 yedi boş daire, cümle yok → 3 yolculuk kartı (ilk durak) → 10 raflar → 12 Premium şeridi → 13 misafirse "hesabını kaydet". Vitrin, "Bugün" yuvası ve ilk okuma kartı yok.
- **3. gün (bir-iki hikâye bitmiş):** 1 kişi kartı (seri ve rütbe satırı) → 2 sayaç; cümle ("n hikâye kaldı") yalnız yarım kitap ve seri isteği yoksa → 3 yolculuk kartı (hak kullanıldıysa "yarın" satırıyla) → 6 seri kırıldıysa telafi → 9–10 raflar → 12 → 13. İlk hafta olduğu için vitrin ve "Bugün" yuvası yok.
- **Güncelleyen eski kullanıcı (7 günden eski, okuma geçmişi var):** 1 kişi kartı → 3 yolculuk kartı. Sunucu ilk açılışta başlangıç yolculuğunu atıyor; daha önce bitirilmiş metinler tamamlanmış sayılıyor. Bu kart eskiden orada duran "Okumaya devam et" kartının yerini alıyor → 4 vitrin → 5/6 gerekiyorsa → 8 "Bugün" yuvası (görev, yoksa seviye ölçümü, yoksa kariyer şeridi) → 9–10 raflar → 12 → 13. Hiç okumamış eski kullanıcıda 4 ve 8 de yok.

**Ekibin bilmesi gereken iki nokta:**
- Yolculuk kartı varken **seri riski şeridi ana sayfada hiç çıkmıyor**. Çünkü şerit yalnız "devam et" kartının yedeği, o kart da yolculuk kartının yedeği. Seri isteği yalnız dolaylı etki ediyor: sayaç cümlesini ve kariyer şeridini susturuyor.
- **Seviye ölçüm kartı**, ana sayfanın "Bugün" yuvasındaki ikinci seçenek. Kart "Seviyeni yeniden ölç" testini açıyor (S1).

## S9 — "Yarın hatırlat" ana sayfa kartında
**Yeniden kullanılır.** Parçalar zaten paylaşılan bileşen:
- Düğme ve durumları (bekliyor / kuruldu "… hatırlatırım" / izin yok): `JourneyReminderDoor`. Herkese açık widget, `journey_finish_panel.dart:174`. Bitiş ekranı ve yolculuk sayfası aynısını kullanıyor.
- Davranış (izin isteme, okuma saati, yoksa 19:00, tek yerel bildirim, `id 2010`, payload `journey_stop` → ana sayfa): `JourneyReminder.remindTomorrow` (`journey_reminder.dart`).
- Yolculuk sayfasının yaptığı tek ek şey, `_remindTomorrow` içindeki iki analitik olayı (`remind_tomorrow_tapped` / `_result`, `source`). Bu 10 satırlık özel metot ortak bir yere (`JourneyActions`) taşınır; ana sayfa `source: 'home'` ile çağırır.
- Görünme koşulu da hazır: `stop.status == JourneyStopStatus.tomorrow` (yolculuk sayfasındaki `waitsForTomorrow`).

İş büyüklüğü birkaç saat, test dahil. **Derleme 50'yi bir günden fazla geciktirmez.**

## İki doğrulama
1. **"A2 metinlerinin 69.091 kelimesinin 46.546'sı altı klasikten": tutuyor.** Canlıda 60 aktif A2 metni var, `WordCount` toplamı 69.091; altı klasiğin (1096, 1098, 1039, 1097, 1103, 1094) toplamı 46.546, yani %67.
2. **"The Island Where Rabbits Won, A2 kullanıcısının ilk ücretsiz hikâyesi": 1.0.4'te tutmuyor.** Canlıdaki `starter-a2` sırası tohumla aynı:
   1. Ali's First Snow (127)
   2. The Cat Knows the Time (1070)
   3. Baba Yaga (1045)
   4. **The Island Where Rabbits Won (1023)**

   Rabbits aynı zamanda `IsStarterPack = true`, yani yolculuk öncesinin (1.0.2) üç ücretsiz başlangıç metninden biri. Ekibin "ilk hikâye" sayısı muhtemelen o döneme ait; bunu ayrıca doğrulamadım. Rabbits'te 30 müşteri yarıda, toplam bitiren 82 (tüm hesaplar). C-12 gövde değişikliğinde bu yarım okuyanların bölüm konumu etkilenebilir.

## Kullanılan sorgular
Hepsi salt okuma işleminde (`default_transaction_read_only=on`) çalıştı. Kopyaları editörün geçici klasöründe; depoya konmadı. Tablolar: `PlacementSessions` (Raw), `AssessmentAttempts/Responses/Items/Stimuli`, `UserEvents`, `VocabularyQuizRounds`, `ReadingTexts`, `JourneyStops`, `Journeys`, `ReadingProgresses`, `UserProfiles`, `Users`.
