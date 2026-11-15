# Editör raporu – Bölüm 1, ek: canlı veri ve düzeltmeler

**Tarih:** 15 Kasım 2026 (öğleden sonra) · **Rol:** Kent Bekçi; arayüz önerileri Dieter Koç, Don Normal, Paul Ulus ve Nassim Talip çerçeveleriyle. Tek geçiş; üyeler kurgusaldır.
**Neden ek:** Mehmet 1a'yı onayladı, canlı veritabanını okumaya izin verdi ve "yolda görülen" bulguların çözülmesini istedi. İlk rapor (`2026-11-15_editor_bolum1.md`) olduğu gibi duruyor; bu ek onun iki cümlesini düzeltir (aşağıda "Düzeltmeler").

## Özet

1. **Taban sayı yanlış.** Uygulamanın kendi kayıtlarına göre onboarding'i bitirenlerin %81–85'i okumaya başlıyor. Firebase'in "26 kişiden 18'i başlamadı" sayısı bunu doğrulamıyor. Kriz toplantısının 1. kararının ve 29 Kasım sınavının dayanağı yeniden yazılmalı.
2. **Android'de ödeme "başarısız" değil; deneyen çok az.** Test satın alması Android'de çalışıyor (son: 1 Kasım). Gerçek müşterilerden yalnız 2'si satın almaya basmış, ikisi de Google'ın penceresinden ödeme yapmadan çıkmış. Neden çıktıkları kaydedilmiyordu; artık kaydediliyor.
3. **iOS'taki deneme:** kullanıcı hesabı açıldıktan 35 saniye sonra, hiçbir şey okumadan denemeyi başlatmış, o akşam 6 dakika kalmış, bir daha açmamış ve son gün yenilemeyi kapatmış.
4. **Çözülenler (kodda, yerel dalda):** yeni son ekranın bekleme anı, büyük yazı tavanı, sekme çubuğu etiketleri, çevrimdışı sözlük bağlantısı, satın alma sonucu kaydı. Kelime sayısı için betik hazır, çalıştırılmadı.
5. **Benim hatam:** yer açarken Xcode'un derleme için ihtiyaç duyduğu iOS 26.1 simülatör platformunu sildim. iOS derlemeleri indirme bitene kadar çalışmıyor (10 GB, bu bağlantıda birkaç saat).

## Canlı veriden bulgular

Kaynak: prod veritabanı, 15 Kasım, yalnız okuma. "Müşteri" = hesap türü customer (test ve geliştirici hesapları hariç).

