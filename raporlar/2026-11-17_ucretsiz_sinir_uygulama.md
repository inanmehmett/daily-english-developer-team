# Ücretsiz sınırların uygulanması

**Tarih:** 17 Kasım 2026. **Görev:** `ortak/editor_gorevi_2026-11-17_ucretsiz_sinir_uygulama.md`. **Dayanak:** `raporlar/2026-11-17_ucretsiz_sinir_karari.md`.
**Durum:** Kod yazıldı, testler geçti, commit'lendi. **Hiçbir dal gönderilmedi.** Canlı veritabanına yazılmadı; sunucu ve uygulama yayını Mehmet'te.

| Depo | Dal | Commit |
|---|---|---|
| Sunucu (`DailyEnglish`) | `feat/free-limits` (`master`'dan) | `9c12fc5` okuma sayacı kaldırıldı · `19d1482` çeviri sayımı, defter, kayıt |
| Flutter | `feat/free-limits` (`fix/paywall-trigger-attribution`'dan) | `a8acbb7` sınırlar, metinler, sınır sayfaları, ölçüm · `a4ab665` paywall düzeni |

Flutter dalı, paywall tetikleyicisi dalının üstüne açıldı; sınır sayfaları o daldaki tetikleyici adlarını kullanıyor. İki dal birlikte birleşmeli.

## Ne değişti

| # | Madde | Sunucu | Flutter |
|---|---|---|---|
| 1 | **Çeviri sayımı** | `TranslateWord` ve `TranslateSentence` her istekte ücretsiz kullanıcının hakkından 1 düşüyor; sözlük ve önbellek ayrımı kalktı. Sınır 25 kaldı, dolunca 402 dönüyor. | Değişmedi (402 zaten sayfayı açıyor). |
| 2 | **Defter** | "İlk 7 gün sınırsız" kuralı (`FreeWordQuota`, `FreeUnlimitedWordDays`) kalktı; ilk günden toplam 15. Mevcut kayıtlar silinmez, yalnız yeni kayıt kapanır. | Defterdeki "ilk hafta sınırsız" notu ve modeldeki alanlar kalktı. |
| 3 | **Okuma sayacı** | Hiç çağrılmayan `use-reading-quota` ucu ve `UseReadingQuotaOnCompletionAsync` silindi. `freemium-status` yanıtının biçimi korundu (aşağıya bkz.). | Okuyucudaki okuma sınırı kontrolü, `FreemiumService` / repository / model ve "günlük okuma hakkın bitti" sayfası silindi. Erişim kuralı (kilit + günde 1 açma) aynen duruyor. |
| 4 | **Yanlış metinler** | — | Onboarding paywall'undaki "Günlük 3 okuma limiti kalkar" ve okuma sonrası "X okuma hakkın kaldı" kalktı. Premium maddeleri gerçek sınırlarla yazıldı: tüm kütüphane, sınırsız çeviri (25), sınırsız defter (15), seri koruma, internetsiz okuma. Karşılığı olmayan "reklamsız" ve "detaylı istatistik" maddeleri de kalktı. |
| 5 | **Sınır sayfası** | — | Çeviri: "Bugünkü 25 kelimen bitti" + "Yarın yenilenir. Okumaya ve dinlemeye devam edebilirsin." + **Premium'la sınırsız** + "Okumaya devam et". Defter aynı yapıda: "slippery sığmadı" + **Premium'la sınırsız** + "Kapat". |
| 6 | **Ölçüm** | Sınıra çarpınca servisin kendisi `AuditLogs`'a `limit_reached` yazıyor; tür `Details`'te (`translation` / `vocabulary`). | `limit_reached` olayı, `type` alanıyla: `translation` (çeviri sayfası açılınca), `vocabulary` (defter sayfası açılınca), `locked_content` (kilitli önizleme, okuyucu engeli, kilitli dizi bölümü, bitişte kilitli bölüm). |
| 7 | **Paywall düzeni** | — | Planlar yüklenince seçili kart, sabit düğmenin hemen üstüne kaydırılıyor. Kart zaten görünüyorsa sayfa kaymıyor. |

**Okuma sonrası pencere:** canlıdaki davranış korundu. İlk hafta pencere yok; sonrasında aynı pencere çıkıyor ama "okuma hakkın kaldı" satırı yok.

## Kararlardan sapmalar ve sınırlar

- **Paywall tetikleyicisi `limitReached` yerine alt türün adı.** Sınır sayfalarından açılan paywall `translationLimit` ve `vocabularyLimit` ile kaydediliyor. `limitReached` yazılsaydı `PaywallAnalyticsEvents.Trigger`'da çeviri ile defter ayrışmazdı. Bu adlar bir önceki iş (`fix/paywall-trigger-attribution`) ile tanımlandı.
- **"Premium sesler" yazılmadı.** Uygulamada seçilebilen bir Premium ses yok; yalnız kullanılmayan bir yetki bayrağı (`canAccessPremiumVoices`) var. Bunu yazmak, düzelttiğimiz türden yanlış bir söz olurdu. Ürün eklenirse madde de eklenir.
- **`freemium-status` okuma alanları silinmedi.** 1.0.2 ve 1.0.4 bu alanı okuyor. Biçimi değişirse eski sürümler okuma sonrası yeni pencere açar. Sayaç hiç artmadığı için `canRead` her zaman `true`; alanın yanına not düşüldü. Eski sürümler kalkınca silinebilir.
- **"Her istek" sunucuya giden istektir.** Uygulamanın kendi bellek önbelleğinden gelen tekrar dokunuşları (aynı oturumda aynı kelime) sunucuya gitmediği için sayılmıyor. 15 Kasım verisinde bu, dokunuşların yaklaşık yedide biri.
- **Defter sınırını atlayan bir yol var.** Sunucudaki `SyncService` kelime eklerken sınırı denetlemiyor. Uygulama bu ucu kullanmıyor; dokunulmadı.
- **Onboarding plan ekranı haftada 14–42 kelime hedefi gösteriyor.** Bu bir defter sözü değil, okuma hedefi; ama ücretsiz defter artık 15'te durduğu için çelişkili okunabilir. Dokunulmadı; karar ekipte.
- **Eski sürümlerde çeviri sayfası eski metinle açılır.** Yeni sayım sunucu yayınıyla herkese uygulanır. Yeni sayfa ve ölçüm ise yalnız yeni uygulama sürümünde görünür.

## Testler

- **Sunucu:** `dotnet test` 1523 geçti, 0 kaldı (3 atlanan, önceden de atlanıyordu).
  - Yeni: bugün açılmış hesap 15 kelimede duruyor.
  - Yeni: çeviri sınırında `limit_reached` kaydı yazılıyor.
  - `FreeWordQuotaTests` kuralla birlikte silindi.
  - Çeviri uçlarının her istekte hak düşmesi birim testle sınanmadı: denetleyicinin çok fazla bağımlılığı var. Değişiklik koşulsuz bir çağrı; düşümün kendisi servis testlerinde sınanıyor.
- **Flutter:** `flutter analyze` temiz; `flutter test` 1108 geçti.
  - Yeni: çeviri ve defter sınır sayfalarının metni, düğmeleri ve kapanması.
  - Kalkan okuma sınırı sayfasının testi silindi.
- **Paywall düzeni:** Sayfa için widget testi yok (çok sayıda servise bağlı). iPhone SE 3 simülatöründe normal yazı ve en büyük sistem yazısıyla (uygulamanın 1,3 tavanı uygulanmış hâlde) görüntüyle doğrulandı.

## Ekran görüntüleri (`raporlar/ekran_2026-11-17/`)

| Dosya | Ne gösteriyor |
|---|---|
| `sinir_paywall_se3.jpg` | SE 3, normal yazı. Seçili yıllık kart tamamen görünüyor, hemen altında düğme. Önceki hâli: `paywall_se3_ilk.jpg` (kartın altı düğmenin altında). |
| `sinir_paywall_se3_buyuk.jpg` | SE 3, en büyük sistem yazısı. Başlık yukarı kaymış; seçili kart ve düğme birlikte görünüyor. |
| `sinir_ceviri_siniri_se3.jpg`, `sinir_ceviri_siniri_se3_buyuk.jpg` | Çeviri sınırı sayfası. |
| `sinir_defter_siniri_se3.jpg` | Defter sınırı sayfası. |

Fiyatlar simülatörün StoreKit test dosyasından geliyor (USD); gerçek TR fiyatları cihazda farklı.

## Yayın öncesi (Mehmet)

1. Sunucu `feat/free-limits` → `master` → Railway. Migration yok. Yeni çeviri sayımı yayın anından itibaren bütün sürümlere uygulanır.
2. Flutter: önce `fix/paywall-trigger-attribution`, sonra `feat/free-limits` birleşir; sonra 1.0.4 derlemesi.
3. Karardaki geri alma kuralı için yayın tarihi kayda geçmeli. Yayından 2 hafta sonra `limit_reached`, satış ve ertesi gün dönüşü okunur.
