# İlk analitik okuması: kullanıcı neden kalmıyor

> **DÜZELTME (15 Kas 2026, akşam):** Bu rapordaki Firebase sayıları uygulamanın kendi kayıtlarıyla uyuşmadı. Canlı veritabanına göre onboarding'i bitiren müşterilerin %81–85'i okumaya başlıyor (11–15 Kas: 34 kişiden 29; 29 Eki–10 Kas: 114 kişiden 92). "26 kişiden 18'i başlamadı" sayısı ve ona dayanan "en büyük kayıp onboarding ile ilk metin arasında" hipotezi **geçersizdir.** Bu rapordaki diğer Firebase sayıları da (okumayan 52 kişi, quize giriş, sonraki okumaya geçiş, paywall hunisi) aynı kaynaktan geldiği için doğrulanmış sayılmaz. Doğru sayılar: `raporlar/2026-11-15_editor_bolum1_ek.md`. Hata, tek ve yeni bir kaynağı (4 günlük Firebase verisi) uygulamanın kendi kayıtlarıyla karşılaştırmadan karara dayanak yapmaktı.


**Tarih:** 15 Kasım 2026 · **Kaynak:** Firebase Analytics olay listesi (veri 11 Kas'ta akmaya başladı; ~4 gün, 84 kullanıcı). Platform ayrımı net değil (listede yalnız Android'de üretilen `app_remove` var, yani büyük olasılıkla iki platform birlikte). Mehmet'in kendi test cihazları dahil olabilir. Tek geçiş.

## Sayılar (olay · kullanıcı)
| Adım | Olay | Kullanıcı |
|---|---|---|
| Aktif kullanıcı | – | 84 |
| Oturum (`session_start`) | 79 | 54 |
| İlk açılış (`first_open`) | 30 | 30 |
| Onboarding başladı / bitti | 33 / 27 | 27 / 26 |
| Okuma başladı (`reading_started`) | 77 | 32 |
| Okuma bitti (`reading_completed`) | 61 | 21 |
| Kelimeye bakma (`word_lookup`) | 1.063 | 28 |
| Cümle çevirisi (`sentence_translated`) | 265 | 13 |
| Sonraki okuma gösterildi / dokunuldu | 81 / 10 | 22 / 6 |
| Quiz tamamlandı / geçti | 35 / 26 | 12 / 11 |
| Paywall (`paywall_shown` / `paywall_impression`) | 23 / 79 | 20 / 14 |
| Satın alma başladı / tamamlandı | 3 / 2 | 3 / 1 |
| Bildirim alındı / açıldı (`push_opened`) | 41 / 2 | 26 / 2 |

## Okuma
- Onboarding sızdırmıyor: başlayan 27 kişiden 26'sı bitirdi.
- İçerik bitiriliyor: okumaya başlayan 32 kişiden 21'i en az bir metni bitirdi; başlatılan 77 okumanın 61'i tamamlandı.
- Ana özellik yoğun kullanılıyor: kelimeye bakan kişi başına ortalama 38 bakış.
- Asıl kopuş ilk oturumdan sonra: 54 kullanıcıya 79 oturum (kişi başı ~1,5). Metni bitiren 22 kişiye sonraki okuma gösterildi, 6'sı dokundu.
- 84 aktif kullanıcının 52'si hiç okumaya başlamadı (bunların kaçı yeni, kaçı eski kullanıcı bilinmiyor).
- Paywall'u 20 kişi gördü, 3'ü satın almayı başlattı, 1'i tamamladı.

## Hipotezler (hiçbiri ders değil; 4 günlük veri)
1. Sorun içerik kalitesinden çok geri dönüş nedeni eksikliği: kullanıcı bir metin okuyup çıkıyor, ertesi gün dönmesi için bir sebep/tetikleyici oluşmuyor.
2. Metin bittikten sonraki adım zayıf: sonraki okumaya geçiş oranı düşük (6/22).
3. Kişi başı 38 kelime bakışı iki şekilde okunabilir: özellik seviliyor ya da metinler seçilen seviyeye göre zor. Ayırmak için seviye bazında kırılım gerekir.

## Bilinmeyenler
- Ses dinleme: ilk 52 olayda sese ait bir olay görülmedi; ses kalitesi bu veriyle değerlendirilemez.
- Çeviri kalitesi: ölçen bir olay yok; yalnız kullanım sıklığı var.
- Mağaza yorumları bu turda okunmadı.

---

## Ek (15 Kas, aynı gece): okumayanlar kim, günün quizine girdiler mi

Kaynak: Google Analytics segment oluşturucu önizlemesi ("şunu yapan, ama `reading_started` hiç yapmayan kullanıcılar", kalıcı hariç tutma). Aynı ~4 günlük pencere.

| Grup | Toplam | Okumaya başlayan | Hiç başlamayan |
|---|---|---|---|
| Tüm kullanıcılar | 84 | 32 | 52 |
| Uygulamayı açan (`session_start`) | 54 | 23 | 31 |
| Yeni kullanıcı (`first_open`) | 30 | 9 | 21 |
| Onboarding'i bitiren | 26 | 8 | 18 |
| Paywall gören (`paywall_shown`) | 20 | 15 | 5 |
| Günün quizine ilk kez giren (`quiz_intro_shown`) | 9 | 8 | 1 |

- 52 okumayanın yaklaşık 21'i bu pencerede uygulamayı hiç açmadı (yalnız bildirim aldı); 31'i açtı ama okumadı. Bu 31 kişinin toplam 38 oturumu var (kişi başı ~1,2).
- Onboarding'i bitiren 26 kişinin 18'i ilk metne hiç başlamadı. Onboarding sonrası akış (kod): misafir hesap açılır, ana sayfaya düşer, paywall ilk okumaya kadar ertelenir. Yani bu kişileri paywall durdurmadı (okumayanlardan yalnız 5'i paywall gördü); ana sayfada kaldılar ve çıktılar.
- Okumayanlar quize de girmedi: günün quizine ilk kez giren 9 kişinin 8'i zaten okuyan kullanıcı.
- Ölçüm sınırı: günün quizine giriş yalnız ilk seferde (`quiz_intro_shown`) olay üretiyor; tekrar girişler ölçülmüyor. `quiz_completed`/`quiz_passed` okuma sonu quizine ait.
- 9 okuyan kullanıcıda `session_start` görünmüyor (küçük veri tutarsızlığı; neden bilinmiyor).

**Hipotez (1 veri noktası):** En büyük kayıp onboarding ile ilk metin arasında. Kullanıcı ana sayfaya bırakılıyor; ilk metni kendisinin başlatması gerekiyor ve çoğu başlatmıyor.

**Öneri (karar Mehmet'te):** Onboarding biter bitmez kullanıcı ana sayfa yerine doğrudan ilk metnin içine alınsın. Etkisi "onboarding'i bitirenlerin okumaya başlama oranı" ile ölçülür (şu an 8/26).

**Ölçüm isteği:** Günün quizine her girişte ve ses dinlemede olay gönderilsin.
