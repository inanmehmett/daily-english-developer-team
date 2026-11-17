# Satın alma kararlarının uygulanması

**Tarih:** 17 Kasım 2026. **Dayanak:** `raporlar/2026-11-17_satin_alma_anlari_karar.md`.
**Durum:** Flutter `fix/paywall-trigger-attribution` dalında. **Commit ve push yok**; yayına alma Mehmet'te.

## 1. V8 geri alındı

`8069597` ("Premium şeridini ilk metin bitene kadar gizle") geri alındı. Şerit, 1.0.2+45'te olduğu gibi Premium olmayan herkese görünüyor. Bugün canlıda olan davranış zaten bu; yani müşteri açısından değişen bir şey yok. Değişen, 1.0.4 yayınına V8'in girmemesi.

## 2. Paywall'u açan her çağrı tetikleyiciyi geçiriyor

**Sorun:** Paywall sayfası tetikleyiciyi rota argümanından okuyordu, ama onu açan hiçbir çağrı bu argümanı vermiyordu. Bu yüzden her gösterim `manual` yazılıyordu.

Satın alma tamamlanma olayları (`subscription_completed`, `trial_started`, `offer_selected`) de `SubscriptionBloc`'ta sabit `manual` ile yazılıyordu. Kampanya sayfası ise her olayı sabit `milestone` ile yazıyordu.

**Şimdi:**
- `PremiumBanner.openPaywall`, `PremiumGate.buildPremiumPaywallRoute`, `PremiumGate.buildCampaignPaywallRoute`, `PremiumPaywallPage` ve `CampaignPaywallPage` tetikleyiciyi **zorunlu** parametre olarak alıyor. Tetikleyicisiz yeni bir çağrı derlenmez.
- `SubscriptionBloc`, kurulduğu yüzeyin tetikleyicisini alıyor ve tamamlanma olaylarını onunla yazıyor.
- Paywall'un kampanya sorgusu ve günlük tavanları eskisi gibi `manual` ile çalışıyor. Tetikleyici yalnız kayda yazılıyor; gösterilen teklif değişmiyor.
- Sunucu tarafında değişiklik gerekmiyor. `PaywallAnalyticsEvents.Trigger` 50 karakterlik serbest metin. Kampanya ucu tanımadığı tetikleyici adında `manual`'daki gibi en iyi kampanyaya düşüyor.

**Yüzey → `trigger` değeri:**

| Yüzey | `trigger` |
|---|---|
| Ana sayfa Premium şeridi (dokunuş) | `highEngagement` (şeridin kendi gösterim/tıklama kaydıyla aynı ad) |
| Kilitli kitap, kilitli bölüm, kilitli dizi bölümü, bitiş sahnesinde kilitli bölüm | `lockedContent` |
| Çevrimdışı indirme, değerlendirme raporu | `premiumFeature` |
| Günlük okuma hakkı penceresi ve okuma sonrası "hakkın bitti" teklifi | `readingLimit` |
| Çeviri hakkı bitti ya da azaldı | `translationLimit` |
| Kelime defteri dolu | `vocabularyLimit` |
| Günlük açma kullanıldı | `dailyUnlockUsed` |
| İlk okumadan sonra açılan ertelenmiş paywall | `deferredFirstRead` |
| Okuma Yolculuğu şeridi / kampanya sandığı | `levelJourney` / `journeyChest` |
| Hediye teklifi ve köşe çipi | `giftOffer` |
| İptal akışındaki indirim | `saveFlow` |
| Profil sayfası Premium satırı | `profile` |
| Girişten sonra "Teklifi gör" | `welcomeBack` |
| Okuma sonrası teklif (hak varken) | `milestone` |
| Quiz başarısı teklifi | `quizSuccess` |
| Onboarding paywall'u, ücretsiz deneme sayfası | `onboarding` |
| Seri riski sayfası | `streakAtRisk` |
| Geri dönüş teklifi | `winBack` |
| Yalnız önizleme aracında genel şerit | `manual` |

Uygulamada `manual` artık yalnız paywall önizleme aracında geçiyor.

**Doğrulama:**
- `flutter analyze`: sorun yok.
- `flutter test`: 1108 test geçti.
- Yeni bir test eklendi: bloc, kurulduğu yüzeyin tetikleyicisini plan seçimi kaydına yazıyor (`test/subscription_bloc_test.dart`).
- Cihazda olay kaydı henüz görülmedi. 1.0.4 canlıya çıkınca `PaywallAnalyticsEvents.Trigger` dağılımından kontrol edilmeli.

**Bilinen eksik (bu turda dokunulmadı):** Şeridin `banner_click` kaydı yalnız etkin bir kampanya varken yazılıyor (`SmartPremiumBanner._openPaywall`). Bu yüzden 18 günde yalnız 1 tıklama görünüyordu. Artık şeritten açılan paywall `highEngagement` ile yazıldığı için tıklama bu yoldan da sayılabilecek.

## 3. Paywall'da varsayılan plan ve aylık planın görünürlüğü (değişiklik yok)

Görüntüler `raporlar/ekran_2026-11-17/` klasöründe:
- `paywall_iphone17.jpg`: iPhone 17, normal yazı boyutu.
- `paywall_se3_ilk.jpg`: iPhone SE 3, ilk açılış.
- `paywall_se3_kaydirilmis.jpg`: iPhone SE 3, kaydırılmış.

Simülatörde mağaza fiyatları Xcode'un test dosyasından (`Products.storekit`) geliyor ve USD görünüyor. Gerçek TR fiyatları cihazda başka. Planların sırası, seçimi ve görünürlüğü ise aynı kodla çalışıyor.

