# Yolculuk çekirdeği: uygulama

**Tarih:** 18 Kasım 2026. **Görev:** `ortak/editor_gorevi_2026-11-17_yolculuk_uygulama.md`. **Plan:** `raporlar/2026-11-17_yolculuk_uygulama_plani.md`.
**Durum:** On bölümün hepsi kodlandı, testleri yazıldı ve her bölüm ayrı commit'lendi. **Dallar gönderilmedi; canlıya yazılmadı.** Sürüm, sunucu yayını ve `NextHook` yazımı Mehmet'in onayında.

| Depo | Dal | Taban |
|---|---|---|
| Sunucu | `feat/journey-core` | `feat/free-limits` (o da `master`'dan) |
| Flutter | `feat/journey-core` | `feat/free-limits` (o da `fix/paywall-trigger-attribution`'dan) |

Dallar zincirli: önce paywall tetikleyicisi, sonra ücretsiz sınırlar, sonra yolculuk birleşir.

## Bölümler ve commit'ler

| # | Bölüm | Sunucu | Flutter |
|---|---|---|---|
| 1 | Yolculuk verisi: `Journeys`, `JourneyStops`, `UserJourneys`; 3 başlangıç ve 3 seviye yolculuğu, metinlere slug ile bağlı | `2947cbf` | — |
| 2 | Kurallar ve API: atama, sıra, durak durumları, ortak günlük hak (ilk yerel gün 2, sonra 1), erişim kuralı, `GET /api/Journey`, `POST /api/Journey/stops/{id}/open` | `235a739`, `cacd039` | — |
| 3 | Ana sayfa ilk kartı: "Senin yolculuğun · 2/4" + bugünün görevleri (durak → kelime tekrarı → günün quizi), tek düğme "Sıradaki görev" | — | `9b1fd41c` |
| 4 | Bitiş ekranı = yolculuk ekranı: küçük harita, sıradaki durak ve cümlesi. "Sıradaki durak" / "Yarın açılır" + "Premium'la şimdi oku" (`journeyWait`) / 3. durakta "Premium'la devam et" (`journeyLocked`) | — | `bbe55037` |
| 5 | Başlangıç bitince: ilerleme kartı (durak, kelime, gün; yalnız gerçek sayılar) + deneme (`starterComplete`). Ekranı kesen teklif günde en çok 1. | `1df4e31` | `7d882b42` |
| 6 | Harita (`/career`): rütbe adı yok; seviye, yolculuk, duraklar | — | `ab7af6ce` |
| 7 | Onboarding'deki ilk okuma = başlangıç yolculuğunun 1. durağı | — | `21fec0a6` |
| 8 | Bildirim: günde en çok 2, eşleme tablosu aşağıda | `c516c1b` | `595293bd` |
| 9 | Ölçüm olayları | (sunucu olayları 2. bölümde) | `19909e5d` |
| 10 | `NextHook`: yedekli yazma ve geri alma betiği, **çalıştırılmadı** | `f0988dc` | — |

## Kurallar kodda nasıl karşılandı

- **Tek kaynak.** Ücretsiz erişim `FreeUnlockService`'te, yolculuk `JourneyService`'te. İstemci kuralı tekrar etmiyor, sunucunun verdiği durumu gösteriyor.
- **Günlük hak.** Hesabın ilk yerel gününde 2 açma, sonra günde 1; yolculuk durağı ve havuz metni aynı haktan düşer. Gün, profildeki saat dilimine göre (cihaz saati). Her zaman açık metin de yolculuk içinde açılınca hak harcar; yoksa "ilk gün 2" kuralı delinirdi. Kütüphaneden açılan her zaman açık metin hak harcamaz.
- **Ücretsiz duraklar.** Başlangıç yolculuğunun 4 durağının hepsi, seviye yolculuklarının ilk 2 durağı. Okuma, quiz, dizi ve yetki uçları açılmış ücretsiz durakları aynı kuralla kabul ediyor. Bugüne kadar yalnız havuz metinleri kabul ediliyordu; New in Town'ın ilk iki bölümü açılsa da kilitli kalırdı.
- **Atama.** Yolculuk seviyeye göre atanıyor. Bir yolculuk bitince sıradaki atanıyor. Mevcut kullanıcının bitirdiği metinler tamamlanmış durak sayılıyor ve kullanıcı kaldığı yerden devam ediyor.
- **Teklif tavanı.** Okuma sonrası teklif penceresi ve başlangıç teklifi, tam ekran paywall ile aynı günlük tavanı (oturumda 1, günde 1) paylaşıyor. Şerit, profil ve kilitli içerik sayılmıyor. Tavan doluysa başlangıç teklifi sessiz bir bağlantı olarak kalıyor.
- **Deneme süresi.** Yalnız bilindiği yerde yazılıyor: iOS'ta "7 gün ücretsiz dene". Android'de mağaza okunmadan süre bilinmediği için "Bütün yolculukları aç" yazıyor.
- **Seri.** Görevlerden biri bitince gün seriye sayılıyor ve bu zaten öyleydi; doğrulandı. Okuma olayları, kelime çalışma oturumu (`session/{id}/complete`) ve günün quizi (`/api/quiz/complete`) seriyi işliyor. Durak açılmadığı gün kelime tekrarı günü kurtarıyor.

## Bildirim eşlemesi (bölüm 8)

Günde en çok iki bildirim: her yuvadan bir tane. Bir turda kullanıcıya tek bildirim gider. Sessiz saat 09:00–21:59 (eskiden 09:00–22:59).

| Tür | Yuva | Kural |
|---|---|---|
| DailyReminder (okuma / durak) | Gün | Okuma saatinde. Başka görevle aynı güne düşerse birleşir. |
| VocabReview (kelime tekrarı) | Gün | Aynı |
| DailyQuiz (günün quizi) | Gün | Aynı |
| **DailyTasks** (yeni) | Gün | İki ya da üç görev aynı güne düşünce: "Bugün 3 görevin var: durak, 6 kelime, quiz." Dokununca ana sayfa açılıyor. |
| TrialEnding (deneme bitiyor) | Gün | İşlemsel; önceliği görevlerden yüksek |
| NewContent (yeni içerik) | Gün | Zaten 7 günde bir |
| Activation (hiç okumamış yeni hesap) | Gün | Geri kazanım: haftada en çok 1 |
| WinBack (uzun süre gelmeyen) | Gün | Geri kazanım: haftada en çok 1 |
| Streak (3+ gün seri, bugün okumadı) | Akşam | Yalnız gün tamamlanmadıysa; metin "Bugün 1 durak kaldı; okursan N. gün olur." |
| StreakStart (1–2 gün seri) | Akşam | Aynı koşul; metin "Bugün 1 durak kaldı." |
| StreakRepair (seri kırıldı, telafi açık) | Akşam | Akşam yuvasını kullanır; telafi penceresi sınırlı olduğu için gün içinde de gidebilir |
| Promotion, DailyUnlock | — | Bu turda üreticisi yok, gönderilmiyor |

Metin sürümü `copy_v3` oldu; açılma oranı eski metinlerle bu alanla karşılaştırılır.

## Ölçüm olayları

| Olay | Nerede |
|---|---|
| `journey_assigned` | Sunucu: yolculuk atanınca (ilk atama ya da sıradaki) |
| `journey_stop_unlocked` | Sunucu: durak günlük hakla açılınca |
| `journey_stop_started` | Ana sayfa, harita, bitiş ekranı ya da onboarding'den okuyucu açılınca (`source`) |
| `journey_stop_completed` | Bitiş ekranı bir durak için açılınca |
| `journey_next_tapped` | "Sıradaki görev" düğmesine basılınca (`task`) |
| `daily_tasks_shown` | Görev listesi gün içinde ilk kez gösterilince |
| `daily_task_completed` | Gösterilmiş bir görev aynı gün tamamlanınca |
| `offer_shown` / `offer_accepted` / `offer_dismissed` | Bitiş ekranındaki üç an: `starter_complete`, `journey_locked`, `journey_wait` (`moment`) |

## Testler

- **Sunucu (gerçek Postgres):**
  - tohum,
  - atama,
  - ilk gün 2 / sonra 1,
  - havuzla ortak hak,
  - sıra,
  - 3. durakta Premium,
  - mevcut kullanıcının sıradaki yolculuğa geçmesi,
  - B2'ye B1 yolu,
  - bugün biten durak ve okunan gün sayısı,
  - bildirim yuvaları ve birleştirme,
  - hesap silmede `UserJourneys`.
- **Flutter:**
  - model ayrıştırma,
  - görev sırası,
  - sıradaki durağın tahmini (hak var, hak yok, Premium, son durak),
  - başlangıç teklif anı,
  - harita sayfası (seviye, durumlar, rütbe adı yok),
  - bildirimden ana sayfaya yönlendirme.
  - `flutter analyze` temiz; tam test takımı geçti.
- **Görülmedi:** Ekranlar cihazda ya da simülatörde görülmedi. Olayların cihazdan düştüğü de bir kayıtla doğrulanmadı. Bunun için `/api/Journey` sunan bir sunucu gerekiyor. Yerel `dotnet run`, ayarlar değiştirilmezse canlı veritabanına bağlanıp migration'ı kendiliğinden uygulayan bir yapı; bu yüzden denenmedi. Görevin istediği "cihazda olay kaydı" doğrulaması açık iş.

## Açık noktalar ve kararlar (Mehmet ve ekip)

1. **Yayın sırası:**
   1. Sunucu dalları `master`'a birleşir. Yolculuk tabloları migration ile gelir ve tohum canlıdaki metinlere slug ile bağlanır.
   2. `NextHook` betiği onayla çalıştırılır (`MigrationScripts/SetJourneyNextHooks_2026_11_18.sql`; geri alma betiği yanında). Betik yerel kopyada denendi: 32 metin yazıldı, 32 satır yedeklendi, ikinci çalıştırma güvenli, geri alma eski hâli getiriyor.
   3. Flutter dalları birleşir; sonra 1.0.4 derlenir.
2. **Cihazda doğrulama:** `/api/Journey`'i yerel veritabanına bağlı bir sunucuyla görmek ya da bir test ortamı açmak gerekiyor. Ekranlar ve olaylar cihazda görülmeden yayın önerilmez.
3. **Kutlamalar hâlâ rütbe adı gösteriyor.** Karar yalnız `/career` için verildi; rütbe atlama kutlamasının dili ayrı karar.
4. **İlgi alanı:** Seçim kodu ilgi alanını destekliyor, ama bugün her seviyede tek yolculuk var; etkisi yok.
5. **B2 ve üstü:** Geçici kural olarak B1 başlangıcı, sonra Dünya Şehirleri atanıyor. İçerik kararı ekipte.
6. **"Sıradaki" cümleleri:** Canlıdaki gövdelerle birebir karşılaştırılmadı (kaynak raporundaki uyarı). Yazmadan önce bir okuma yapılmalı.
7. **Plan ekranı:** Onboarding'deki plan ekranı haftada 14–42 kelime hedefi gösteriyor; ücretsiz defter 15'te duruyor (ücretsiz sınır raporunda da not edildi).
