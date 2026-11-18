# Yol haritası toplantısı

**Tarih:** 18 Kasım 2026, 23:01 · Tek geçiş; üyeler kurgusaldır, her biri gerçek adaşının belgelenmiş çerçevesinden konuşur. **Çağıran:** Mehmet.
**Dayanak:** `raporlar/2026-11-18_genel_durum.md` (editör, 311 müşteri, 18 Kas 19:35 kesimi) ve `raporlar/ekran_genel/` (60 kare).
**Katılanlar:** Steve İşler (lider), Kent Bekçi, Don Normal, Dieter Koç, Paul Ulus, Sean Büyüt, Nate Gümüş, Tony Şeyh, Nassim Talip; ekip başı (Claude).

## 0. Önce ekip başının hesabı
Editörün raporunun 6.2 bölümü ekibin ürettiği 13 çelişkiyi sayıyor. Hepsi doğru ve çoğunun kaynağı benim:
- 18 Kasım'da altı ayrı belgeyle görev tanımladım; aynı gün içinde harita, bildirim düzeni, rütbe ve yolculuk sayfası kararlarını değiştirdim.
- Taslaksız görev yazdım; harita için yarım gün boşa gitti.
- Listeyi güncel tutmadım: balon (Mehmet "aynı kalsın" demişti) ve çeviri işi (Mehmet "4 işçi" demişti) listede yanlış duruyor.
- En ağırı: 6 Kasım'dan beri hiçbir şey müşteriye ulaşmadı. Bu sürede müşterilerin yarısı (158 kişi; 76'sı tek günde, 17 Kasım'da) geldi ve eski ilk deneyimi gördü. Biz konuşurken onlar gitti.

Mehmet'in "ağzımızda geveleyip durduğumuz işler" sözü bunun adı. Toplantının işi yeni fikir bulmak değil, bunu bitirmek.

## 1. Rapor ne diyor (yedi sayı)
| | |
|---|---|
| Müşterinin elindeki sürüm | 6 Kasım'ın uygulaması (1.0.2+45). Yazılan 73 commit kimseye ulaşmadı. |
| İlk hikâye | 311 → okumaya başlayan 247 → bir hikâye bitiren 169 (%54) → iki bitiren 67 (%22) → dört bitiren 12 |
| Dönüş | 1. gün 60/288 (%21), 3. gün %10, 7. gün 4/153 (%3) |
| Satış | 4 (hepsi iOS). Satın almaya basan 15'in 11'i tamamlamadı; neden bilinmiyor. Android'de gerçek satın alma hiç doğrulanmadı. |
| Bildirim | 1.015 gönderim, 18 dokunuş. İzin oranı ve telefona ulaşıp ulaşmadığı bilinmiyor. |
| Dönenle dönmeyeni ayıran | Bir hikâye bitiren %38 / bitirmeyen %14. Okumanın dışına çıkan her eylem (cümle çevirisi %48, günün quizi %45, kelime çalışması %55) dönüşle birlikte görülüyor. Bağıntı, neden değil. |
| Kırılganlık | Sürüm 1'in 60 commit'i yalnız bir Mac'te; disk bugün %98 doldu. Son iki haftada uygulamadaki 80 commit'in 33'ü düzeltme. |

## 2. Herkes kendi alanından
**Steve İşler** (odak, hayır demek, "gerçek sanatçılar teslim eder"): "On iki gündür tek bir şey teslim etmedik. Elimizde iyi bir ürün fikri var: seviyene göre kısa hikâye, dokun, anla. Onu boğan şey fikir kıtlığı değil, fikir bolluğu. Bu toplantıdan bir yayın tarihi ve bir 'yapmıyoruz' listesi çıkmazsa toplantı da geveleme olur."

**Kent Bekçi** (küçük adım, sık birleştirme, çalışan yazılım): "On iki gün yaşayan, uzak depoda olmayan 44 commit'lik dal, bildiğim her kuralın tersi. Birleşmiş hâli hiç test edilmedi. Sıra belli: dalları uzak depoya gönder, `master`'ı içine al, testi koş, yayınla. Bundan sonra hiçbir dal bir haftadan uzun yaşamasın. Test takımının bıraktığı veritabanları diski dolduruyor; o da bu hafta kapanır."

