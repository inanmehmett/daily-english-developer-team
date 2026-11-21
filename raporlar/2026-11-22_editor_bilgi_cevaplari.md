# Editörden: bilgi isteklerinin cevapları (S1–S9)

**Tarih:** 21 Kasım 2026 gece · **Kimden:** editör · **Kime:** ekip
**Soru dosyası:** `raporlar/2026-11-21_editore_bilgi_istekleri.md`
**Bakılan kod:** uygulama `feat/journey-core` (d2228a73; derleme 49 = c639a389 bunun atası), müşterideki sürüm 1.0.2+45 = 383edc66; sunucu `fix/notification-rules` (10ecd26, `origin/master` + 3 bildirim commit'i).

## Önce: canlı veritabanı okunamadı
Canlı veritabanına salt okuma bağlantısı bu oturumda **izin katmanında reddedildi**. Kayıt isteyen kısımlar (S1 kayıtları, S5 sayıları, S7'nin veri kısmı, iki doğrulama) **bilinmiyor**. Aşağıdaki her biri için çalıştırılacak sorgu hazır (en altta). Kod tarafının cevapları tam.

| # | Kısa cevap | Durum |
|---|---|---|
| S1 | Kod, şikâyetin **"Seviyeni yeniden ölç"** testine uyduğunu gösteriyor; "Seviyeni belgele"de boşluk doldurma yok. Kayıtlar okunamadı | Kod ✔ · kayıt ✘ |
| S2 | Rozet dokunuşu her durumda aynı alt sayfayı açar. Rütbe hiçbir içerik, hak ya da görünüm açmıyor | ✔ |
| S3 | Kariyer sayfasında hiç ekran okuyucu etiketi yok. Yüzde ve bayrak hiç okunmuyor | ✔ |
| S4 | **Toplu ekleme yok.** Tek tek "Ekle" var; 15'te "defter doldu" sayfası çıkıyor | ✔ |
| S5 | Müşteri sürümü quiz için neredeyse olay yazmıyor; başlama, bitiş ve skor sunucunun tur tablosunda var. Sayılar okunamadı | Kod ✔ · sayı ✘ |
| S6 | İki sürümde de dokunma **ana sayfaya** açılıyor. Sunucu hikâye kimliği koymuyor. Sıradaki hikâyeyi hesaplayan servis sunucuda var | ✔ |
| S7 | Dokuz metnin hiçbiri yolculuk tohumunda yok. Etiket değişince A1 okurunun raflarından kalkar, B1 okurunun önüne çıkar. Başlangıç paketi, günlük havuz ve yarım okuyan okunamadı | Kod ✔ · veri ✘ |
| S8 | Döküm aşağıda (3 durum) | ✔ |
| S9 | **Yeniden kullanılır**; yeni yazmak gerekmiyor. Derleme 50'yi geciktirmez | ✔ |
| Doğrulama 1 | Kelime sayıları okunamadı | ✘ |
| Doğrulama 2 | **Kodda tutmuyor:** tohumda The Island Where Rabbits Won A2 başlangıç yolculuğunun **4.** durağı, ilki değil. Canlıdaki sıra okunamadı | Kod ✔ · canlı ✘ |

---

## S1 — Hangi test boşluk doldurmayla başlıyor
**Koddan kesin olanlar:**
- **"Seviyeni yeniden ölç"** (profil satırı `levelRemeasureButton` ve ana sayfadaki seviye ölçüm kartı): sunucu `POST /api/Placement/remeasure` "başlangıç sorusu sormaz, tur mevcut seviyeden başlar" (`Controllers/Api/PlacementController.cs:81-86`). İlk ekran doğrudan bir **boşluk doldurma parçası**: metinde `___` işaretleri, altta numaralı sorular (`level_measure_view.dart:83, 733-752`). Mehmet'in tarifi ("doğrudan zor bir boşluk doldurmayla başlıyor") birebir buna uyuyor.
- **"Seviyeni belgele"** (profil satırı `asmEntryTile`, yalnız `AppConfig.assessmentEntryEnabled` açıkken): 4 soru dosyasında (`Assessment/reading-v1-a1/a2/b1/b2.json`) hiç `___` yok. İlk soru (A1) bir tabela sorusu: *"Shop open 9:00–17:00, Monday to Saturday." When is the shop closed?* Dört şıklı, okuma sorusu.
- İki testin girişi ayrı: yeniden ölçme profilde ve ana sayfa kartında (`level_measure_offer_card.dart:93`), onboarding'de de (`onboarding_v2_page.dart:339`); belgeleme yalnız profilde (`profile_page.dart:1827`).

**Bilinmiyor:** 20–21 Kasım kayıtları (hangi hesap, hangi test, nereden, ilk soru). Sorgu Q-S1.

**Karar etkisi:** Kayıt doğrulanmadan kesin söylenemez, ama kod "görülen test yeniden ölçmeydi" diyor. Bu doğrulanırsa T19 (belgeleme satırını gizleme) yanlış testi gizliyor olur. **T19'a dokunmadım**; ekip kararını bekliyor.

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

**Bilinmiyor:** son 7 günün sayıları ve A1'deki yarıda bırakma oranı. Sorgu Q-S5. Q1'in yeniden açılıp açılmayacağı bu sayıya bağlı; şu an söyleyemiyorum.

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
- **Yolculuk:** sunucunun yolculuk tohumunda (`DataAccess/Seed/JourneySeed.cs`; 6 yolculuk, 44 durak, slug ile bağlı) dokuzundan **hiçbiri yok**. Canlıda sonradan elle eklenmiş durak ya da ilgi alanına göre başlangıç yolculuğu (`Journeys.Interest`) olup olmadığını okuyamadım.
- **Başlangıç paketi (`IsStarterPack`), günlük havuz (`IsDailyUnlock`), yarıda okuyan:** canlı veri. **Bilinmiyor**, sorgu Q-S7.
- **Etiket A2 → B1 olunca kimin önünden kalkar** (`book_list_view_model.dart:322-457`; raf tavanı okurun seviyesi + 1):
  - **A1 okuru:** "Yeni eklenenler" ve vitrinden **kalkar** (tavan A2'ydi, B1 tavanı aşıyor). "Önerilen"de üst seviye cezası ikiye katlanıyor (`_levelOvershootPenalty = 2`), metinler sona iner.
  - **A2 okuru:** raflarda kalır (tavan B1), ama "Önerilen"de seviye farkı 0'dan "bir üst"e çıkar ve aşağı iner.
  - **B1 okuru:** **öne çıkar** (fark 1'den 0'a).
  - **B2 ve üstü:** fark küçülür, biraz yukarı çıkar.
  - Yolculuk ve günlük açma havuzu etiketten bağımsız. Okuyucu ekranı da etiketi kilit için kullanmıyor.

**Karar etkisi:** Kodda engel yok. Yarıda okuyan ve paket bilgisi okunmadan C-11 betiğine başlamıyorum.

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
1. **"A2 metinlerinin 69.091 kelimesinin 46.546'sı altı klasikten"**: **bilinmiyor** (canlı `ReadingTexts.WordCount` okunamadı). Sorgu Q-D1.
2. **"The Island Where Rabbits Won, A2 kullanıcısının ilk ücretsiz hikâyesi"**: **kodda tutmuyor.** Tohumda `starter-a2` sırası:
   1. Ali's First Snow
   2. The Cat Knows the Time
   3. Baba Yaga
   4. **The Island Where Rabbits Won**

   (`JourneySeed.cs:32-35`.) Canlıda sıra değiştirilmiş ya da ilgi alanına göre başka bir A2 başlangıç yolculuğu eklenmiş olabilir; okuyamadım (Q-D2). "93 başlayan" sayısı yolculuk öncesi döneme (ilk okuma kartı ve başlangıç rafı) ait olabilir; bu da doğrulanmadı.

---

## Bekleyen sorgular (salt okuma; canlı erişim açılınca çalıştırılacak)
```sql
-- Q-S1: 20–21 Kas seviye ölçümleri (Mehmet + test hesapları; e-postalar sorguda elle verilecek)
select u."Email", 'yeniden_olc' test, s."StartedAt", s."StartLevel", s."ResultLevel", s."Status", left(s."Raw",300) ilk_adim
from "PlacementSessions" s join "AspNetUsers" u on u."Id"=s."UserId"
where s."StartedAt" >= '2026-11-19 21:00' and u."Email" in (/* hesaplar */)
union all
select u."Email", 'belgele', a."StartedAt", null, null, a."Status"::text, null
from "AssessmentAttempts" a join "AspNetUsers" u on u."Id"=a."UserId"
where a."StartedAt" >= '2026-11-19 21:00' and u."Email" in (/* hesaplar */)
order by 3;
-- Nereden başlatıldı: aynı kullanıcıların UserEvents'inde (placement_*, career_*, screen_view) StartedAt ±2 dk

-- Q-S5: son 7 gün günün quizi turları, seviyeye göre
select p."CurrentCefrLevel", count(*) basladi, count(r."CompletedAt") bitti,
       round(avg(r."CorrectCount") filter (where r."CompletedAt" is not null),1) ort_dogru
from "VocabularyQuizRounds" r join "UserProfiles" p on p."UserId"=r."UserId"
where r."DailyQuizNumber" is not null and r."CreatedAt" >= now()-interval '7 days'
group by 1 order by 1;   -- müşteri süzgeci: test/promo hesapları hariç (önceki raporlardaki liste)

-- Q-S7: dokuz metin + 1023
select t."Id", t."Title", t."CefrLevel", t."IsStarterPack", t."IsDailyUnlock",
  (select string_agg(j."Slug"||'#'||s."Position", ', ') from "JourneyStops" s join "Journeys" j on j."Id"=s."JourneyId" where s."ReadingTextId"=t."Id") yolculuk,
  (select count(*) from "ReadingProgresses" rp where rp."ReadingTextId"=t."Id" and not rp."IsCompleted") yarim
from "ReadingTexts" t where t."Id" in (1096,1098,1039,1097,1103,1094,1063,1089,1067,1023);

-- Q-D1: A2 kelime sayıları
select sum("WordCount") a2_toplam,
       sum("WordCount") filter (where "Id" in (1096,1098,1039,1097,1103,1094)) alti_klasik
from "ReadingTexts" where "IsActive" and "CefrLevel"='A2';   -- sütun adı/değer tipini çalıştırmadan önce kontrol et

-- Q-D2: canlıdaki A2 başlangıç yolculukları ve sıraları
select j."Slug", j."Interest", s."Position", t."Title"
from "Journeys" j join "JourneyStops" s on s."JourneyId"=j."Id" join "ReadingTexts" t on t."Id"=s."ReadingTextId"
where j."Kind"='starter' and j."CefrLevel"='A2' and j."IsActive" order by j."SortOrder", s."Position";
```
(Sorgular çalıştırılmadı. Sütun adları kod modellerinden alındı; `CefrLevel`'ın tipi ve `AspNetUsers` tablo adı çalıştırmadan önce kontrol edilmeli.)
