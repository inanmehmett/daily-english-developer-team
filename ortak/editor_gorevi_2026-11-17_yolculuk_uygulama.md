# Editör görevi – yolculuk çekirdeği

**Tarih:** 17 Kasım 2026 · **Dayanak:** `raporlar/2026-11-17_tutma_ve_satis_plani.md`, `ortak/okuma_yolu_sistemi.md`, `ortak/okuma_yolu_sinirlari.md`, `raporlar/2026-11-17_ilk_uc_yolculuk_ve_kancalar.md`.
Önce ücretsiz sınır görevini bitir. Bu iş büyük: önce kısa bir uygulama planı yaz (`raporlar/` altına), sonra bölüm bölüm ilerle; her bölüm ayrı commit. Canlı veritabanına yazma yalnız Mehmet'in onayıyla ve yedekle. Sürüm kararı Mehmet'te.

## 1. Yolculuk tanımı ve açılma
- Yolculuk = sıralı metin listesi (başlangıç 4 durak + seviye yolculukları). Tanım veriyle tutulur (tablo ya da yapılandırma), kodda sabit değil.
- Kullanıcıya seviyesine (ve mümkünse ilgi alanına) göre yolculuk atanır; seviye belirleme zorunlu, kullanıcı yolculuk dışından da okuyabilir.
- Ücretsiz: ilk gün 2 durak açık, sonra yerel günde 1 (cihaz saati). Günlük ücretsiz hak tek: yolculukta ya da başka yerde harcanır. Her yolculuğun ilk 2 durağı ücretsiz, 3. ve sonrası Premium. Premium'da bekleme yok.
- Onboarding'deki ilk okuma alıştırması yolculuğun ilk adımı olarak işaretlenir.

## 2. Ekranlar
- **Ana sayfa ilk kartı:** "Senin yolculuğun · 2/4" + "Bugünün görevleri" (durak → kelime tekrarı → günün quizi), tek düğme "Sıradaki görev".
- **Bitiş ekranı = yolculuk ekranı:** biten durak işaretli küçük harita, sıradaki durağın adı ve `NextHook` cümlesi. Açıksa "Sıradaki durak"; ücretsizde kapalıysa "Yarın açılır" + ikincil "Premium'la şimdi oku". Geri sayım yok.
- **Başlangıç bitince:** ilerleme kartı (durak, kelime, gün — yalnız doğru sayılar) + "7 gün ücretsiz dene" (tetikleyici `starterComplete`).
- **3. durak kilidi:** tetikleyici `journeyLocked`.
- **Harita sayfası (`/career`):** rütbe adları kalkar; seviye ve duraklar.
- Ekranı kesen teklif günde en çok 1; şerit, profil, kilitli içerik sayılmaz.

## 3. Görev listesi, seri, bildirim
- Görevlerden biri tamamlanınca gün seriye sayılır; durak yoksa kelime tekrarı günü kurtarır.
- Bildirim günde en çok 2: okuma saatinde görev çağrısı ("Bugün 3 görevin var"), akşam yalnız gün tamamlanmadıysa "Bugün 1 durak kaldı". 11 türün bu ikisine eşlemesini tablo olarak raporla; geri kazanım haftada en çok 1; 09–21 dışı yok.

## 4. İçerik
- `NextHook` cümleleri: yedek al, Mehmet onayından sonra 32 satırı yaz (`raporlar/2026-11-17_ilk_uc_yolculuk_ve_kancalar.md`).

## 5. Ölçüm olayları
`journey_assigned`, `journey_stop_unlocked`, `journey_stop_started`, `journey_stop_completed`, `journey_next_tapped`, `daily_tasks_shown`, `daily_task_completed`, `offer_shown` (an), `offer_accepted`/`offer_dismissed`. Olayların cihazda düştüğü bir ekran görüntüsü ya da kayıt ile doğrula.

## 6. Mevcut kullanıcılar
Okudukları metinler yolculukta tamamlandı sayılır; kaldıkları yerden devam ederler.