| | Bulgu |
|---|---|
| Plan sırası | Haftalık, Aylık, Yıllık (yukarıdan aşağı; tür sırasına göre). |
| Varsayılan seçili plan | **Yıllık** (lansman ürünü). `SubscriptionBloc` mağazadan gelen planlardan `isBestValue` olanı seçiyor; bu da her zaman yıllık. |
| Yıllık kartta | "EN İYİ DEĞER · %58" etiketi, turuncu çerçeve, günlük ve aylık karşılık. |
| Aylık kartta | Fiyat ve "günde $0,13"; etiket, deneme ya da tasarruf yazısı yok. |
| Deneme | Yalnız yıllıkta (7 gün). Başlıktaki "7 gün ücretsiz dene" ve "Ücretsiz Dene" düğmesi **seçili plana göre** değişiyor; aylığa dokununca deneme satırı kalkıyor. |
| iPhone 17 | Üç plan, yasal satır ve düğme tek ekranda; kaydırma gerekmiyor. |
| iPhone SE 3 | Üç plan görünüyor, ama seçili yıllık kartın alt kısmı ilk açılışta sabit "Ücretsiz Dene" düğmesinin altında kalıyor. Kaydırınca tamamı görünüyor. |
| 15 Kasım, küçük iOS ekranı, büyük yazı (`ekran_2026-11-15/b3_ios_kucuk_paywall.jpg`) | Seçili yıllık kart hiç görünmüyor; aylık kartın yarısı görünüyor. Düğme "Ücretsiz Dene", altında "Sonra $19,99/yıl" yazıyor. Kullanıcı hangi planın seçili olduğunu görmeden yıllık denemeye basabiliyor. |

**Okuma (öneri değil):** Aylık plan görünür ve seçilebilir, ama sayfanın bütün vurgusu yıllıkta: varsayılan seçim, etiket, renk ve deneme. 10 tamamlamayanın 10'unun yıllıkta basması bu varsayılanla uyumlu. Yıllık seçili geldiği için bu, "yıllığı seçtiler" değil, "değiştirmediler" diye de okunabilir.

### Dieter Koç bulgusu: seçili plan küçük ekranda ve büyük yazıda görünmüyor — **ENGELLEYİCİ**

**Ne:** Paywall yıllık planı seçili açıyor; ama küçük ekranda bu kart görünür alanın dışında kalıyor.
- iPhone SE 3'te, normal yazıda, kartın alt kısmı sabit "Ücretsiz Dene" düğmesinin altında kalıyor.
- Küçük ekran ve büyük yazıda (15 Kasım çekimi) kart hiç görünmüyor; ekranda haftalık ve aylığın yarısı duruyor.

Kullanıcı hangi planın seçili olduğunu görmeden düğmeye basabiliyor. Düğmenin altındaki "Sonra $19,99/yıl" satırı tek ipucu.

**Neden engelleyici:**
- Kullanıcı bir yıllık aboneliği ve denemeyi, seçimi görmeden başlatabiliyor.
- Apple'ın abonelik kuralı (3.1.2), satın alınan ürünün süresinin ve fiyatının açıkça görünmesini istiyor; inceleme riski taşıyor.
- 15 Kasım'daki V7 vakası (35 saniyede yıllık deneme, sonra iptal) bu ekran düzeniyle uyumlu.

**Düzeltme seçenekleri (karar ekipte; kod yazılmadı):**
1. **Seçili kart her zaman görünür açılsın.** Sayfa açılınca liste seçili karta kaydırılsın; ya da varsayılan seçili plan listenin en üstünde dursun. Küçük ekranda başlık ve fayda satırları kısaltılabilir. Böylece kart, sabit düğmenin üstünde kalan alana sığar. Değişiklik yalnız düzen; teklif aynı kalır.
2. **Sabit düğme seçimi kendisi söylesin.** Düğmenin hemen üstünde ya da üzerinde seçili planın adı, fiyatı ve süresi yazsın (ör. "Yıllık · $19,99/yıl · 7 gün ücretsiz"). Kart görünmese de kullanıcı neyi aldığını bilir. Satır sabit alanda olduğu için büyük yazıda da kaybolmaz.

İki seçenek birlikte de uygulanabilir. İkincisi, büyük yazıda düzenin ne kadar sıkışacağından bağımsız olarak çalışır.

## Ayrıca: okuyucuda balon ve vurgu yanlış satırı gösteriyordu (aynı dalda)

Tek satırlık bir paragrafın son kelimesine dokununca ("I walked to the bus with my fish." → "fish") vurgu kutusu ve balon bir alt satırdaki boşluğu gösteriyordu.

**Kök neden:** Ekrandaki metin Türkçe yerel ayarla diziliyor; Türkçede "fi" bitişik harfi kullanılmıyor ve satır biraz daha dar çıkıyor. Vurgu ve balon ölçümü ise yerel ayar olmadan, ayrı bir yeniden dizmeyle yapılıyordu. Tek satırlık paragrafın kutusu satırın kendi genişliği kadar olduğu için daha geniş ölçülen son kelime alt satıra düşüyordu.

**Düzeltme:** Balon konumu artık ekrandaki paragraftan ölçülüyor. Vurgu çizimi de aynı yerel ayarı alıyor; bu düzeltme onboarding dinleme demosunu da kapsıyor. Gerçek Lora yazı tipi ve Türkçe yerel ayarla yazılan test eski kodda kırılıyor, yenisinde geçiyor.
