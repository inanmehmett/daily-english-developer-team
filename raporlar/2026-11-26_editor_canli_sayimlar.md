# Canlı sayımlar (26 Kasım 2026, 17:50)

**Kimden:** editör · **Kaynak:** canlı veritabanı, salt okuma. Mehmet: "İzin kuralını sen ekle." Erişim açıldı; `ortak/editor_gorevi_2026-11-25.md` A1–A5, A7, A11 ve kuyruk 2–3'ün sayımları tek turda çekildi.
**Tanımlar:** "müşteri" = hesap türü `customer` (432 hesap; 185 testçi, 146 geliştirici, 2 promosyon hariç). Günler Türkiye saatiyle. Kişi adı ve e-posta okunmadı.
**Okuma kuralı:** tek ölçüm hipotezdir; küçük gruplarda (20'nin altı) yüzde yazılmadı.

## 1. Sürümler (A1): son 7 günde olay gönderen müşteriler
| Platform | 1.0.2 (45) | 1.0.4 (47) | 1.0.4 (49) | 1.0.4 (50) |
|---|---|---|---|---|
| Android | 23 | 40 | 1 | 1 |
| iOS | 73 | – | – | 22 |
- **iOS:** 1.0.4 (50) ile gelen ilk müşteri olayı **24 Kasım 13:56**; yayın o gün ya da hemen öncesi. Etkin iOS müşterilerinin dörtte biri yeni sürümde, dörtte üçü hâlâ 1.0.2'de.
- **Android:** müşterilerin çoğu 20 Kasım'dan beri **1.0.4 (47)**'de. Derleme 50'de bugün 17:50 itibarıyla **1 müşteri** var; Play'deki yayın henüz kullanıcıya ulaşmamış ya da yeni ulaşıyor.
- 33 müşterinin olayında sürüm bilgisi yok (sunucunun yazdığı olaylar).

## 2. Okumaya başlama ve ilk gün (A3): 11–25 Kasım'da gelen müşteriler, ilk sürümlerine göre
| Platform, ilk sürüm | Yeni müşteri | Onboarding'i bitiren | Okumaya başlayan | İlk gün bir hikâye bitiren |
|---|---|---|---|---|
| Android 1.0.2 | 67 | 62 | 46 (%74) | 34 (%51) |
| Android 1.0.4 (47) | 17 | 12 | 9 | 7 |
| Android 1.0.4 (49, 50) | 2 | 2 | 2 | 0 |
| iOS 1.0.2 | 141 | 132 | 109 (%83) | 91 (%65) |
| iOS 1.0.4 (50) | 9 | 9 | 6 | 6 |
| Hiç olay göndermemiş | 35 | 24 | 7 | 4 |
| **Toplam** | **271** | **241** | **179 (%74)** | **142 (%52)** |
- **29 Kasım sınavı (hedef %90):** tutmuyor. Toplam %74; hiç olay göndermeyenler çıkarılınca 172/217 = %79.
- **1.0.4'ün etkisi henüz okunamaz:** 1.0.4 ile gelen 28 müşteri var (onboarding'i bitiren 23, okumaya başlayan 17). Karar 5 gereği sınav 1.0.4 yayınından 7 gün sonraya kayar; iOS için 1 Aralık, Android 50 için yayın teyidinden sonra.
- **Tanım farkı:** "onboarding'i bitiren" profildeki işaret, "okumaya başlayan" en az bir okuma kaydı. Aynı tanım 11–15 Kasım için 30/39 veriyor; 15 Kasım raporundaki sayı 29/34'tü (o gün olay kayıtlarından sayılmıştı). İki sayı aynı yönde, payda farklı.
- "Hiç olay göndermemiş" 35 müşterinin 24'ü onboarding'i bitirmiş görünüp 7'si okumuş; bu grup ayrıca bakılmaya değer (uygulama olay göndermeden kapanıyor olabilir).

