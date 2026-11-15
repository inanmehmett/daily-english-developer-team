# Arayüz taraması – Aşama 1

**Rol:** Dieter Koç (arayüz). **Tarih:** 15 Kasım 2026. **Dal:** `feat/onboarding-first-story` (Flutter, yerel; gönderilmedi).

Kontrol listesi: `uyeler/dieter_koc_arayuz.md` (yedi madde). Görüntüler: `raporlar/ekran_2026-11-15/b3_*.jpg`.

## Nasıl tarandı

Uygulama her turda silinip yeniden kuruldu; misafir olarak onboarding'den paywall'a kadar bütün akış otomatik sürüldü (`integration_test/critique_shots_test.dart`, tur başına 59-60 görüntü).

| Koşul | Android | iOS |
|---|---|---|
| (a) En küçük ekran + en büyük yazı | Emülatör 360×640 dp, `font_scale 2.0` | Simülatör 375×667 (iPhone SE 3), en büyük erişilebilirlik boyutu |
| (b) Yaygın ekran + varsayılan yazı | Pixel 7, Android 15 | iPhone 17 Pro simülatörü, iOS 26.2 |

Kapsam: onboarding'in 17 ekranı, ana sayfa (yeni ve okumuş kullanıcı), keşfet, okuyucu (kelime balonu, cümle çevirisi, ses çubuğu, ayarlar), bitiş ekranı, quiz, kelime defteri, profil, profil düzenleme, bildirim ayarları, paywall.

Sınırlar:
- Uygulama sistem yazı boyutunu 1,3 katta tutuyor (`lib/main.dart`, `AppTypography.maxSystemTextScale`). "En büyük yazı" koşulu bu yüzden fiilen 1,3 kat demek.
- "Hareketi azalt" ayarı açıkken tur atılmadı; o madde koddan okundu.
- Gerçek cihazda bakılmadı; hepsi emülatör ve simülatör.

## Özet

Yaygın ekranda ve varsayılan yazıda, iki platformda da kontrol listesine takılan bir ekran yok. Bulguların hepsi küçük ekran + büyük yazı koşulunda, bir kısmı da koddan çıktı.

En ağır bulgular 360×640 Android ekranında çıkıyor. 375×667 iOS ekranı biraz daha geniş ve uzun olduğu için 4, 5, 6 ve 9 orada görünmüyor (`b3_ios_kucuk_soz_ver.jpg`); 7 orada da var (`b3_ios_kucuk_seviye.jpg`).

| # | Önem | Bulgu | Durum |
|---|---|---|---|
| 1 | Yüksek | Quiz girişinde "Başla" düğmesi ekran dışında | Düzeltildi; iki platformda küçük ekranda doğrulandı |
| 2 | Yüksek | Günün quizi ekranı taşıyor | Düzeltildi; iki platformda küçük ekranda doğrulandı |
| 3 | Yüksek | Paywall'da yıllık plan kartı bozuk | Düzeltildi; 360×640 Android'de doğrulandı |
| 4 | Yüksek | "Söz ver" ekranında parmak izi ekranın altında | Açık |
| 5 | Orta | Onboarding ilk ekranı taşıyor (sarı-siyah şerit) | Açık |
| 6 | Orta | İlgi alanı kartlarında kelime ortadan bölünüyor | Açık |
| 7 | Orta | Seviye ve amaç kartlarında açıklama kesiliyor | Açık |
| 8 | Orta | Paywall'da fayda satırları kesiliyor | Açık |
| 9 | Orta | Ana sayfada "Okumaya başla" düğmesi sekme çubuğunun altında | Açık |
| 10 | Orta | Dokunma hedefleri alt sınırın altında (3 yer) | Açık |
| 11 | Orta | "Planın oluşturuluyor" en az 6,3 saniye bekletiyor | Açık |
| 12 | Orta | Animasyonlar "hareketi azalt" ayarına bakmıyor | Açık |
| 13 | Düşük | Plan özeti ve son ekranda kart sabit düğmenin altında kesik başlıyor | Açık |
| 14 | Düşük | Profil düzenlemede "İsmi kaydet" bağlantısı kesik | Açık |
| 15 | Düşük | "Planın oluşturuluyor"da iki durum yazısı üst üste biniyor | Açık |
| 16 | Düşük | Bitiş ekranındaki "Sona göz attın" uyarısı dar sütuna sıkışıyor | Açık |

1-3 için not: Aşama 1'de kod değişikliği yapılmayacaktı. Bu üçü kullanıcının ilerlemesini engellediği için Mehmet'in "diğer adımların hepsini yap" talimatı kapsamında düzeltildi; ortak bileşenle (`FitOrScroll`), ekran bazında yama olmadan.

