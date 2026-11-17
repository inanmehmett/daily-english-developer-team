# "Okuma Yolculuğun" sayfası – canlı veri okuması

**Rol:** Nate Gümüş (veri), itirazlar Nassim Talip. **Tarih:** 17 Kasım 2026.
**Görev:** `ortak/editor_gorevi_2026-11-17_okuma_yolculugu.md`. Yalnız okuma yapıldı. Bağlantı `default_transaction_read_only = on` ile açıldı ve canlıda hiçbir satır değişmedi.

## En üstte beş satır

1. **Sayfayı kaç kişi görüyor:** 243 müşteriden 25'i (%10), toplam 36 açılış. Sayfayı kendi isteğiyle (kutlama dışında) açan 14 kişi var. Ana sayfadaki yolculuk şeridinden (`target_card`) gelen açılış hiç yok.
2. **Kendiliğinden geri dönen var mı:** çok az. Kendi isteğiyle iki ya da daha çok kez açan 4 kişi var, farklı iki günde açan 3 kişi. Açanların 18'i sayfayı yalnız bir kez açmış.
3. **Okumaya yöneltiyor mu:** belirgin bir fark yok. Açılışların 22/36'sında (%61) sonraki 10 dakikada okuma olayı geliyor. Kayıt gününden sonraki uygulama açılışlarında bu oran 118/194 (%61); aynı kişilerin açılışlarında 64/91 (%70).
4. **Dönüşle ilişkisi:** aynı etkinlik düzeyinde ilişki görünmüyor; sayılar da çok küçük. İlk gün en az bir metin bitirenlerde, o gün sayfayı açanların D1'i 3/10, açmayanların 17/54. Fark yok denecek kadar az ve iki grup da az veri.
5. **Gelir katkısı:** sıfır. `level_journey` şeridi 7 kişiye 10 kez gösterildi. Bunlardan sonra 1 paywall açıldı, satın almaya basan olmadı. `journey_chest` hiç gösterilmedi (0). Sayfayı açan tek abone, satın almayı 29 saat sonra başka bir yüzeyden (`highEngagement` şeridi) yaptı.

## Yöntem

- **Kimler:** `Users.AccountKind = 'customer'`, 243 hesap (154 iOS, 89 Android). Kayıt tarihleri 29 Ekim – 17 Kasım. Kayıt anı için `UserProfiles.CreatedAt` kullanıldı.
- **Gün:** UTC+3 takvim günü. "N. gün döndü": kayıt gününden N gün sonraki takvim gününde `UserEvents`'te hata dışında en az bir olay olması. D1 için 16 Kasım ve öncesinde kaydolanlar, D7 için 9 Kasım ve öncesinde kaydolanlar sayıldı.
- **Açılış:** `screen_view` olayında `screen_name = career_journey`. Bütün müşteri sürümleri bu olayı yazıyor; ilgili kayıt kodu 9–10 Eylül'den beri var.
- **Sayfa içi olaylar:** `career_node_tap`, `level_up_map_opened`, `level_journey` ve `journey_chest` gösterimleri. "Sonraki olay" hesaplanırken bunlar sayfanın kendi olayı sayıldı ve atlandı.
- **Okuma olayı:** `reading_started`, `reading_active`, `reading_completed`, `sentence_listened`, `word_lookup`, `sentence_translated`, ayrıca raftan metin açma (`shelf_item_opened`, `next_reading_tapped`).
- **Nasıl çalıştı:** Müşteri satırları (e-posta ve ad olmadan) `Users`, `UserProfiles`, `UserEvents`, `PaywallAnalyticsEvents` ve `Subscriptions` tablolarından yerel bir çalışma veritabanına kopyalandı. Sorgular orada koştu. Kopya iş bitince silindi.

## S1. Erişim

| | Değer |
|---|---|
| Sayfayı en az bir kez açan müşteri | 25/243 (%10) |
| iOS / Android | 19/154 / 6/89 |
| Toplam açılış | 36 |
| İlk açılış kayıt gününde | 13/25 |
| İlk açılış ertesi gün | 7/25 |
| İlk açılış 2. gün ya da sonra | 5/25 |

| Kişi başı açılış | Kişi |
|---|---|
| 1 | 18 |
| 2–3 | 6 |
| 4+ | 1 |

| Kaynak | Açılış | Kişi |
|---|---|---|
| Rütbe kutlaması (`celebration`) | 17 | 16 |
| Profil sayfası (`profile_page`) | 11 | 10 |
| Ana sayfa kişi kartı (`profile_card`) | 8 | 6 |
| Ana sayfa yolculuk şeridi (`target_card`) | 0 | 0 |