## 3. Tutunma (A3): başladığı haftaya göre, o gün uygulamadan olay gelenler
Payda, o güne ulaşmış (süresi dolmuş) müşteriler.
| Başlangıç haftası | Platform | Yeni | 1. gün | 7. gün | 14. gün |
|---|---|---|---|---|---|
| 26 Eki | Android | 22 | 1/22 | 0/22 | 0/22 |
| 26 Eki | iOS | 5 | 2/5 | 0/5 | 1/5 |
| 2 Kas | Android | 30 | 5/30 (%17) | 0/30 | 0/30 |
| 2 Kas | iOS | 69 | 17/69 (%25) | 3/69 (%4) | 3/69 (%4) |
| 9 Kas | Android | 14 | 1/14 | 1/14 | 0/5 |
| 9 Kas | iOS | 51 | 11/51 (%22) | 3/51 (%6) | 1/22 |
| 16 Kas | Android | 86 | 21/86 (%24) | **8/53 (%15)** | – |
| 16 Kas | iOS | 119 | 30/119 (%25) | 5/74 (%7) | – |
| 23 Kas | Android | 10 | 2/3 | – | – |
| 23 Kas | iOS | 26 | 4/14 | – | – |
- 1. gün dönüşü iOS'ta dört haftadır %22–25; Android 16 Kasım haftasında iOS'a yetişti (%24).
- **Android 7. gün, 16 Kasım haftası: 8/53 (%15)**; önceki üç haftanın toplamı 1/66. Tek hafta, hipotez. Olası neden 20 Kasım'da gelen 1.0.4 (47); sürüme göre ayrım bir sonraki turda.
- iOS 7. gün dört haftadır %4–7: sorun hâlâ 2–7. günler.
- Uyarı: 29 Ekim öncesi olay kaydı yok; ilk satırlar eksik sayabilir.

## 4. Abonelikler (A5, kuyruk 2 ve 3)
33 abonelik kaydı var (en büyük kimlik 37; 4 kimlik boş, silinmiş satır). Hesap türüne göre: testçi 13, **müşteri 12**, geliştirici 5, promosyon 3. Panelde "kayıt 34" görünürken gerçek satışın tek haneli olmasının nedeni bu.