**Don Normal** (gösterge, keşfedilebilirlik, zihin modeli): "Kareleri tek tek gezdim. Üç bulgu. Bir: birinci hikâyenin bitişinde (kare 24) ana düğme 'Sıradaki hikâye' küçük ekranda görünmüyor, kartın altında kalıyor. Bütün planımızın kaldıracı 'ilk gün iki hikâye'; onu açan düğme ekranda yok. Bu yayını durdurur. İki: cümle çevirisi basılı tutmayla açılıyor ve ekranda bunu söyleyen hiçbir işaret yok. Kullananın dönüşü %48, kullanmayanın %20; müşterilerin %22'si bulabilmiş; tek yazılı kullanıcı isteği de bu: 'tesadüfen keşfettim.' Üç: ikinci ve yedinci gün ana sayfası aynı; kelime tekrarı ve günün quizi için hiçbir çağrı yok, oysa dönenlerin yaptığı şeyler bunlar."

**Dieter Koç** (daha az ama daha iyi; dürüst tasarım): "Bitiş ekranında XP, Paylaş, defter kelimeleri, sıradaki kart, iki düğme, quiz bağlantısı, çıkış aynı yerde yarışıyor. İlk bitişte ayrıca iki-üç rozet penceresi düşüyor (163 kişinin 86'sında iki ve üzeri). 'Paylaş' ilk ekrandan çıkar, kart kısalır, düğme yukarı gelir. Bir de onboarding'deki beş yıldızlı 'Elif K., doğrulanmış kullanıcı': gerçek değilse dürüst tasarımın tersi ve mağaza riski. Elimizde yedi gerçek App Store yorumu var; biri oraya konur ya da ekran kalkar."

**Paul Ulus** (anlaşılır girdi, kısa ve kolay metin, tekrar): "Veri kitabın yazdığını söylüyor: 104–137 kelimelik metinler neredeyse hep bitiyor, 332 kelimelik 'Penguins' %58'de kalıyor. Sürüm 1 A1 ve A2 okuruna doğru başlangıcı veriyor (137 ve 121 kelime). B1 başlangıcı ise 281 ve 332 kelimeyle açılıyor; orada kayıp sürer. Başlangıç dizileri en kısadan uzuna sıralanmalı. İkinci konu: dokunuşların %98,5'i bugün elle düzeltilmiş ücretsiz rafta. Sürüm 1 okuru 12 başlangıç metnine yayacak ve bunların kaçının elle düzeltildiğini bilmiyoruz. Yanlış anlam, yeni okurun ilk hikâyesinde güveni bitirir. Çeviri işinde önce bu 12 metin."

**Sean Büyüt** (önce etkinleşme, sonra büyüme; olmazsa olmaz anketi): "Etkinleşme anımız belli: ilk hikâyeyi bitirmek. Oran %54. 17 Kasım'da bir günde 76 kişi geldi ve hepsini eski sürüme döktük; kaynağını bile bilmiyoruz. Yeni sürüm çıkmadan Instagram'dan uygulamaya yeni bir çağrı yapılmamalı. Gelir tarafında en ucuz iki iş kod istemiyor: Android'de bir gerçek satın alma denemesi ve tamamlamayan 11 kişinin nedenini gösterecek kaydın yayınlanması. 6 Kasım'da söz verdiğimiz anket hâlâ yapılmadı; dönen kullanıcıya sorulacak."

**Nate Gümüş** (işaret ve gürültü; sayı uygulamanın kaydından): "Raporun 'bilinmiyor' satırlarının yarısı yazılmış ama yayınlanmamış kodda. Yayından sonra günde 15–20 yeni müşteriyle iki haftada yaklaşık 250 kişi olur: ilk hikâyeyi bitirme oranındaki değişimi (%54 → %65) görürüz; ertesi gün dönüşü sınırda görürüz; satışı göremeyiz. Ölçüleri şimdi yazıyoruz, sonra değiştirmiyoruz. 3.6'daki tablo seçilim: hevesli kullanıcı her şeyi yapar. 'Quiz çözdürürsek döner' diyemeyiz; deneyip ölçeriz."

**Tony Şeyh** (kullanıcının kendi sözü): "Uygulama içinden müşteriden sıfır mesaj gelmiş; kanal görünmüyor demek. Yedi mağaza yorumunun hepsi olumlu; sevenler yazmış, gidenler yazmamış. Bir müşteri son yedi günde deftere 42 kez kelime ekleyememiş: duvara 42 kez vurup satın almamış biri. Altı müşteri bildirim ayarını kaydederken hata almış. Play yorumlarını ve destek e-postasını kimse okumamış; ekip başı okuyacak."

**Nassim Talip** (kırılganlık, eksilterek iyileştirme, küçük ve geri alınabilir deney): "Kırılgan olan uygulama değil, biziz. Tek Mac'te duran 60 commit; bir günde altı görev belgesi; üç kez dönen kararlar; tek seferde çıkacak dev bir sürüm. Önerim eksiltmek: sahte olabilecek yorumu çıkar, kutlama yığınını azalt, yeni sayfa ekleme. Ve bir kural: bir sürüm çıkana kadar o sürümün kararı yeniden açılmaz. Mehmet hariç; o zaman da editör doğrudan uygular, biz listeye yazarız."