Okuma: açılışların neredeyse yarısı kutlamadaki "Yolculuğunu gör" düğmesinden geliyor. Yolculuk şeridinden hiç açılış olmaması koddaki bir koşulla tutarlı: Flutter `d5e4343`'te şerit, ana sayfada yalnız ilk haftadan sonra ve günlük iş ile seviye ölçümü kartı yoksa yedek olarak çiziliyor (`home_page.dart:1125-1156`). Kayıtların en eskisi 18 günlük; şeridi görecek kadar eski ve hâlâ etkin müşteri çok az. Yani "şerit kimseyi getirmiyor" demek için erken; şerit büyük olasılıkla neredeyse kimseye gösterilmedi. **Hipotez.**

## S2. Kendiliğinden mi geliyor

| | Değer |
|---|---|
| Kutlama dışı açılışların payı | 19/36 (%53) |
| Kutlama dışında en az bir kez açan kişi | 14 |
| Yalnız kutlamadan açan kişi | 11 |
| Kutlama dışında 2 ya da daha çok kez açan kişi | 4 |
| Kutlama dışında farklı 2 günde açan kişi | 3 |
| Kutlamadan sonra sayfaya kendi isteğiyle dönen açılış | 6 |

Okuma: kendi isteğiyle açan 14 kişinin 10'u bir kez açıp bırakmış. Sayfaya düzenli bakan bir grup yok; olsa bile 3 kişi (az veri). **Hipotez.**

## S3. Sayfada ne yapılıyor

| | Değer |
|---|---|
| `career_node_tap` | 19 dokunuş, 11 kişi |
| Dokunulan düğüm: kilitli / şu anki | 14 / 5 |
| En az bir düğüme dokunulan açılış | 16/36 |
| Sayfada kalma (sonraki olaya kadar, ortanca) | 33 sn (çeyrekler 13–58 sn, 24 açılış) |

Okuma: açılışların yarıya yakınında bir düğüme dokunuluyor; dokunulan düğümlerin çoğu kilitli, yani sıradaki rütbe merak ediliyor. Kalma süresi kısa. 12 açılıştan sonra 10 dakika içinde hiç olay yok; bu açılışlar ölçüme girmedi, kalma süresi onlar için bilinmiyor. **Hipotez.**

## S4. Sonrasında ne oluyor

Sayfadan sonraki 10 dakikadaki ilk olay:

| İlk olay | Açılış | Bunlardan kutlamadan |
|---|---|---|
| Okuma | 14 | 6 |
| 10 dakikada olay yok (çıkış) | 12 | 6 |
| Paywall (sayfa dışı) | 4 | 2 |
| Metin quiz girişi | 3 | 2 |
| Sıradaki okuma kartı gösterimi | 2 | 1 |
| İpucu gösterimi | 1 | 0 |

Sonraki 10 dakikada okuma olayı gelme oranı, karşılaştırma gruplarıyla:

| Ani | 10 dk içinde okuma |
|---|---|
| Okuma Yolculuğu açılışı | 22/36 (%61) |
| Kayıt gününden sonraki her uygulama açılışı (`app_open`) | 118/194 (%61) |
| Aynı 25 kişinin kayıt günü sonraki açılışları | 64/91 (%70) |

Okuma: sayfa açılışından sonra okumaya geçme oranı, sıradan bir uygulama açılışından sonrakiyle aynı. Sayfayı açanların kendi açılışlarından ise biraz düşük. Ana sayfaya dönüş anı ayrıca kaydedilmiyor (ana sayfa için `screen_view` yok); karşılaştırma bu yüzden uygulama açılışıyla yapıldı. Sayfanın okumaya ek bir yöneltmesi görünmüyor. **Hipotez.**

## S5. Dönüşle ilişkisi

Ham karşılaştırma (yanıltıcı; yalnız bağlam için):

| Kayıt gününde sayfayı | D1 | D7 |
|---|---|---|
| Açtı | 3/11 (az veri) | 0/5 (az veri) |
| Açmadı | 39/201 | 3/133 |

Aynı etkinlik düzeyinde (yalnız kayıt gününde en az bir metin bitirenler):

| Kayıt gününde | Sayfayı açtı | Açmadı |
|---|---|---|
| ≥1 metin bitirdi, D1 | 3/10 (az veri) | 17/54 |
| ≥1 metin bitirdi, D7 | 0/4 (az veri) | 2/35 |
| Tam 1 metin bitirdi, D1 | 1/3 (az veri) | 5/30 |
| 2+ metin bitirdi, D1 | 2/7 (az veri) | 12/24 |
| Kendi isteğiyle açtı (kutlama dışı), D1 | 2/8 (az veri) | 18/56 |

Okuma: kayıt gününde sayfayı açan 13 kişinin 12'si o gün en az bir metin bitirmişti. Aynı düzeydeki okurlarla karşılaştırınca sayfayı açanlar daha çok dönmüyor; 2+ metin bitirenlerde açanlar daha az dönüyor, ama 7 kişilik bir grupla hüküm verilmez. Sayfanın dönüşle olumlu bir bağıntısı görünmüyor. **Hipotez.**

## S6. Kutlama sonrası harita