**Müşteri kayıtları (12):**
| Kayıt | Platform, plan | Durum | Yenileme | Başlangıç → bitiş | Not |
|---|---|---|---|---|---|
| 21 | iOS yıllık | **Ücretli** | açık | 2 Kas deneme → 9 Kas ödeme | Misafir. 19 Kas'tan beri olay yok |
| 22 | iOS aylık | **Ücretli** | açık | 3 Kas → 3 Ara | Üye. 14 Kas'tan beri olay yok |
| 24 | iOS aylık | **Ücretli** | açık | 13 Kas → 13 Ara | Üye. Dün etkin |
| 33 | iOS aylık | **Ücretli** | açık | 23 Kas → 23 Ara | Üye. Bugün etkin |
| 31 | iOS yıllık | Deneme | **açık** | 21 Kas → **28 Kas 01:13** | Üye. Denemede 0 hikâye bitirdi; 24 Kas'tan beri olay yok |
| 32 | iOS yıllık | Deneme | açık | 22 Kas → 29 Kas 19:11 | Üye. Denemede 7 hikâye bitirdi |
| 34 | iOS yıllık | Deneme | **kapalı** | 24 Kas → 1 Ara 16:40 | Üye. Aşağıda |
| 35 | iOS yıllık | Deneme | açık | 24 Kas → 1 Ara 20:25 | Misafir. 24 Kas'tan beri olay yok |
| 36 | iOS yıllık | Deneme | açık | 25 Kas → 2 Ara 14:32 | Misafir. Bugün etkin |
| 37 | **Android** yıllık | Deneme | açık | 25 Kas → 2 Ara 23:46 | Misafir. Android'de ilk müşteri denemesi |
| 23 | iOS yıllık | Bitti | – | 7 Kas → 14 Kas | Deneme, son gün yenileme kapatıldı; hiç okumadı |
| 28 | Android yıllık | Bitti | – | 19 Kas → 26 Kas | Denemesiz satın alma, aynı dakikalarda iki iptal. son olayı 19 Kas 19:41, sonrasında yok; test satın alması olabilir (Mehmet'in 19 Kas 19:16 iptal denemesiyle aynı saatler) |

- **Ödeyen müşteri bugün: 4** (21, 22, 24, 33). Checkpoint "en az 5": 28 Kasım 01:13'te 31 numaralı deneme ücrete dönerse 5 olur.
- **Deneme özeti (müşteri):** 8 deneme başladı; 1 ücrete döndü (21), 1 dönmeden bitti (23), 5'i sürüyor ve yenilemesi açık (31, 32, 35, 36, 37), 1'i sürüyor ve yenilemesi kapalı (34).
- **28 Kasım'da biten deneme (kuyruk 2d):** yenileme **açık**. Kullanıcı denemede hiç hikâye bitirmedi ve 24 Kasım akşamından beri uygulamadan olay gelmedi; ücret alınırsa iade ya da şikâyet riski olan tek kayıt bu. Deneme bitiş bildirimi bu kayda 25 Kasım 21:05'te gitti, dokunulmadı.
- **Kayıt 34 (kuyruk 2b, 3e):** hesabını açtığı gün, onboarding'i bitirdikten 9 dakika sonra deneme başlattı (24 Kas 16:40); **4,5 saat sonra** yenilemeyi kapattı (21:07). Öncesinde 2, denemede 3 hikâye bitirdi; kapattıktan sonra da kullanıyor (bugün 14:33'te etkin). Erken kapatma "unutmayayım" tedbirine benziyor, terk değil. Tarihler tutarlı: başlangıç 24 Kas 16:40, bitiş 1 Ara 16:40, tam 7 gün; saat kayması yok. Hangi ekrandan satın aldığı olaylardan ayrılamadı.
- **Yanlış sınıflanmış olabilecek kayıtlar:** 28 (yukarıda). Promosyon türündeki 19 ve 30 doğru ayrılmış.
- Panel sayaçlarının bu tabloyla satır satır karşılaştırması yapılmadı (panel oturumu gerekir); tablo, karşılaştırmanın dayanağı olarak burada.

## 5. Geri bildirimler (A2)
- Profildeki "bize ulaş" alanından bugüne kadar **4 ileti** gelmiş; **hiçbiri müşteriden değil** (2 geliştirici, 2 testçi). Dördü de "okundu" işaretli. Okunmamış müşteri iletisi yok.
- Son ileti (18 Kas, testçi, Android 1.0.2), özet: denemek için indirdi ama "her şey ücretli olduğu için doğru düzgün deneyimleyemedi"; "en azından 1 hafta açsaydınız"; A2 hikâyeleri başka uygulamalara göre zor geldi; birkaç çeviri yanlışı gördü.
- **Mağazada değerlendir:** profildeki girişe 5 müşteri 13 kez dokundu. **Uygulama içi değerlendirme penceresi bugüne kadar yalnız 1 kez istendi** (1 müşteri). Koşullar (3 gün, 3 etkin gün, 3 bitmiş okuma ve "mutlu an") pratikte kimseye uymuyor.

