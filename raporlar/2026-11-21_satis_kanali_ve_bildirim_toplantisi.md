# Toplantı: Premium üyeler nereden geldi, bildirimler ne durumda

**Tarih:** 21 Kasım 2026, 00:07 · Tek geçiş; üyeler kurgusaldır. **Çağıran:** Mehmet.
**Sorular:** Premium üyeler nereden geldi? Satış hangi kanaldan oldu? Bildirim sistemi çalışıyor mu, hangi bildirimler gidiyor, ne kadar işe yarıyor?
**Verinin tarihi:** satışlar 17–18 Kasım, bildirimler 18 Kasım (uygulamanın kendi kayıtları; `2026-11-17_satin_alma_anlari.md`, `2026-11-18_genel_durum.md` 3.4 ve 3.7). 18 Kasım'dan sonrası için yeni döküm editörden istendi. App Store Connect oturumu kapalı; mağaza kaynak sayıları bu toplantıda güncellenemedi.

## 1. Premium üyeler
**Dört gerçek satış, hepsi iOS:**
| | A | B | C | D |
|---|---|---|---|---|
| Tarih | 2 Kas | 3 Kas | 7 Kas | 13 Kas |
| Plan | Yıllık, deneme | Aylık | Yıllık, deneme | Aylık |
| Kayıttan satın almaya | 2 dk 57 sn | 2 gün 18 sa | 35 sn | 1 dk 45 sn |
| Uygulama içinde satışı açan yüzey | ilk hikâye bitişi | Premium şeridi | Premium şeridi | kilitli dizi bölümü |
| Bugün | etkin (ücretliye döndü) | etkin | denemeyi 7. gün kapattı | etkin |

Etkin ödeyen: 3 (1 yıllık, 2 aylık). Android: 0. Satın almaya basıp tamamlamayan: 11 (neden bilinmiyor; kaydı 1.0.4 ile gelecek).

**"Nereden geldiler" sorusunun iki katmanı var:**
1. **Uygulamanın içinde hangi yüzey sattı:** biliniyor (tablo). Dört satışın üçünde Premium şeridi son dört dakikada görülmüş; biri kilitli diziden.
2. **Uygulamaya nereden geldiler (Instagram mı, mağaza araması mı):** **bilinmiyor.** Uygulama kayıtlarında kullanıcı başına geliş kaynağı ayrıntısı yok. Elimizdeki tek ipuçları: 15 Kasım'da App Store Connect etkin planların kaynağını "App Store araması 2, başka uygulamadan yönlendirme 2, göz atma 1" gösteriyordu (5 plan; biri testçi, biri denemeydi); bir mağaza yorumu "Instagram'dan takip ediyorum" diyor; 17 Kasım'daki 76 kayıtlık sıçramanın kaynağı da bilinmiyor.

**Sean:** "Mağaza araması" çoğu zaman uygulamanın adını yazıp arayan kişidir; adı da ancak Instagram'dan duymuş olabilir. "Başka uygulamadan yönlendirme" bir uygulamanın içindeki bağlantıdan gelen demek; bizde bu büyük olasılıkla Instagram. Yani satışların hepsi doğrudan ya da dolaylı Instagram'dan geliyor olabilir. Ama bu bir tahmin; kanıtı yok.
**Nate:** Dört satışla kanal kıyaslanmaz. Yapılabilecek olan, bundan sonrasını ölçülür kılmak.
**Nassim:** "Bilmiyoruz" demek, uydurma bir kanal tablosundan iyidir.

