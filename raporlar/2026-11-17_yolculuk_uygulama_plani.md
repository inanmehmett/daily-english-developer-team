# Yolculuk çekirdeği – uygulama planı

**Tarih:** 17 Kasım 2026. **Görev:** `ortak/editor_gorevi_2026-11-17_yolculuk_uygulama.md`.
**Dallar:** sunucu ve Flutter'da `feat/journey-core`; ikisi de `feat/free-limits` dalının üstünde, çünkü günlük hak ve sınır sayfaları ona dayanıyor. Her bölüm ayrı commit. Canlıya yazma yok; sürüm Mehmet'te.

## Koddan bilinen (planın dayandığı)
- **Ücretsiz erişim** `FreeUnlockService` üzerinden işliyor:
  - 3 metin her zaman açık.
  - Havuzdan günde 1 açma yapılabiliyor; açılan metin kalıcı.
  - Gün, profildeki saat dilimine göre hesaplanıyor (`TimeZoneOffsetMinutes`). "Cihazın yerel günü" kuralı zaten bu yolla uygulanıyor.
- **Seri** okuma, quiz ve kelime çalışmasıyla sayılıyor (`StreakGateway.RecordActivityAsync`). "Kelime tekrarı günü kurtarır" kuralı büyük olasılıkla hazır; doğrulanacak.
- **Metin kimlikleri** yerel ve canlı veritabanında farklı. Yolculuk tanımı metinlere `Slug` ile bağlanır, kimlikle değil.
- **`NextHook`** canlıda 287 metnin hepsinde boş.

## Kurallar (tek yorum)
| Kural | Uygulama |
|---|---|
| Günlük ücretsiz hak | Hesabın ilk yerel gününde 2 açma, sonra günde 1. Hak tek: yolculuk durağı da havuz metni de aynı haktan düşer (`FreeTextUnlocks`). |
| Durak açmak | Ücretsiz kullanıcı bir durağı açınca `FreeTextUnlocks`'a satır düşer. Her zaman açık metinler de yolculuk içinde açılınca hak harcar; böylece "ilk gün 2, sonra günde 1" yolculukta gerçekten uygulanır. Kütüphaneden açılan her zaman açık metin hak harcamaz. |
| Ücretsiz duraklar | Başlangıç yolculuğunun 4 durağının hepsi; seviye yolculuklarında ilk 2 durak. 3. ve sonrası Premium. |
| Sıra | Bir durak, öncekisi bitmeden açılmaz. Premium'da sıra var, bekleme yok. |
| Erişim | `CanAccessReadingTextAsync`: her zaman açık **ya da** (açılmış **ve** (havuz metni **ya da** ücretsiz yolculuk durağı)). |
| Atama | Yolculuk, profildeki seviyeye göre atanır. Önce başlangıç yolculuğu; o bitince seviye yolculuğu; o bitince sıradaki (`NextJourney`). İlgi alanına göre tanımlı bir yolculuk varsa o seçilir; bugün yok (aşağıya bkz.). |
| Mevcut kullanıcılar | Biten metinler (`ReadingProgresses.IsCompleted`) yolculukta tamamlanmış sayılır; ilk bitmemiş duraktan devam edilir. |

## Bölümler ve commit sırası
| # | Bölüm | Sunucu | Flutter | Doğrulama |
|---|---|---|---|---|
| 1 | **Yolculuk verisi** | `Journeys`, `JourneyStops`, `UserJourneys` tabloları. Migration, 3 başlangıç ve 3 seviye yolculuğunu slug ile tohumlar (eksik metin atlanır). | — | Migration testi (gerçek Postgres), tohum sayıları |
| 2 | **Kurallar ve API** | `JourneyService`: atama, durak durumları (bitti / açık / yarın / Premium), açma. `FreeUnlockService`'te ilk gün 2 hak ve yolculuk durakları; erişim kuralı. `GET /api/journey`, `POST /api/journey/stops/{id}/open`. Sunucu olayları: `journey_assigned`, `journey_stop_unlocked`. | — | Birim testleri: ilk gün 2, ertesi gün 1, ortak hak, sıra, 3. durak Premium, mevcut kullanıcı |
| 3 | **Ana sayfa kartı** | — | İlk kart: "Senin yolculuğun · 2/4" + "Bugünün görevleri" (durak → kelime tekrarı → günün quizi), tek düğme "Sıradaki görev". | Widget testi, simülatör görüntüsü |
| 4 | **Bitiş = yolculuk ekranı** | Bitiş verisine sıradaki durak ve `NextHook` | Küçük harita (biten durak işaretli), sıradaki durak ve cümlesi. Açıksa "Sıradaki durak"; kapalıysa "Yarın açılır" + "Premium'la şimdi oku". 3. durak kilidi `journeyLocked`. | Widget testi, görüntü |
| 5 | **Başlangıç bitince** | Gerçek sayılar: durak, kelime, gün | İlerleme kartı + "7 gün ücretsiz dene" (`starterComplete`). Ekranı kesen teklif günde en çok 1 (şerit, profil ve kilit sayılmaz). | Test |
| 6 | **Harita sayfası** | — | `/career`: rütbe adları kalkar; seviye ve duraklar görünür. | Görüntü |
| 7 | **Onboarding bağı** | — | Onboarding'deki ilk okuma, başlangıç yolculuğunun 1. durağı olur (aynı metin, aynı sıra). | Test |
| 8 | **Görevler, seri, bildirim** | Bildirim günde en çok 2: okuma saatinde görev çağrısı, akşam yalnız gün tamamlanmadıysa. 11 türün eşlemesi; geri kazanım haftada en çok 1; 09–21. | Görev bitince gün seriye sayılır (doğrulama). | Birim testleri + eşleme tablosu |
| 9 | **Ölçüm** | — | `journey_stop_started`, `journey_stop_completed`, `journey_next_tapped`, `daily_tasks_shown`, `daily_task_completed`, `offer_shown`, `offer_accepted` / `offer_dismissed` | Cihazda olay kaydı ya da görüntü |
| 10 | **İçerik (`NextHook`)** | Yedek betiği + 32 satırlık, slug'a dayalı yazma betiği. **Çalıştırılmaz**; Mehmet'in onayı ve yedekle. | — | Yerel veritabanında deneme |

1–2 sunucu çekirdeğidir; 3–9 onun üstüne kurulur. Her bölüm biter bitmez testleriyle commit'lenir; ara durum `raporlar/` altında not edilir.

## Bilinçli sınırlar ve açık noktalar
- **İlgi alanı:** bugün her seviyede tek yolculuk var. Seçim mantığı ilgi alanını destekleyecek biçimde yazılır; içerik gelene kadar etkisi yoktur. Plan ekranındaki "ilgi alanına göre" ifadesi o zamana kadar tam doğru değil.
- **B2 ve üstü:** başlangıç yolculuğu tanımsız. Geçici kural: B2+ kullanıcıya B1 başlangıcı, sonra Dünya şehirleri. İçerik kararı ekipte.
- **A1 ikinci yolculuk:** New in Town'dan sonra Coffee Shop (A2).
- **Seviye zorunluluğu:** onboarding'deki ölçümün zorunlu olması bu görevin kapsamında değil; seviye yoksa onboarding'de seçilen seviye kullanılır.
- **Bildirim yayını:** sunucu kodu yazılır, test edilir; canlıya çıkışı sunucu yayınıyla, Mehmet'in kararıyla.
