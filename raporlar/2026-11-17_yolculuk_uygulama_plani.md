# Sürüm 1 – ilk oturum: uygulama planı (güncellendi)

**Tarih:** 18 Kasım 2026 (ilk sürümü 17 Kasım). **Görev:** `ortak/editor_gorevi_2026-11-18_surum1_ilk_oturum.md`. **Dayanak:** `ortak/butun_plan.md`.
Bu plan, önceki "yolculuk çekirdeği" planının yerini alır. O planla yapılan işler korunur; durumları `raporlar/2026-11-18_yolculuk_uygulama.md`'de.

**Dallar:** sunucu ve Flutter'da `feat/journey-core`; zincir şöyle: `fix/paywall-trigger-attribution` → `feat/free-limits` → `feat/journey-core`. Her madde ayrı commit. Canlıya yazma ve yayın Mehmet'te.

## Maddeler: ne hazır, ne yapılacak

| # | Madde | Durum | Yapılacak |
|---|---|---|---|
| 1 | Yolculuk tanımı ve atama | **Hazır** (sunucu `2947cbf`, `235a739`, `cacd039`, `1df4e31`) | — |
| 2 | Onboarding sonu: "{ad}, yolculuğun hazır" + 4 durak; teklif (`onboarding`): "7 gün ücretsiz dene" + kaydırmadan görünen "Ücretsiz başla: günde bir durak"; kapatınca durak 1 | Kısmen: son ekran ilk hikâyeyi açıyor (`21fec0a6`), paywall ilk okumaya erteleniyor | Plan ekranı metni ve 4 durak; erteleme yerine onboarding sonu teklifi; teklif kapanınca durak 1 |
| 3 | Ana sayfa kartı: "Senin yolculuğun · 1/4 · Sıradaki: {ad}", tek düğme | Kart var, ama görev listesi de içinde (`9b1fd41c`) | Görev listesi Sürüm 3'e ait: kart sadeleşir, tek düğme "Sıradaki durak"; kelime ve quiz yuvası eski yerine döner |
| 4 | Bitiş ekranı: n/4, sıradaki ad + `NextHook` (boşsa açıklama); açıksa "Sıradaki durak"; kapalıysa "Sıradaki yarın açılır" + "Yarın hatırlat" (izin akışı) + "Premium'la şimdi oku" (`journeyNext`) | Kısmen (`bbe55037`) | Açıklama yedeği, "Yarın hatırlat" kapısı, tetikleyici adı `journeyWait` → `journeyNext` |
| 5 | Deneme/Premium başlayınca "Premium açıldı: yolculuğun bekliyor" → sıradaki durak | Yok | Satın alma başarı akışından sıradaki durağa |
| 6 | Paywall: yıllığın aylığa bölünmüşü, "7 gün ücretsiz, sonra {fiyat}/{dönem}; istediğin an iptal", gerçek sayılar, yanlış satırlar yok, SE 3 | Çoğu hazır (`a8acbb77`, `a4ab665f`) | Deneme satırı metni |
| 7 | Vazgeçince ikinci yol: paywall açık kalır; yıllık seçiliyse "Yıllık fazla mı geldi? Aylık planla başla" | Yok | İptal/hata sonrası satır ve aylığa geçiş |
| 8 | Ücretsiz sınırlar + başlangıç istisnası; sınır ekranı tetikleyicisi `limitReached` | Sınırlar hazır (sunucu `19d1482`, Flutter `a8acbb77`) | Başlangıç duraklarında dokunuş haktan düşmez (istemci metin kimliğini gönderir); tetikleyici `limitReached`, alt tür `limit_reached` olayında |
| 9 | Kilitli içerik: metnin adı; "Premium'la şimdi oku"; hak varsa "Bugünkü ücretsiz hakkımla aç" | Genel uyarı var | Ekran yeniden: ad + iki yol |
| 10 | Teklif sayısı: ilk oturumda en çok 2 (onboarding sonu, durak 2 bitişi), sonra günde 1 | Günde 1 tavanı var (`7d882b42`) | İlk oturum için 2 |
| 11 | Olaylar + cihazda kayıtla doğrulama | Çoğu var (`19909e5d`) | `journey_wait_shown`, `remind_tomorrow_tapped`, `purchase_downsell_shown/accepted`, onboarding anı; yerel sunucuyla cihazda doğrulama |
| 12 | 12 başlangıç durağı için Türkçe `NextHook` taslağı | Yok (seviye yolculuklarının 32 cümlesi için betik hazır, `f0988dc`) | Metinleri okuyup tablo; canlıya yazma yok |

## Sürüm 1 dışında kalan ama yapılmış işler
Aşağıdakiler yolculuk çekirdeği görevinde yapıldı, ama bütün planda Sürüm 2 ya da 3'e ait. Kod dalda duruyor; Sürüm 1 ile çıkıp çıkmayacağı Mehmet'in kararı:
- **Başlangıç bitince ilerleme kartı ve ana teklif** (Sürüm 2, `7d882b42`).
- **3. durak kilidi** (Sürüm 2, `bbe55037`).
- **Harita sayfası** (Sürüm 3, `ab7af6ce`).
- **Bildirim düzeni**, günde 2 (Sürüm 3, sunucu `c516c1b`, Flutter `595293bd`).

Görev listesi madde 3 ile karttan çıkıyor.

## Doğrulama
- Her madde: `flutter analyze` ve testler temiz, sunucu testleri temiz.
- Ekran görüntüleri: iPhone SE 3, normal ve en büyük yazı boyutunda (uygulamanın 1,3 tavanı).
- Cihazda olay doğrulaması için sunucu yerelde, **yerel veritabanına** bağlanarak çalıştırılır. Ayarlar değiştirilmezse yerel `dotnet run` canlı veritabanına bağlanıp migration'ı kendiliğinden uygular; bağlantı ayarı her çalıştırmadan önce kontrol edilir.