**Kanalı ölçülür kılmak için (onboarding'e soru eklemeden):**
- Instagram'daki her bağlantı (profil, hikâye, reels açıklaması) kendi kampanya etiketiyle: App Store'da kampanya bağlantısı, Play'de yönlendiren bilgisi. Mağazalar indirme ve satışı etikete göre ayırır.
- Sunucuda kurulum kaynağı kaydı var görünüyor (`InstallSourceReport`); ne tuttuğunu ve dört alıcıda ne yazdığını editör raporlayacak.
- App Store Connect'e Mehmet giriş yapınca ekip başı ödeyenlerin kaynak dökümünü çıkarır.

## 2. Bildirimler
**Gidiyor mu:** Evet. 18 Kasım'a kadar 246 müşteriye 1.015 bildirim; son 7 günde 212 kişiye 494.

| Tür | Bugüne kadar | Son 7 gün | Son 7 gün: 2 saat içinde uygulamayı açan |
|---|---|---|---|
| Günün quizi | 187 | 103 | 7 |
| Kelime tekrarı | 177 | 107 | 3 |
| Seri başlat | 154 | 68 | 5 |
| Günlük açılan metin | 154 | 16 | 0 |
| İlk okumaya çağrı | 139 | 72 | 2 |
| Geri dön | 130 | 85 | 1 |
| Günlük hatırlatma | 39 | 35 | 4 |
| Seri hatırlatma | 24 | 5 | 0 |
| Diğer | 11 | 3 | 0 |
| **Toplam** | **1.015** | **494** | **22 (%4)** |

**İşe yarıyor mu:** Ölçülebildiği kadarıyla çok az. Bildirime dokunma kaydı toplam 18 (10 kişi). "2 saat içinde açan" 22 kişi bildirimin etkisi demek değildir; o saatte zaten açacak olanları da sayar.

**Bilinmeyen üç şey (üçü de sonucu değiştirir):**
| Bilinmeyen | Neden | Ne zaman öğrenilir |
|---|---|---|
| Kaç kullanıcı bildirime izin verdi | Alanı dolduran kod 1.0.4'te; müşteriler eski sürümde | 1.0.4 mağazada olunca |
| Bildirim telefona ulaşıyor mu | Ulaşma kaydı boş | 1.0.4 (Android); iOS'ta sınırlı |
| Hangi tür açılıyor | Dokunma kaydı türü taşımıyor | Editör, dokunma kaydı gönderim kaydıyla eşleşiyor mu bakacak |

Bildirim adresi olan: iOS %97, Android %79; adres izin demek değildir.

**Don:** İzin ilk kez onboarding'in 15. adımında, kullanıcı daha hiçbir şey okumadan isteniyor. Kullanıcı neye izin verdiğini bilmeden "hayır" der. 1.0.4'te ikinci bir kapı var: hikâye bitince "Yarın hatırlat". İzin oranını asıl o belirleyecek.
**Tony:** 494 bildirimin 192'si "geri dön", "ilk okumaya çağrı" ve "seri başlat": uygulamayı bırakmış kişiye giden çağrılar. Bırakan kişiye aynı cümleyle üç kez gitmek şikâyet ve bildirim kapatma getirir. Altı müşteri bildirim ayarını kaydederken hata aldı; düzeltilmedi.
**Paul:** Metinleri görmeden konuşmayalım. Her türün bugünkü metni çıkarılsın; "uygulamanın sesi" belgesine göre yeniden yazarım. Sıradaki hikâyenin merak cümlesi en iyi bildirim metnidir: "Emma her sabah tilkiye biraz daha yaklaşıyor…"
**Sean:** En değerli bildirim, vaadi olan bildirimdir: "Sıradaki hikâyen açıldı." 1.0.4 ile bunu söyleyebiliyoruz, çünkü artık gerçekten bir sıradaki hikâye var.
**Kent:** Gönderim tarafı çalışıyor; eksik olan ölçüm. Türü dokunma kaydına eklemek küçük iş.
**Nassim:** İzin oranını bilmeden bildirim düzenini değiştirmek karanlıkta ayar yapmaktır. Önce 1.0.4, sonra bir hafta veri, sonra karar. Tek istisna zarar veren şey: bırakmış kişiye aynı çağrıyı tekrar tekrar göndermek bugün durdurulabilir.

## 3. Kararlar
1. **Kanal:** bugün söylenebilen "dört satışın hepsi iOS; uygulamaya geliş kaynağı bilinmiyor". Tahmin tablo olarak sunulmaz.
2. **Kanalı ölçmek:** Instagram bağlantılarına kampanya etiketi (Instagram ekibiyle; kod istemez). Editör kurulum kaynağı kaydını raporlar.
3. **Bildirim:** 1.0.4 mağazaya çıkmadan düzen değişmez. Çıktıktan bir hafta sonra izin oranı, ulaşma ve türe göre açılma okunur; günde en çok iki bildirim düzeni o veriyle yeniden ele alınır.
4. **Şimdi yapılacak iki şey (kod yok):** editör her türün metnini, gönderim saatlerini ve kişi başı sıklığı çıkarır; Paul metinleri "uygulamanın sesi"yle yeniden yazar.
5. **Ölçü:** bildirimin başarısı "gönderilen" değil, "izin veren kullanıcıda, gönderimden sonraki 2 saatte hikâye açan" oranıdır; izin vermeyenler paydadan çıkar.

## İtirazlar
- **Sean:** Kampanya etiketi geçmişi kurtarmaz; ilk dört alıcının kaynağını büyük olasılıkla hiç öğrenemeyeceğiz.
- **Tony:** Bildirim ayarı kaydetme hatası (6 müşteri) "sonra"ya bırakılmamalı; kullanıcı bildirimi kapatmak isteyip kapatamıyorsa bu şikâyettir.
