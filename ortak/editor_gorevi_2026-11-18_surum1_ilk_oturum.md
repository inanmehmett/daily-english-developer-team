# Editör görevi – Sürüm 1: ilk oturum (tut ve sat, tek akış)

**Tarih:** 18 Kasım 2026 · **Dayanak:** `ortak/butun_plan.md` (tek kaynak). Bu görev, `editor_gorevi_2026-11-18_satis_surumu.md` ile `editor_gorevi_2026-11-17_yolculuk_uygulama.md`'nin Sürüm 1 kısmını **birleştirir ve onların yerine geçer.** Yapılmış işler (V8 geri alma, tetikleyici, ücretsiz sınırlar) korunur.
Canlı veritabanına yazma ve yayın Mehmet'in onayıyla. Her madde ayrı commit; analyzer ve testler temiz; SE 3 + en büyük yazı boyutunda ekran görüntüsü.

Önce var olan uygulama planını (`raporlar/` altındaki yolculuk çekirdeği planı) bu kapsama göre güncelle, sonra sırayla:

1. **Yolculuk tanımı ve atama:** sıralı metin listesi veriyle tutulur; seviye (ve mümkünse ilgi alanı) ile atanır. Başlangıç 4 durak. Ücretsiz: ilk gün 2 durak açık, sonra yerel günde 1; Premium'da bekleme yok. Mevcut kullanıcıların okudukları tamamlanmış sayılır.
2. **Onboarding sonu:** "Planın hazır" ekranı "{ad}, yolculuğun hazır" olur ve 4 durağın adını gösterir. Ardından teklif (tetikleyici `onboarding`): ana düğme "7 gün ücretsiz dene", aynı ekranda kaydırmadan görünen "Ücretsiz başla: günde bir durak". Kapatınca doğrudan durak 1. Onboarding'e yeni soru/ekran eklenmez.
3. **Ana sayfa kartı:** "Senin yolculuğun · 1/4 · Sıradaki: {ad}", tek düğme.
4. **Bitiş ekranı:** ilerleme (n/4), sıradaki durağın adı ve `NextHook` cümlesi (boşsa açıklaması). Sıradaki açıksa tek ana düğme "Sıradaki durak". Kapalıysa "Sıradaki yarın açılır" + iki kapı: "Yarın hatırlat" (bildirim izni yoksa izin akışı burada) ve "Premium'la şimdi oku" (tetikleyici `journeyNext`). Geri sayım yok.
5. **Deneme/Premium başlayınca:** paywall kapanır kapanmaz "Premium açıldı: yolculuğun bekliyor" → sıradaki durak.
6. **Paywall:** yıllığın aylığa bölünmüş fiyatı; "7 gün ücretsiz, sonra {fiyat}/{dönem}; istediğin an iptal"; Premium'un açtıkları gerçek sayılarla; yanlış satırlar ("Günlük 3 okuma limiti") kalkar; SE 3'te seçili plan + düğme birlikte görünür.
7. **Vazgeçince ikinci yol:** iptal/hata sonrası paywall açık kalır; yıllık seçiliyse "Yıllık fazla mı geldi? Aylık planla başla". İndirim yok.
8. **Ücretsiz sınırlar:** yapılan işe başlangıç istisnasını ekle (başlangıç duraklarında dokunuş haktan düşmez). Sınır dolunca tek eylemli, dürüst ekran (tetikleyici `limitReached`).
9. **Kilitli içerik ekranı:** metnin adı; ana düğme "Premium'la şimdi oku"; günlük hak varsa ikincil "Bugünkü ücretsiz hakkımla aç".
10. **Teklif sayısı:** ilk oturumda ekranı kesen en çok iki (onboarding sonu, durak 2 bitişi); sonra günde bir.
11. **Olaylar:** `journey_assigned`, `journey_stop_started/completed`, `journey_next_tapped`, `journey_wait_shown`, `remind_tomorrow_tapped`, `offer_shown/accepted/dismissed` (an ile), `purchase_downsell_shown/accepted`, `limit_reached`. Cihazda düştüğünü kayıtla doğrula.
12. **Merak cümleleri:** 12 başlangıç durağı (A1, A2, B1) için metinleri okuyup birer Türkçe `NextHook` taslağı yaz (`raporlar/` altına tablo). Canlıya yazma; Paul inceleyecek, yazım Mehmet onayıyla.

Rapor: `raporlar/2026-11-1X_surum1_ilk_oturum.md` – madde madde ne yapıldı, ekran görüntüleri, olay adları, açık kalanlar.