## Bulgular

### Yüksek

**1. Quiz girişinde "Başla" düğmesi ekran dışında** (madde 1)
Küçük ekranda içerik 128 px taşıyor, düğme görünmüyor, sayfa kaydırılmıyor. Kullanıcı kelime quizini başlatamıyor.
Görüntü: `b3_kucuk_quiz_giris.jpg`. Kod: `lib/features/quiz/presentation/widgets/vocabulary_quiz_intro.dart`.
Düzeltme `867d9b4`: içerik sığmazsa kayar, düğme altta sabit. Test: `test/quiz_small_screen_test.dart`.
Sonrası: aynı koşulda quiz başlatılıp çözülebildi (`b3_kucuk_quiz_soru_sonra.jpg`).

**2. Günün quizi ekranı taşıyor** (madde 1)
"Alıştırma" satırı 22 px taşıyor ve taşma şeridinin altında kalıyor.
Görüntü: `b3_kucuk_quiz_hazirlik_tasma.jpg`. Kod: `lib/features/quiz/presentation/widgets/daily_quiz_landing.dart`.
Düzeltme `867d9b4` (aynı bileşen). Sonrası: `b3_kucuk_quiz_hazirlik_sonra.jpg`, `b3_ios_kucuk_quiz_sonra.jpg`.

**3. Paywall'da yıllık plan kartı bozuk** (madde 1)
Plan adı tek harfe sıkışıp dikey yazılıyor ("Y / ı / l…"), fiyatın yanında taşma şeridi çıkıyor. Satın alma ekranının ana kartı okunmuyor.
Görüntü: `b3_kucuk_paywall_once.jpg`. Kod: `lib/features/subscription/presentation/widgets/subscription_card.dart`.
Düzeltme `e0d568b`: ad ve rozet sığmazsa alt satıra iner. Test: `test/subscription_card_narrow_test.dart`.
Sonrası: `b3_kucuk_paywall_sonra.jpg`. Küçük iPhone'da kartlar zaten düzgün (`b3_ios_kucuk_paywall.jpg`).

**4. "Söz ver" ekranında parmak izi ekranın altında** (madde 1, 4)
Ekranın tek eylemi parmak izine basılı tutmak. Küçük ekranda parmak izinin yarısı ve "Söz veriyorum" yazısı görünmüyor; düğme olmadığı için kullanıcı ekranın bittiğini sanabilir.
Görüntü: `b3_kucuk_soz_ver.jpg`. Kod: `lib/features/onboarding/presentation/widgets/v2/steps/step_11_commitment.dart:45` (`V2FitOrScroll` sabit alt bölüm olmadan kullanılmış).

### Orta

**5. Onboarding ilk ekranı taşıyor** (madde 1)
Başlığın altında sarı-siyah taşma şeridi; alt yazı hiç görünmüyor. Şerit yalnız test derlemesinde çizilir; yayın sürümünde alt yazı sessizce kesilir. Uygulamanın ilk ekranı.
Görüntü: `b3_kucuk_onboarding_ilk_ekran.jpg`. Kod: `step_00_value_prop.dart:26-57` (sabit yükseklikli kapak yelpazesi, satır 76).

**6. İlgi alanı kartlarında kelime ortadan bölünüyor** (madde 1, 5)
"Edebiya / t", "Efsanele / r". İki sütunlu dar kartta uzun kelime sığmıyor.
Görüntü: `b3_kucuk_ilgi_alanlari.jpg`. Kod: `step_10_interests.dart:88`, `v2_option_card.dart:101`.

**7. Seviye ve amaç kartlarında açıklama kesiliyor** (madde 1)
"Kendimi tanıtır, basit cümleler …", "Toplantı, yazışma, …". Kullanıcı seviyesini bu açıklamaya göre seçiyor; yarım cümleyle seçiyor.
Görüntü: `b3_kucuk_seviye.jpg`. Kod: `v2_option_card.dart:110` (`subtitleMaxLines`), `step_05_level.dart:129`, `step_05b_goal.dart:96`.

**8. Paywall'da fayda satırları kesiliyor** (madde 1, 7)
"Tüm kütüphane açılır — şimdi 3 hikâ…". Satın alınan şeyin tarifi yarım. İki platformda da var. Yıllık kartın alt satırı da kesiliyor ("günde ₺2,74 · ₺8…").
Görüntü: `b3_kucuk_paywall.jpg`. Kod: `lib/features/subscription/presentation/widgets/paywall_benefit_list.dart:39` (`maxLines: 1`).

