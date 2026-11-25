# Haftalık rapor ve ekip toplantısı (19–25 Kasım 2026)

**Tarih:** 25 Kasım 2026, 16:30 · **Mehmet (16:02):** "Hemen bir toplantı yapın. Haftalık rapor istiyorum."
Tek geçiş; üyeler kurgusaldır. Rakamlar bugün çekildi; çekilemeyenler açıkça yazıldı.

## 1. Durum: 🟡 belirsiz
İş çok ilerledi, ama **1.0.4'ün son hâli (derleme 50) üç gündür mağaza kapısında bekliyor** ve iOS tarafının sayıları bu turda çekilemedi.

## 2. Rakamlar
| Ölçü | 15 Kas | 25 Kas | Checkpoint (4 Ara) | Kaynak, not |
|---|---|---|---|---|
| Android edinme (son 28 gün) | 80 | **180** | – | Play Console; önceki 28 güne göre +%800 (taban çok küçüktü) |
| Android ilk açılış (son 28 gün) | 50 | **105** | – | Play Console |
| Android aylık etkin cihaz | 56 | **123** | en az 60 ✔ | Play Console |
| Android gelir | 0 | **–** (0) | – | Play Console |
| Android puan | – | **4,75** | – | Play Console |
| iOS ilk indirme | 160 (13 Kas) | **çekilemedi** | – | App Store Connect oturumu kapalı |
| Toplam indirme | ~240 | **en az ~340** | en az 275 ✔ | Android 180 + iOS'un 13 Kasım sayısı; gerçek sayı daha yüksek |
| Ödeyen abone (gerçek satış) | 3 | **çekilemedi** | en az 5 ? | App Store Connect gerekli |
| PMF anketi | yok | **yok** | en az bir kez ✗ | – |
| Onboarding'i bitirip okumaya başlayan | %81–85 | **ölçülmedi** | en az %90 (29 Kas sınavı) | Uygulamanın kendi kayıtlarından, editör çeker |
Google Analytics bu turda açılmadı (kullanım tasarrufu); uygulama içi sayılar editörden istenecek.

## 3. Mağaza durumu (Play Console, bugün)
| Kanal | Sürüm | Durum |
|---|---|---|
| Play üretim | **47 (1.0.4)** | "Google Play'de mevcut", 20 Kasım 00:33'ten beri |
| Play üretim | **50 (1.0.4)** | Sürüm 23 Kasım 00:43'te hazırlanmış; **yayında değil.** Kontrol panelinde "İncelemeye gönderilmeye hazır değişiklikleriniz var" yazıyor |
| iOS | bilinmiyor | App Store Connect'e girilemedi |
**İki sonuç:**
1. Ekip üç gündür "mağazada 1.0.2 var" diye konuşuyordu. Play'de 20 Kasım'dan beri **1.0.4'ün 47 numaralı derlemesi** yayında görünüyor. Android kullanıcılarının bir bölümü yolculuğu ve "Seviyeni belgele" satırını (eski ilk ekranıyla) günlerdir görüyor olabilir. Sunucudaki uygulama sürümü dağılımıyla doğrulanmalı (editör).
2. Derleme 50 Play'de **bir düğme uzakta** duruyor: değişiklikler incelemeye gönderilmemiş.

## 4. Bu hafta biten işler
- **Sunucu (canlıda):** bırakan kullanıcıya en çok 7 bildirim (önce 45); yeni "geri dön" metinleri, sıradaki hikâyenin adıyla; quiz cevabında tam eşleşme; sıralama rozetleri kapalı; sınav sistemi (ısınma soruları seviyeye göre, sınanmamış seviye verilmez, belge testi yalnız yükseltir, seviye değişince yolculuk, kelime bazında kayıt).
- **İçerik (canlıda):** dokuz metin B1'e; dört belirsiz B1 ölçüm parçası kapandı, dört yenisi girdi; 29 belge sorusunun kökü düzeldi.
- **Uygulama (derleme 50, test kanallarında):** yolculuk kartı (gövde dokunma, "Yarın hatırlat", yolculuğun adı), kariyer sayfası (yol rozet kenarında, yüzde yolda), günün quizi, yorum ekranı, belge testinde sorular tek tek ve puansız sonuç, ana sayfa slaytı (Türkçe ad, seviye), okuma balonu düzeltmeleri.
- **Ekip:** sınav sistemi değerlendirmesi, test tanımı, 176 sorunun okunması, öz değerlendirme ve iki eğitim, yedi ekip kuralı.