| # | Bulgu | Kanıt | Önem | Öneri |
|---|---|---|---|---|
| V1 | Onboarding'i bitiren müşterilerin çoğu okumaya başlıyor: 11–15 Kas 34 kişiden 29 (%85), 29 Eki–10 Kas 114 kişiden 92 (%81). İlk bir saat içinde başlayan: 28/34 ve 83/114. | `UserEvents`: `onboarding_completed` olan müşteriler × `reading_started` | yüksek | 29 Kasım sınavı bu sorguyla, sürüme göre ayrılarak okunsun. Hedef "ikiye katlamak" olamaz; gerçekçi hedef %82 → %90. |
| V2 | Hiç olayı olmayan 19 müşteri var (13 iOS, 6 Android). Hepsi "bitirdi ama okumadı" sayılsa bile başlama oranı %72. | `Users` × `UserEvents` | orta | V1'e alt sınır olarak not edilsin. |
| V3 | Android'de test satın alması çalışıyor: 1 Kasım'da haftalık (build 41), Ekim'de altı yıllık; hepsi sunucuda doğrulanmış. | `Subscriptions`, `Receipts` (Android, Sandbox, Valid) | – | İlk rapordaki "hiç görülmedi" cümlesi yanlıştı. |
| V4 | Satın alma hunisi (29 Eki'den beri, müşteri): iOS 122 kişi → 50 paywall gördü → 10 satın almaya bastı → 4 tamamladı. Android 65 → 23 → 2 → 0. | `PaywallAnalyticsEvents` × `Users.SignupPlatform` | yüksek | Fark ödeme hatasından değil, satın almaya basan sayısından geliyor (23'te 2'ye karşı 50'de 10). Sayılar küçük; hüküm verilmez. |
| V5 | Satın almaya basıp tamamlamayan 8 müşteride (2 Android, 6 iOS) sunucuya hiç makbuz gelmemiş; yani mağaza penceresinde kalmışlar. İptal mi hata mı, kayıt yok. | `Receipts`, `RequestMetrics` | yüksek | Kayıt eksikliği kodda kapatıldı (`9d169eb`). |
| V6 | Android'de satın almaya basan iki müşteriden biri hâlâ aktif: 7 gün, 17 biten metin. | `UserEvents` | orta | Tony Şeyh: bu kullanıcıya sorulabilir (uygulama içi geri bildirim ya da e-posta varsa). |
| V7 | iOS denemesi (7–14 Kas): hesap 20:11:13'te açılmış, 20:11:48'de deneme başlamış. Hiç okuma, kelime, XP kaydı yok. Son istek 20:17. 14 Kas 12:12'de yenileme kapatılmış. Kullanıcının saat dilimi UTC−8. | `Subscriptions`, `SubscriptionHistories`, `RequestMetrics`, `ReadingProgresses` | yüksek | Deneme, ürün denenmeden başlamış. Paywall'un ilk okumadan sonraya ertelenmesi kararını destekliyor. |
| V8 | Yeni müşterilerin yaklaşık %76'sına hesap açıldıktan sonraki iki dakika içinde Premium şeridi kaydı düşüyor; tetikleyici adı "yoğun kullanım" (`highEngagement`). | `PaywallAnalyticsEvents` (142/187) | orta | Sean Büyüt + Don Normal: şerit yeni kullanıcıya gösterilmeli mi, karar verilsin. Koda dokunulmadı. |
| V9 | Apple ve Google'ın abonelik bildirimleri hiç kaydedilmemiş (`WebhookEventLogs` boş). Yenileme ve iptaller uygulama açılınca ya da zamanlanmış kontrolle öğreniliyor. | `WebhookEventLogs`: 0 satır | orta | Kent Bekçi: mağaza panellerinde bildirim adresi tanımlı mı bakılmalı. |
| V10 | Kelime sayısı 287 aktif metnin 81'inde gerçek uzunluktan %15'ten fazla sapıyor (79'u fazla). İlk okuma hikâyesi 370 yazıyor, gerçek 287. | `ReadingTexts.WordCount` × metin | orta | Betik hazır: backend `MigrationScripts/RecomputeReadingTextWordCount_2026_11_15.sql`. Canlıya yazma Mehmet'in onayında. |
| V11 | "Seviyende şu kadar kitap var" ekranını yaklaşık 150 müşteriden 2'si görmüş. | `first_experience` adım 6 | düşük | Öneri: olduğu gibi kalsın, iş yapılmasın. Çalıştırmak herkese bir ekran daha eklemek olur. |
| V12 | Onboarding'i yarıda bırakanları sayması gereken sayaç yalnız hesabı olanları sayıyor; ilk ekranlar sayılmıyor. | `OnboardingScreenCounts`, `RequestMetrics` | orta | Nate Gümüş'e: onboarding kaybı bu sayaçla ölçülemiyor. Koda dokunulmadı. |

## Büyük yazı ayarı: önerilen ve yapılan

| Kim | Öneri |
|---|---|
| Dieter Koç | Tek kural, tek yerde: sistem yazı boyutu uygulamanın tamamında bir tavana kadar izlensin; her ekran o tavanda denensin. Gezinme çubuğu içerik değil, etiketi büyümesin. |
| Don Normal | Yazıyı büyüten kişi okumak için büyütür. Okuyucunun kendi boyut ayarı var; sistem ayarı onun üstüne sınırsız çarpan olmasın. İlk kullanım ipucu ekranın üçte birini kaplamasın. |
| Paul Ulus | Sayfada dört kelime cümleyi parçalar; kelimeye dokunup bağlamdan anlam çıkarma çalışmaz. Bir sayfa en az birkaç cümle taşımalı. |
| Nassim Talip | Tavan, çok büyük yazıya ihtiyacı olandan bir şey alır. Kaç kullanıcının büyük yazı kullandığı bilinmiyor; önce ölçülsün. |

Yapılan: uygulama genelinde tavan 1,3 (`lib/core/theme/app_typography.dart`, `lib/main.dart`, commit `64ba4fc`); sekme çubuğu etiketleri sistem ayarıyla büyümüyor. Onboarding'in 1,15'lik sınırı duruyor. Nassim'in şartı için ölçüm eklendi: her uygulama açılışı telefonun yazı boyutu ayarını (`text_scale`) taşıyor (`807c814`).

## Kod durumu (Flutter, yerel dal `feat/onboarding-first-story`, gönderilmedi)

| Commit | Ne |
|---|---|
| `5ff1250` | Yeni son ekran beklerken "Hikâyeni seçiyoruz" diyor; kapak önceden iniyor |
| `9d169eb` | Satın almada iptal ve hata, nedeniyle kaydediliyor |
| `2a9b61d` | İndirilmiş kitapta çevrimdışı çeviri bulunuyor |
| `64ba4fc` | Sistem yazı boyutu tavanı 1,3; sekme etiketleri büyümüyor |
| `807c814` | Uygulama açılışında yazı boyutu ayarı kaydediliyor |

Otomatik testler: 1064 geçti, 1 atlandı.

## Doğrulama durumu

**Android emülatöründe doğrulandı** (Pixel 7, Android 15, yazı ölçeği en büyük; debug derleme, sıfırdan kurulum):

| Ne | Sonuç | Görüntü |
|---|---|---|
| Tooltip (1d) | Balon açıkken ve deftere eklendikten sonra "Devam" yerinde | `ekran_2026-11-15/android_1d_balon_acik.jpg`, `android_1d_deftere_eklendi.jpg` |
| Yeni son ekran (1a) | Hikâye kartı, iki düğme; okuyucu açıldı, geri tuşu ana sayfaya döndü | `android_1a_son_ekran.jpg` |
| Yazı tavanı, ana sayfa | Kart ilk ekranda, sekme etiketleri tam | `android_tavan_ana_sayfa.jpg` (önce: `yan_ana_sayfa_enbuyuk_yazi.jpg`) |
| Yazı tavanı, okuyucu | Okunur sayfa, 5 sayfa; üst şerit taşmıyor | `android_tavan_okuyucu.jpg` (önce: `yan_okuyucu_enbuyuk_yazi.jpg`, 43 sayfa) |

**Doğrulanmadı:** aynı değişikliklerin iOS görüntüsü ve küçük ekranlı iPhone (iOS platformu inince yapılacak); Android'de gerçek cihaz; Android satın alma (Mehmet'in test hesabı gerekiyor).