## 3. Tartışılan dört konu
**a) Sürüm 1'e şimdi ne eklenir?** Don: bitiş ekranı düğmesi ve cümle çevirisi işareti. Sean: kilitli 3. hikâyede iki kapı. Steve ve Nassim: hiçbir şey; her ek bir gün daha demek. **Sonuç:** yalnız yayını durduran dört şey girer (aşağıda Y1–Y4). Cümle çevirisi işareti ve kilitteki iki kapı bir sonraki sürüme; 12 kişi dört hikâye bitirmiş, kilide varan az.

**b) İlk rütbe hızlansın mı (Mehmet'in isteği)?** Veri: 20 XP eşiği ilk hikâyede hemen herkese rütbe verir (159/163). Ama quiz çözenlerin üçte biri aynı anda ikinci rütbeye de atlar ve ilk bitişte kutlama sayısı üçe-dörde çıkar. İkinci rütbe "başlangıç bitince" gelsin isteniyorsa eşik 150 değil 300–350 olmalı. Dieter ve Don: önce kutlamalar tek ana indirgenir, sonra eşik değişir. Paul: Çaylak'a varanın ertesi gün dönüşü %35, varamayanın %10; ama o gün daha çok çalışmışlar, neden rütbe olmayabilir. **Sonuç:** Mehmet'in yönü geçerli; Sürüm 1'e girmez, bir sonraki sürümün ilk işi olur: eşikler 20 / 350 / (üçüncü veriyle), ilk bitişte tek kutlama.

**c) Dört hafta hiçbir şey eklememek (editörün önerisi) mi?** Mehmet ilerleme hissi istiyor; Nate iki haftanın ilk hikâye ve ertesi gün için yettiğini söylüyor. **Sonuç:** yayından sonra iki hafta ilk oturuma kod yok; yalnız hata, ölçüm ve içerik. Bu iki haftada sonraki sürümün taslakları ve verisi hazırlanır. İki hafta sonunda tek toplantı: ne çıkacağına veriyle karar.

**d) Kim neye karar verir?** Editörün 4., 10. ve 11. maddeleri. **Sonuç:** bölüm 6'daki kurallar.

## 4. Hedef
**Yeni gelen kullanıcı ilk gün iki hikâye bitirsin; ertesi gün dönsün ya da ödesin.**

Yayından sonraki ilk 250 yeni müşteride, uygulamanın kendi kayıtlarından:
| Ölçü | Bugün | Hedef |
|---|---|---|
| Bir hikâye bitiren | %54 | %65 |
| İki hikâye bitiren | %22 | %35 |
| Ertesi gün dönen | %21 | %28 |
| Satın almaya basıp tamamlamayanın nedeni | bilinmiyor | her biri kayıtlı |
| Bildirim izni ve ulaşma | bilinmiyor | biliniyor |
Satış sayısı hedef değil; bu hacimde iki haftada okunmaz. Adım oranları okunur.

## 5. Yol haritası (4 hafta, 5 iş)
| # | İş | Sahibi | "Bitti" ne demek | Ne zaman |
|---|---|---|---|---|
| 1 | **Sürüm 1'i yayınla.** Dalları uzak depoya gönder → `master`'ı birleştir, tam test → Y1–Y4 → sunucu yayını → merak cümleleri → TestFlight → bir gün kullanım → mağaza | Kent (editör) + Mehmet | Müşterilerin çoğu yeni sürümde; yeni olaylar canlı kayıtlarda görünüyor | 3 gün içinde TestFlight; hafta sonuna mağaza |
| 2 | **Ödeme yolunu doğrula.** Android'de gerçek satın alma; iOS'ta TestFlight'ta satın al ve iptal et | Mehmet + Sean | Android'de bir satın alma tamamlandı ya da hata bulundu | TestFlight günü |
| 3 | **Ölç ve dinle** (iki hafta). Haftalık tek tablo; ödeme yarım kalma nedenleri; bildirim izni ve ulaşma; Play yorumları ve destek e-postası; dönen kullanıcıya "bu uygulama olmasa ne kadar üzülürdün" sorusu | Nate, Tony, Sean, ekip başı | Rapordaki "bilinmiyor" satırlarının yarısı kapandı | Yayından sonraki 2 hafta |
| 4 | **İçerik.** 12 başlangıç metninin anlam denetimi (çeviri işinde önce bunlar); başlangıçlar kısadan uzuna; her seviye için yolculuk zinciri; A1 için yeni metin planı | Paul + editör (tur04) | 12 metin elle düzeltilmiş; zincir yazılı | 2 hafta |
| 5 | **Sonraki sürümün hazırlığı (kod yok).** İlk rütbe hızlı + tek kutlama; cümle çevirisinin işareti; hikâye bitince kelime tekrarı ve günün quizine çağrı; kilitte iki kapı. Taslak ve veri hazırlanır; hangisinin çıkacağı 2. hafta toplantısında | Don, Dieter, Sean | Taslaklar Mehmet'e gösterildi; karar verildi | 2. haftanın sonu |