## 6. Bildirimler, 22 Kasım'dan beri (A11), müşteriler, eski metinler (`copy_v2`)
| Tür | Gönderim | Kişi | Dokunma | Oran |
|---|---|---|---|---|
| Geri dön | 165 | 157 | 3 | %1,8 |
| İlk okuma çağrısı | 60 | 50 | 0 | %0 |
| Seri başlat (1–2 gün) | 42 | 37 | 5 | %11,9 |
| Günün quizi | 38 | 25 | 0 | %0 |
| Kelime tekrarı | 34 | 31 | 0 | %0 |
| Günlük hatırlatma | 32 | 27 | 0 | %0 |
| Seri (3+ gün) | 23 | 13 | 4 | %17,4 |
| Seri telafisi | 7 | 7 | 0 | – |
| Deneme bitiyor | 1 | 1 | 0 | – |
| **Toplam** | **402** | – | **12** | **%3,0** |
- Dokunma yalnız seri ailesinde var; öbür altı türde 172 gönderimde sıfır.
- **Tahmin 3** ("geri dön" 185'te 1'den 100'de 3'e): 165'te 3 (%1,8). Yön doğru, hedefin altında.
- Bu tablo yeni metinlerin (`copy_v3`, 26 Kas 17:30'dan beri yayında) karşılaştırma tabanıdır. Aynı tablo 3 Aralık'ta yeniden çekilmeli.

## 7. Haftalık tablo (A7), 19–25 Kasım, müşteriler
| Gün | 19 | 20 | 21 | 22 | 23 | 24 | 25 | Toplam |
|---|---|---|---|---|---|---|---|---|
| Yeni müşteri | 19 | 19 | 22 | 18 | 10 | 7 | 7 | 102 |
| iOS | 9 | 11 | 17 | 8 | 7 | 7 | 6 | 65 |
| Android | 10 | 8 | 5 | 10 | 3 | 0 | 1 | 37 |
- **Android'de yeni müşteri 23–25 Kasım'da 3, 0, 1.** Önceki dört günün ortalaması 8. Üç gün, hipotez; neden bilinmiyor (Instagram akışı, Play'deki inceleme, mağaza sayfası). 26 Kasım'da 17:50'ye kadar 6 Android, 6 iOS.

| Ölçü (19–25 Kas) | Sayı | Kişi |
|---|---|---|
| Okumaya başlama | 428 | 119 |
| Hikâye bitirme | 335 | 74 |
| Günün quizi: başlayan / bitiren tur | 100 / 98 | 59 |
| Seviye ölçümü: başlayan / biten | 40 / 30 | – |
| Belge testi denemesi | 1 | 1 |
| Bildirime dokunma | 29 | 20 |
| Yeni abonelik kaydı (müşteri) | 8 | 6 deneme (5 iOS, 1 Android), 1 aylık, 1 denemesiz Android (kayıt 28) |

## 8. Çekirdek grup (A4): en az 3 hikâye bitirmiş ve son 14 günde etkin
- **64 müşteri:** 44 iOS, 20 Android; 41'i misafir, 23'ü üye. Hepsinin bildirim adresi var; Android'de izin 3 açık, 8 kapalı (9'u bilinmiyor); iOS'ta 11 açık (33'ü bilinmiyor).
- Son 14 gün, kişi başına: 4,3 hikâye bitirme (ortanca 3), 3,4 etkin gün (ortanca 3), 85 kelimeye dokunma. 43'ü günün quizini çözmüş. **7 gün ve üstü etkin: 9 kişi.**
- En çok bitirdikleri: Two Cups (47), Rabbit Island (44), Thirty-One Mornings (39), First Ramadan in London (26), Breakfast in New York (19), Ali's First Snow (13), Sunday Lunch with Grandma (10), The Village That Whistles (9), Why Penguins Can't Fly (7), The Cat Knows the Time (6).

## 9. Bugünkü yayınların canlıda doğrulaması
- **PR #21:** soru havuzu canlıda istenen hâlde: B2 metin sorularında 32 etkin, 4 kapalı; dört yeni soru etkin, eskileri kapalı (silinmedi); iki şık düzeltmesi yerinde; her metinde 4 etkin soru. Yayından beri belge testi ya da ölçüm başlatan olmadı; karışık şık sırası canlıda henüz gözlenmedi.
- **PR #23:** yayından sonra (17:30) bildirim işi henüz çalışmadı (son gönderim 17:05). İlk `copy_v3` gönderimleri 18:05'te beklenir; ayrıca bakılacak.
- **PR #22 ve ad betiği:** aşağıda, `raporlar/2026-11-26_editor_ad_degisiklikleri.md`.

## Yapılmayanlar
- Mağaza yorumlarının dökümü ve panel sayaçlarının karşılaştırması (konsol ve panel oturumu gerekir).
- Tutunmanın sürüme göre ayrımı; kayıt 34'ün satın aldığı ekran.
- "Hiç olay göndermemiş" 35 müşterinin incelenmesi.