## Ekip kararları

Mehmet bu turdaki kararları ekibe bıraktı (15 Kas). Tek geçiş, `ortak/kontrol-listesi.md` ile.

| Konu | Karar | Gerekçe ve itiraz |
|---|---|---|
| 29 Kasım hedefi | Onboarding'i bitirenlerin okumaya başlama oranı %82 → en az %90; uygulamanın kendi kayıtlarından, sürüme göre ayrılarak okunur. | Firebase sayısı tutmadı (V1). Nassim Talip: ~150 kişide 8 puan 12 kişi eder; sonuç "ders" yazılmaz. |
| Kelime sayıları (V10) | Düzeltilsin. | Paul Ulus: süre etiketi ve "50 kelimede 1" ölçüsü buna dayanıyor. Kent Bekçi: yedekli, geri alınabilir. Nassim'in sorusu (ilk hikâye değişir mi) kontrol edildi: üç ücretsiz metnin seçimi aynı kalıyor. **Uygulanmadı:** editörün canlıya yazması izin katmanında reddedildi; betiği Mehmet çalıştıracak. |
| "Kitap sayısı" ekranı (V11) | Dokunulmasın. | Çalıştırmak herkese bir ekran daha eklemek olur. |
| Yazı tavanı | 1,3 kalsın; iki hafta `text_scale` verisi birikince yeniden değerlendirilsin. | Nassim'in şartı ölçümle karşılandı. |
| Yeni kullanıcıya Premium şeridi (V8) | İlk okuma bitene kadar gösterilmesin. Sıradaki editör işi; bu turda kod değişmedi. | V7: deneme ürün görülmeden başladı, hiç okunmadı. Sean Büyüt şerh: şeridin tamamen kalkmasına karşı, ertelenmesini kabul ediyor. |
| Onboarding sayacı (V12) | Sıradaki editör işi. | Onboarding'i yarıda bırakanlar ölçülemiyor. |
| Yeni son ekran | Premium cümlesi eklenmedi; başlık "İlk hikâyen hazır." | Ekran tek şey söylesin. |
| `main`'e alma | iOS'ta da ekranda görüldükten sonra. | Android'de doğrulandı, 1064 test geçiyor. |

**Mehmet'e çıkanlar (yalnız onun yapabilecekleri):** kelime sayısı betiğini çalıştırmak ya da yazma izni vermek; Android satın alma testi; mağaza panellerinde sunucu bildirim adresine bakmak (V9).

## Düzeltmeler (ilk rapor)

- "Android'de satın almanın baştan sona çalıştığı hiç gözlenmedi" yanlıştı. Test satın almaları çalışıyor (V3). Gözlenmeyen şey gerçek bir müşterinin Android'de ödeme yapması.
- C3 (sunucudaki Play anahtarı) pratikte kapandı: 1 Kasım'da doğrulama çalıştı. Açılış denetimindeki boşluk kodda duruyor.
- İtirazlar 1'deki şüphe doğrulandı (V1).

## Yan etkiler

- **iOS derlemeleri geçici olarak çalışmıyor.** Yer açmak için kullanılmayan iki simülatör platformunu sildim (iOS 18.3.1 ve 26.1). Xcode 26.1, 26.1 platformunu derleme için istiyor. `xcodebuild -downloadPlatform iOS` ile yeniden indiriliyor.
- Diskte açılan yer: silinen iOS 18.3.1 platformu ve üç kullanılmayan simülatörün içeriği (iPhone 16e, iPad A16, iPhone 17). Boş alan 0,2 GB'tan yaklaşık 16 GB'a çıktı; 26.1 geri gelince yaklaşık 8 GB kalır.
- Prod'da iki misafir hesap daha açıldı (çekimler).