**9. Ana sayfada "Okumaya başla" düğmesi sekme çubuğunun altında** (madde 1, 4)
Yeni kullanıcının ana sayfasındaki tek ana eylem ilk açılışta çubuğun arkasında; görmek için kaydırmak gerekiyor.
Görüntü: `b3_kucuk_ana_sayfa.jpg`. Kod: `lib/features/home/presentation/pages/home_page.dart` (ilk okuma kartı).

**10. Dokunma hedefleri alt sınırın altında** (madde 3)
Alt sınır iOS'ta 44, Android'de 48.
- Onboarding geri düğmesi 34×34: `v2_scaffold.dart:91-93`.
- Kelime balonunda ses düğmesi 28×28: `word_balloon.dart:278-279`.
- Kelime balonunda deftere ekle düğmesi 40×40: `word_balloon.dart:427-428`.
Görüntü: `b3_kucuk_balon.jpg`.

**11. "Planın oluşturuluyor" en az 6,3 saniye bekletiyor** (madde 6)
Sayaç 55 ms'de bir %1 artıyor, sonunda 0,8 sn duruyor: 100 × 55 + 800 = 6.300 ms. Arkada yapılan bir iş yok; bekleme süs. Bildirim sorusu çıkarsa süre uzuyor.
Kod: `step_12_plan_building.dart:79-85`.

**12. Animasyonlar "hareketi azalt" ayarına bakmıyor** (madde 6)
Bütün kodda ayarı okuyan tek yer açılış ekranı (`splash_screen.dart:152`). Onboarding'in giriş animasyonları, konfeti, rozet kutlaması ve bitiş ekranı ayar açıkken de oynuyor.
Kod: `v2_motion.dart` (kontrol yok).

### Düşük

**13. Plan özeti ve son ekranda kart sabit düğmenin altında kesik başlıyor** (madde 1)
İçerik kayıyor ve düğme görünüyor; ama "7 hikâye / 21 kelime" sayılarının etiketi ve ilk hikâyenin süresi ilk bakışta görünmüyor.
Görüntü: `b3_kucuk_plan_ozeti.jpg`, `b3_kucuk_son_ekran.jpg`.

**14. Profil düzenlemede "İsmi kaydet" bağlantısı kesik** (madde 1)
Görüntü: `b3_kucuk_profil_duzenle.jpg`.

**15. "Planın oluşturuluyor"da iki durum yazısı üst üste biniyor** (madde 6)
Durum yazısı değişirken eski ve yeni satır 250 ms boyunca aynı yerde okunmaz biçimde çakışıyor (biri iki satır, diğeri tek satır).
Kod: `step_12_plan_building.dart:212`.

**16. Bitiş ekranındaki "Sona göz attın" uyarısı dar sütuna sıkışıyor** (madde 1)
Metni okumadan sona atlayan kullanıcıya çıkan uyarı küçük ekranda altı satıra bölünüyor ve "Kitabı bitirdin" başlığını örtüyor; yazı düğmenin yanında dar bir sütunda kalıyor.
Görüntü: `b3_ios_kucuk_bitis_uyari.jpg`. Kod: `lib/features/reader/presentation/pages/advanced_reader_page.dart:2543`.

### Sorunsuz bulunanlar

- Okuyucu: küçük ekranda metin, balon, cümle çevirisi, ses çubuğu ve ayarlar sayfası sağlam (`b3_kucuk_okuyucu.jpg`). Balon metnin üstünde açılıyor, satırları kaydırmıyor (madde 2).
- Bitiş ekranı, quiz soru ve sonuç ekranı, kelime defteri, bildirim ayarları: iki koşulda da taşma yok (`b3_yaygin_bitis.jpg`, `b3_yaygin_quiz.jpg`).
- Okumadan sonra ana sayfa ve keşfet rafları dolu geliyor (`b3_kucuk_okuma_sonrasi.jpg`, `b3_yaygin_okuma_sonrasi_dolu.jpg`). İlk turda boş iskelet kalıyordu (`b3_yaygin_okuma_sonrasi_bos_raflar.jpg`); `646fa81` ile düzeltildi.
- Dürüstlük (madde 7): paywall'da kapat düğmesi baştan görünür, gecikmeyle açılmıyor. Son onboarding ekranında "Önce uygulamaya göz atayım" seçeneği okunur boyutta.

## Animasyon dökümü