| | Değer |
|---|---|
| `level_up_map_opened` | 16 kişi, 16 kez (her biri bir kez) |
| Kutlamadan hemen önceki olay | `reading_completed` 11, `reading_active` 2, diğer 3 |
| Haritadan sonraki 30 dk içinde yeni metin başlatan | 8/16 (az veri) |
| Haritadan sonraki 30 dk içinde metin bitiren | 5/16 (az veri) |
| En az 200 XP'si olan (ilk rütbeyi geçmiş) müşteri | 40 |
| Bunlardan haritayı hiç açmayan | 21 |

Kaba vekil (doğrudan karşılaştırma değil): 200+ XP'li müşterilerde bir metni bitirdikten sonraki 30 dakikada yeni metin başlatma oranı, haritayı kutlamadan açmış olanlarda 72/120 (%60), hiç açmamış olanlarda 32/75 (%43).

Okuma: kutlamanın kendisi kaydedilmiyor (`BadgeCelebration` olay yazmıyor). Bu yüzden "kutlama gösterildi, harita açılmadı" anları ayrı ayrı sayılamıyor; tam karşılaştırma yapılamaz. Vekil sayı kişi düzeyinde bir seçim farkını gösteriyor: haritaya basanlar zaten daha çok okuyan kişiler. Bu, haritanın etkisi değildir. Haritadan sonraki aynı oturumda okuma başlatan 0 kişi var, ama `SessionId` metin başlarken değişiyor olabilir; bu sayı güvenilir değil ve tabloya alınmadı. **Hipotez.**

## S7. Gelir yüzeyi

| Yüzey | Gösterim | Kişi | 3 dk içinde paywall açılışı | Satın almaya basma | Tamamlama |
|---|---|---|---|---|---|
| `level_journey` (şerit) | 10 | 7 | 1 | 0 | 0 |
| `journey_chest` (kampanya sandığı) | 0 | 0 | – | – | – |

Bağlam (aynı dönemde bütün müşteriler): paywall'u 87 kişi gördü, 14 kişi satın almaya bastı, 4 abonelik var. Sayfayı açan tek abone, satın almayı ilk açılışından 29 saat sonra `highEngagement` şeridinden yaptı.

Okuma: şeridin tıklaması kendi tetikleyicisiyle kaydedilmiyor; paywall `manual` olarak açılıyor. Bu yüzden şeridin paywall'u, gösterimden sonraki 3 dakikada aynı kişide açılan paywall olarak eşlendi. Sandık yalnız etkin bir kampanya varken çiziliyor ve bu dönemde hiçbir müşteriye çizilmedi. Sayfanın gelir katkısı ölçülebilir düzeyde değil. **Hipotez.**

## İtirazlar (Nassim Talip)

- **Seçim yanlılığı her tabloda var.** Sayfayı açanların 12/13'ü o gün metin bitirmiş, kutlamadan gelenler tanım gereği 200 XP'yi geçmiş okurlar. Okumaya geçiş ve dönüş sayılarının hiçbiri sayfanın etkisi olarak okunamaz. Aynı düzeyde karşılaştırınca da olumlu bir fark çıkmıyor; bu "etkisi yok" demek değil, "bu veriyle görünmüyor" demek.
- **Sayılar çok küçük.** 25 açan, 13'ü ilk gün. D1 ve D7 hücrelerinin hepsi 20'nin altında. Tek bir kişinin dönmesi oranı 10 puan oynatır.
- **Yolculuk şeridi sınanmadı.** Şerit ilk haftadan sonra ve başka kart yoksa çiziliyor; 18 günlük bir kitlede neredeyse kimse o koşula girmedi. "Şerit açılış getirmiyor" sonucu çıkarılamaz.
- **Kutlama kaydı yok.** Kutlama kaç kez gösterildi, bilinmiyor. "Kutlamaların kaçı haritaya gitti" oranı ancak 200+ XP'li 40 kişiyle kabaca tahmin edilebilir (16/40). Bu da bir rütbeyi geçen herkese kutlama gösterildiği varsayımına dayanıyor.
- **Ölçüm alt sınır.** 16 Kasım raporunda görüldüğü gibi olay kaydı dönenlerin yaklaşık beşte birini kaçırıyor; "10 dakikada olay yok" satırının bir kısmı ölçüm kaybı olabilir.
- **Ham karşılaştırma tek başına kullanılmamalı.** İlk tablo yalnız bağlam için verildi.

## Ek: sorgu tanımları

Canlıdan yalnız müşteri satırları okundu: `Users` (kimlik, kayıt platformu), `UserProfiles` (kayıt anı, toplam XP), `UserEvents`, `PaywallAnalyticsEvents`, `Subscriptions`. Sorgular yerel kopyada koştu ve depoya betik olarak kaydedilmedi. Tekrarlamak isteyen, yukarıdaki "Yöntem" bölümündeki tanımlarla yeniden yazmalı. Kod okuması Flutter `d5e4343` üzerinde yapıldı: `career_page.dart` (açılış, düğüm, şerit, sandık olayları), `celebration_coordinator.dart:296-301` (kutlamadan haritaya düğme), `career_strip.dart:119` (`target_card`).
