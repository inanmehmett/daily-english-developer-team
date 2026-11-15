# İlk analitik okuması: kullanıcı neden kalmıyor

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
