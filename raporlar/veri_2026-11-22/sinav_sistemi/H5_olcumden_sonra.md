# H5 – Ölçümden sonra ne oldu

**Kaynak:** canlı veritabanı, 22 Kasım 2026, salt okuma. Yalnız müşteri hesapları. "Seviyeni yeniden ölç" ile seviyesi yazılan 105 kayıt; her biri için sonraki 7 günde **başlanan** metinler (`ReadingProgresses.StartedAt`).

| Ölçümün sonucu | Kişi | Sonraki 7 günde okuyan | Başlanan metin | Biten | Yeni seviyenin **altında** | Yeni seviyede | Yeni seviyenin **üstünde** |
|---|---|---|---|---|---|---|---|
| Seviye yükseldi | 65 | 48 | 120 | 99 (%83) | 61 | 39 | 20 |
| Aynı kaldı | 28 | 18 | 37 | 28 (%76) | 6 | 25 | 6 |
| **Seviye düştü** | 12 | 11 | 25 | 19 (%76) | 5 | 5 | **15** |

## Okuma
- **Seviye değişince okunan metin pek değişmiyor.** Seviyesi yükselen 65 kişinin başladığı 120 metnin yarısı (61) yeni seviyesinin altında; seviyesi düşen 12 kişinin 25 metninin 15'i yeni seviyesinin üstünde.
- **Olası neden (hipotez, kişi kişi doğrulanmadı):** müşterilerin kullandığı sürümde ücretsiz okurun açabildiği metinler az ve sabit: üç başlangıç metni (ikisi A1, biri A2) ve günde bir ücretsiz açma. Seviye ne çıkarsa çıksın ilk okunanlar büyük ölçüde aynı metinler. Yolculuk bu veriyi açıklamaz: yolculuk kartı 1.0.4 ile geliyor ve bugün yalnız 1 müşteride yolculuk var.
- **1.0.4 için uyarı (koddan):** yolculuk kullanıcıya ilk açılışta, o günkü seviyesine göre atanıyor ve seviye sonradan değişince **yeniden atanmıyor** (`JourneyService.CurrentJourneyAsync`). Ana sayfanın ilk kartı yolculuk olacağı için, ölçümle seviyesi değişen kullanıcı eski seviyenin hikâyelerini görmeye devam eder.
- **"Önceki seviye" çoğu kayıtta gerçek değil.** 105 kaydın 86'sında önceki seviye A1: ölçüm onboarding'de, kullanıcı seviye seçmeden önce yapıldığında profilde varsayılan A1 duruyor. "Yükseldi" grubunun büyük kısmı aslında ilk ölçüm.
- **Bitirme oranı** üç grupta da %76–83; seviyesi düşenlerde düşük değil. Sayılar küçük (12 kişi), hipotez düzeyinde.
- Ekip notunda "seviyesi düşen 4 müşteri" yazıyordu; kayıtta **12** düşüş var (3'ü A1 → Pre-A1, 5'i B1 → A2, 2'si A2 → A1, 2'si B2'den).

## Bilinmeyen
- **100 kelimede dokunma: ölçülemedi.** Müşterilerin kullandığı sürümlerde kelimeye bakma olayı metnin kimliğini taşımıyor; bakışı metne bağlayamıyorum. 1.0.4 yayınlanınca ölçülebilir.
- Okunan metinlerin kullanıcıya nereden geldiği (yolculuk kartı mı, raf mı) bu sorguda ayrılmadı.