**Yayını durduran dört şey (Y1–Y4), başka ek yok:**
- **Y1.** Birinci hikâyenin bitişinde "Sıradaki hikâye" düğmesi SE 3'te kaydırmadan görünür ("Paylaş" ilk ekrandan iner, kart kısalır). İkinci bitişte iki kapı birlikte görünür.
- **Y2.** A1'deki iki küçük düzen hatası (teklifte yarım satır; büyük yazıda "Paylaş").
- **Y3.** Onboarding'deki "Elif K., doğrulanmış kullanıcı" yorumu: gerçekse kalır; değilse gerçek bir App Store yorumuyla değiştirilir ya da ekran kalkar. Mehmet söyler.
- **Y4.** Birleşmiş sunucunun tam testi ve eski sürümle (1.0.2) bir sürüş.

## 6. Durdurulan işler
| İş | Durum |
|---|---|
| Yeni "Senin Yolculuğun" sayfası (harita) | 2. hafta toplantısına kadar yalnız taslak |
| Günde iki bildirim düzeni | İzin ve ulaşma verisi gelene kadar kapalı |
| Kelime balonu A/B | Kapandı: Mehmet "tasarım aynı kalsın" dedi |
| Rütbe adları | Kapandı: değişmez |
| Kariyer ve okuma yolculuğunun adı, birleşmesi, ayrılması | 2. hafta toplantısına kadar yeni tartışma yok |
| Anlam motorunun kalanları, boşluk doldurma soruları, kampanyalar | Kapalı; ilgi zamiri dalı yayından sonra birleşir ya da silinir (Kent) |
| Okuma değerlendirmesi ve sertifika | 176 soru okunmadan öne çıkarılmaz; müşteride görünüp görünmediği doğrulanır (editör) |
| Instagram'dan uygulamaya yeni çağrı | Sürüm 1 mağazada olana kadar bekler |

## 7. Çalışma kuralları (editörün 6.2 bölümüne cevap)
1. **Tek görev kaynağı:** `ortak/guncel_is_listesi.md`. Ekip görevi yalnız oraya yazar; günde en çok bir kez, akşam günceller. Raporlar gerekçe içindir, görev tanımlamaz.
2. **Mehmet'in editöre doğrudan sözü her şeyin üstündedir** ve taslak gerektirmez. Editör uygular, listeye bir satır not düşer; ekip listeyi ona göre düzeltir.
3. **Ekibin yazdığı görev, listede duruyorsa sorulmadan uygulanır.** Mehmet'e yalnız şunlar sorulur: canlıya yazma, sunucu ve mağaza yayını, fiyat, silme.
4. **Taslak kuralı** yalnız ekipten gelen ve var olan bir ekranın görünümünü değiştiren işler içindir.
5. **Bir sürümün kararı o sürüm çıkana kadar yeniden açılmaz.** Yeni fikir "sonraki sürüm" başlığına yazılır.
6. **Ekran görüntüsü:** her değişiklikte değil, sürüm adayı başına bir tam sürüş (SE 3 + büyük yazı).
7. **Derleme numarası:** editör sıradaki boş numarayı kendisi verir.
8. **Özellik dallarını uzak depoya gönderme:** ekip öneriyor (ana dal ve canlı hariç, sormadan). İzin Mehmet'in.

## 8. İtirazlar (kayda geçti)
- **Nassim:** Sürüm hâlâ tek parça ve büyük. Onboarding teklifinin sunucudan kapatılabilmesi iyi; aynı anahtarın yolculuk kartı için de olması gerekirdi. Yayından sonraki ilk 48 saat çökme paneli ve ilk hikâyeye başlama oranı (%79) her gün okunur; düşerse teklif kapatılır.
- **Sean:** Kilitteki iki kapının ertelenmesi satış kaybı olabilir; kilide varan sayısı artarsa öne alınır.
- **Paul:** B1 başlangıcı uzun metinlerle açılıyor; yayını durdurmaz ama ilk hafta B1 seçenlerin bitirme oranı ayrı okunur.
- **Don:** Cümle çevirisi işareti bu ürünün en ucuz kazancı olabilir; sonraki sürümde ilk sıraya yazılmasını istiyorum.