## 5. Derleme 50 görüntüleri (ekip bugün baktı: Dieter, Don, Charles)
Kareler: `raporlar/ekran_2026-11-22/d50_kariyer.png`, `d50_belge.png`, `d50_ana_sayfa_karti.png`. Öbür dört kareye (quiz, ölçüm, ölçüm sonucu, slayt-yolculuk-yorum) bu turda bakılmadı.
| # | Gözlem | Önem | Karar |
|---|---|---|---|
| 1 | Kariyer: yol rozetin kenarında başlıyor ve bitiyor; halka ve kapı yok; yüzde bayrakta. İstenen oldu | – | Temiz |
| 2 | Kariyer alt şeridi "Meraklı'ya doğru ilerliyorsun" diyor; karar "yaklaşık 5 günlük okuma kaldı" idi | Orta | Editöre soru: gün tahmini neden yok? Bugünkü cümle bilgi vermiyor |
| 3 | Kariyer, büyük yazı, %0: "Yeni yol başladı" etiketi bayrağın ve sıradaki rozetin dibine sıkışıyor | Düşük | Sonraki derleme |
| 4 | Kariyer, %92: bayrak sıradaki rozetin kenarına değiyor (24 pt kuralı tutmuyor) | Düşük | Sonraki derleme |
| 5 | Belge testi: giriş ekranı dürüst ("okuma seviyeni ölçer ve paylaşabileceğin bir belge verir"; "sertifika" ya da "resmî" yok); sorular tek tek; sonuçta puan yok, "B1 seviyesinin sonuna yaklaştın" | – | Temiz |
| 6 | Belge testi, metin sorusu: normal yazıda üçüncü şık "Devam" şeridinin altında yarım; büyük yazıda şıkların hiçbiri ilk ekranda görünmüyor | Orta | Kaydırınca geliyor; yine de editöre: şıkların altta olduğunu gösteren bir ipucu var mı? Sonraki derleme |
| 7 | Belge sonucu: "Intermediate / Independent User" İngilizce | Düşük | Kalır (CEFR'in kendi adları) |
| 8 | Ana sayfa kartı: üç durum da kararlaştırıldığı gibi | – | Temiz |
**Sonuç (Dieter, Don):** derleme 50'yi mağazaya göndermeyi engelleyen bir bulgu yok. 2, 3, 4 ve 6 sonraki derlemeye.

## 6. Toplantı
**Steve:** Bir haftada dört büyük konu ve üç küçük konu aynı derlemeye girdi; sonra derleme üç gün bekledi. Hız sorunu kodda değil, kapıda. Bu haftanın tek işi 1.0.4'ü mağazaya çıkarmak.
**Kent:** Play'de derleme 50 hazır, gönderilmemiş. iOS'un durumunu bilmiyoruz. Telefonda yapılacak kontroller (satın alma, iptal, promosyon kodu, bildirimden kapak) hâlâ açık; yapılmadan gönderilirse "denenmedi" diye yazılmalı. App Store'da kademeli yayın öneriyorum.
**Nate:** Android etkin cihaz 56'dan 123'e çıktı; sayı küçük ama yön açık (iki ölçüm; hipotez). Ödeyen abone ve iOS olmadan checkpoint'i kapatamam. 29 Kasım sınavının sayısı (okumaya başlama oranı) dört gün sonra isteniyor; editörden sürüme göre ayrılmış sayım gerekiyor.
**Sean:** PMF anketi dört haftadır yapılmadı; 4 Aralık'a yetişmez, çünkü 1.0.4 yayınlanmadan sormak eski ürünü ölçer. Yayından iki hafta sonraya öneriyorum.
**Charles, Paul:** 176 soru okundu. En önemli açık soru şıkların ekranda karıştırılıp karıştırılmadığı; cevap üç gündür gelmedi (editöre iletilmemiş olabilir). Dört yeni B2 sorusu ve iki şık düzeltmesi canlıya yazılmayı bekliyor.
**Don:** Bu hafta ana sayfadan açılışın kaynağını ölçmeye başladık (derleme 50). Veri ancak yayından sonra gelir.
**Tony:** Bu hafta yeni mağaza yorumu ya da e-posta derlemedim; Play puanı 4,75. Yorum dökümü hâlâ borç.
**Nassim:** aşağıda.

## 7. Kararlar
| # | Karar | Sahibi | Tarih |
|---|---|---|---|
| 1 | Bu haftanın tek ürün işi: 1.0.4 (50) mağazada. Yeni iş başlamaz | Steve | 28 Kas |
| 2 | Play'de derleme 50 incelemeye gönderilir; iOS'ta derleme 50 incelemeye gönderilir (kademeli yayınla) | **Mehmet** | 26 Kas |
| 3 | Telefon kontrolleri: yapılanlar ve yapılmayanlar tek liste; yapılmayan "denenmedi" diye sürüm notuna yazılır | Kent, Mehmet | Gönderimden önce |
| 4 | Editöre tek iş tanımı (aşağıda, bölüm 9): sürüm dağılımı, şık karıştırma, 29 Kasım sayımı, haftalık tablo, görüntü soruları | Editör | 27 Kas |
| 5 | 29 Kasım sınavı: okumaya başlama oranı sürüme göre okunur; 1.0.4 mağazada değilse sınav 1.0.4 yayınından 7 gün sonraya kayar | Nate | 29 Kas |
| 6 | PMF anketi: 1.0.4 yayınından iki hafta sonra, en az üç hikâye bitirmiş kullanıcılara. Checkpoint'in 4. maddesi bu yüzden 4 Aralık'ta **tutmayacak**; kayda geçti | Sean | Yayın + 14 gün |
| 7 | App Store Connect sayıları (indirme, ödeyen abone, gelir) Mehmet oturum açınca çekilir ve bu rapora eklenir | Nate | Mehmet'in oturumuyla |
| 8 | Sonraki sürümün en çok dört konusu, 1.0.4 yayınlandıktan sonra seçilir. Adaylar: profil resmi ve hesap teşviki · yolculuk rozetleri · belge soruları ve şık karıştırma · ana sayfa (veriyle) | Steve | Yayından sonra |
| 9 | Yayından önce üç tahmin (ekip kuralı 6), aşağıda | Nate | Bugün |

**Üç tahmin (1.0.4, yayından 14 gün sonra bakılacak):**
1. Onboarding'i bitirenlerin okumaya başlama oranı %81–85'ten **%88 ve üstüne** çıkar (yolculuk kartı ilk kart olduğu için).
2. Yeni gelenlerin ilk gün bir hikâyeyi bitirme oranı 1.0.2'ye göre **artar** (taban sayı editörden gelince sayıya çevrilecek).
3. "Geri dön" bildirimlerine dokunma, 185'te 1'den **en az 100'de 3'e** çıkar.

## 8. İtirazlar
| Kim | İtiraz | Sonuç |
|---|---|---|
| Nassim | "Toplam indirme hedefi tuttu" demek kolay; taban küçüktü ve asıl ölçü (ödeyen abone) bilinmiyor. Durum yeşil yazılamaz | **Kabul.** Durum 🟡 |
| Nassim | Üç gün "mağazada 1.0.2 var" varsayımıyla karar verildi; Play'de 1.0.4 (47) yayındaymış. Kimse mağazaya bakmadı | **Kabul.** Her toplantının başında mağaza durumu Play Console ve App Store Connect'ten okunur |
| Nassim | Derleme 50 yirmiye yakın değişiklik taşıyor ve telefonda satın alma denenmedi. En kötü durum: Android'de satın alma bozuk çıkar. Geri alma: Play'de önceki derlemeye dönülemez, yeni derleme gerekir | **Kabul.** Karar 3; Play'de de aşamalı yayın (%20 ile başlamak) önerilir, karar Mehmet'in |
| Dieter | Slayt başlığının boyu slayttan slayta değişiyor (Mehmet'in isteği) | **Şerh.** Mehmet'in kararı geçerli; yayından sonra görüntüyle yeniden bakılır |
| Kent | "Bir derleme, bir konu" kuralı derleme 50 için geç kaldı | **Kabul.** Sonraki sürümden itibaren |

## 9. Editöre iş tanımı (kopyalanabilir)
> **Görev (25 Kasım; salt okuma, kod yazma yok, yayın yok). Cevap: `raporlar/2026-11-26_editor_haftalik_cevap.md`.**
> 1. **Sürüm dağılımı:** son 7 günde etkin kullanıcıların uygulama sürümü ve derleme numarası dağılımı, iOS ve Android ayrı. Play'de 20 Kasım'dan beri 1.0.4 (47) yayında görünüyor; doğru mu, kaç kullanıcı 47'de? iOS'ta mağazadaki sürüm hangisi?
> 2. **Şıklar karıştırılıyor mu?** "Seviyeni belgele"de şıklar ekranda kayıttaki sırayla mı görünüyor (`AssessmentService` ve uygulama)? Kayıtta doğru şıkkın yeri soru türüne bağlı (`raporlar/2026-11-22_belge_sorulari_paul_okumasi.md` bölüm 1). Karıştırılmıyorsa düzeltmenin iş büyüklüğü ve eski sürümle uyumu.
> 3. **29 Kasım sayımı:** onboarding'i bitiren müşterilerin kaçı okumaya başladı; 11–25 Kasım, sürüme göre (1.0.2, 1.0.4-47) ve platforma göre. Aynı dönemde yeni gelenlerin ilk gün hikâye bitirme oranı.
> 4. **Haftalık tablo (19–25 Kasım):** yeni müşteri (gün gün, platform), ilk hikâyeyi bitiren, 7. gün dönen, günün quizi başlayan ve bitiren, seviye ölçümü başlayan ve bitiren, belge testi denemesi, "geri dön" bildirimi gönderim ve dokunma (yeni metinlerle, 22 Kasım'dan sonra ayrı), yeni abonelik (promosyon ve testçi hariç).
> 5. **Belge iddiası soruları B1–B4** (`raporlar/2026-11-22_belge_seviye_iddiasi_plani.md`): puan eşikleri, soru bazında kayıt, metin dökümü. (Belgenin ve giriş ekranının metni görüntüde görüldü; "sertifika" ya da "resmî" sözü yok. Mağaza açıklamasındaki ve sitedeki iddialar hâlâ isteniyor.)
> 6. **Görüntü soruları (derleme 50):** kariyer alt şeridi neden "…'ya doğru ilerliyorsun" diyor, gün tahmini neden yok? Belge testinde şıklar ekranın altında kalınca kullanıcıya kaydırma ipucu var mı?
> 7. Bekleyen canlı veri işi (çalıştırma **Mehmet'in sözüyle**, bu görevde çalıştırma): dört yeni B2 sorusu ve iki şık düzeltmesi için yedekli betiği hazırla, çalıştırmadan raporla.

## 10. Mehmet'ten beklenenler
1. Play Console'da derleme 50'yi incelemeye göndermek (istersen %20 aşamalı yayınla).
2. iOS'ta derleme 50'nin durumu: gönderildiyse söylemen yeter; gönderilmediyse gönderim (kademeli yayın önerilir).
3. App Store Connect'te oturum açmak (Chrome); iOS sayılarını çekip rapora ekleyelim.
4. Editöre bölüm 9'daki iş tanımını vermek.
5. Telefon kontrollerinden hangilerini yaptığını tek satırla yazmak (satın alma, iptal, promosyon kodu, bildirim).
6. Belge soruları için bir İngilizce öğretmeni (dış göz); acil değil.