| Yer | Animasyon | Süre | İşi | Bekletiyor mu |
|---|---|---|---|---|
| Onboarding, her ekran | Öğeler sırayla aşağıdan belirir (`V2RiseIn`, `V2Stagger`) | 520 ms + öğe başına 90 ms | Okuma sırasını gösterir | Hayır; düğme en son belirir (yaklaşık 0,8 sn) |
| Kelimeye dokun | Kelimenin çevresinde halka (`V2TapPulse`) | 1,6 sn, döngü | Nereye dokunulacağını gösterir | Hayır |
| Dinle | İşaret sallanır (`V2CueBob`) | 1,1 sn, döngü | Oynat düğmesine çeker | Hayır |
| Söz ver | Basılı tutunca dolan halka | 1,0 sn | Sözün "mühürlendiğini" gösterir | Evet: 1 sn basma + 2 sn bekleme (`step_11_commitment.dart:39`) |
| Planın oluşturuluyor | Yüzde çubuğu, yorum kartları (3,2 sn'de bir) | En az 6,3 sn | Yok; plan o sırada hesaplanmıyor | Evet |
| Plan özeti | Satırlar 0,5-0,95 sn gecikmeyle belirir | yaklaşık 1,5 sn | Sıra duygusu | Kısmen; düğme en son gelir |
| Onboarding paywall | Giriş, nabız, parıltı | 0,6-3 sn, parıltı döngü | Dikkati plana çeker | Hayır |
| Kelime balonu | Açılıp kapanma | kısa | Hangi kelimeye ait olduğunu gösterir | Hayır |
| Bitiş ekranı | Arka plan ışıması, yazıların belirmesi | 1,35 sn ve 3,5 sn | Bitişi kutlar | Hayır; düğmeler hemen basılabilir |
| Rozet kutlaması | Tam ekran, konfeti | 0,8 sn giriş, 2,4 sn konfeti | Kazanımı gösterir | Evet: kapatılana kadar ekranı örter |
| Quiz | Şık geri bildirimi, sonuç sayacı | kısa | Doğru/yanlışı gösterir | Hayır |

Değerlendirme: işi olmayan tek animasyon "Planın oluşturuluyor". "Söz ver"in 2 saniyelik beklemesi kısaltılabilir. Geri kalanların bir işi var; eksikleri "hareketi azalt" ayarını dinlememeleri.

## Önerilen iş listesi

| İş | Bulgu | Büyüklük |
|---|---|---|
| A. "Söz ver": parmak izini altta sabit tut | 4 | Küçük |
| B. Onboarding ilk ekranı: kapak yelpazesi küçük ekranda küçülsün | 5 | Küçük |
| C. Seçenek kartı: dar ekranda tek sütun, açıklama kesilmesin | 6, 7 | Orta (ortak bileşen, üç ekran) |
| D. Paywall fayda satırları iki satıra inebilsin | 8 | Küçük |
| E. Ana sayfa ilk okuma kartı: düğme ilk bakışta görünsün | 9 | Küçük |
| F. Dokunma hedefleri: görsel aynı kalır, basılabilir alan 48'e çıkar | 10 | Küçük |
| G. "Planın oluşturuluyor": süreyi kısalt ya da "Geç" ekle | 11 | Küçük (karar Don Normal ve Sean Büyüt ile) |
| H. "Hareketi azalt": onboarding hareketleri, konfeti ve kutlamada ayarı dinle | 12 | Orta |
| I. Küçük düzeltmeler: plan özeti, profil düzenleme, durum yazısı, "Sona göz attın" uyarısı | 13, 14, 15, 16 | Küçük |

Önerilen sıra: A, C, B, D, E, F, H, G, I.

## Yolda gördüklerim (arayüz dışı)

- Günün quizinin sonuç ekranında iki anlam yanlış ya da işe yaramaz: "in → olumsuzluk ön eki", "the → sadece bir tane olan isimlerden önce" (`b3_ios_yaygin_quiz_sonuc.jpg`). İçerik işi; Paul Ulus'un kelime anlamı listesine eklenmeli.
- Yeni son onboarding ekranı (kapaklı ilk hikâye) iki platformda ve iki koşulda doğru çiziliyor (`b3_ios_yaygin_son_ekran.jpg`).

## Yapamadıklarım

- Gerçek cihazda bakılmadı; hepsi emülatör ve simülatör.
- "Hareketi azalt" açıkken tur atılmadı; 12. bulgu koddan.
- Tam turda quizden sonra çıkan "İlk Quiz" rozet kutlaması profil, bildirim ayarları ve paywall karelerini örttü. Bu üç ekran okuma ve quiz olmadan giden ayrı bir kısa turla çekildi (`SADECE_HESAP`); yani bu ekranların okumuş kullanıcıdaki hali görülmedi.
- Simülatör mağaza fiyatlarını dolar gösteriyor; Türk lirası fiyatların sığması yalnız Android emülatöründe görüldü.
- Okuyucuda ses çalarken görüntü küçük iPhone turunda alınamadı (test oynat düğmesini bulamadı; uygulama çalıyordu).

Aşama 2 için hangi işlerin onaylandığını bekliyorum.
