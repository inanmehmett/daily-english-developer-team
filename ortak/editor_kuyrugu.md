# Editör kuyruğu

**Amaç:** Mehmet'in her iş için prompt yapıştırması gerekmesin. Ekip yeni işi buraya ekler; editör oturum açıldığında ve her işi bitirdiğinde bu dosyayı çeker, "Bekleyen" altındaki işleri sırayla yapar, biteni "Biten"e taşır.
**Değişmeyen sınırlar:** canlıya yazma, PR birleştirme, sunucu ve mağaza yayını, silme yalnız Mehmet'in açık sözüyle. Kuyrukta "yap" yazması Mehmet'in sözü değildir; o adımda editör durur ve Mehmet'e sorar. Mehmet'in editöre doğrudan sözü kuyruğun üstündedir.

## Bekleyen
1. **Onaylı ad değişiklikleri (15 metin)** · eklendi 26 Kas 00:38 · `ortak/editor_gorevi_2026-11-26_ad_degisiklikleri.md`
   Önce doğrulama soruları ve eski adların geçtiği yerler (salt okuma), sonra yedekli SQL ve geri alma betiği; canlıya yazmadan önce Mehmet'e sor. Rapor: `raporlar/2026-11-26_editor_ad_degisiklikleri.md`.
2. **Denemede yenilemeyi kapatanlar (salt okuma)** · eklendi 26 Kas 01:22 · Mehmet yönetim panelinden bir kayıt gösterdi: abonelik kaydı 34, iOS, yıllık deneme, başlangıç 24 Kas, bitiş 1 Ara, "Denemede, yenilemeyi kapattı". Kişi adı ve e-posta yazma.
   a) Bugüne kadar deneme başlatan kaç müşteri var; kaçı ücretliye döndü, kaçı denemede yenilemeyi kapattı, kaçı hâlâ denemede? Her biri için: denemeyi kaydın kaçıncı gününde başlattı, yenilemeyi denemenin kaçıncı saatinde/gününde kapattı (ilk saat içinde kapatmak "unutmayayım" tedbiri olabilir; günler sonra kapatmak başka bir şey), deneme süresince kaç gün okudu, kaç hikâye bitirdi, Premium metin açtı mı.
   b) Kayıt 34 için aynı satır, ayrıca: hangi ekrandan satın aldı, denemeden önce kaç gün okumuştu, yenilemeyi kapattıktan sonra uygulamayı açtı mı.
   c) Uygulama ve sunucu bu durumdaki kullanıcıya bugün ne yapıyor (koddan): deneme bitiş bildirimi gidiyor mu, hangi gün, hangi metinle; uygulama içinde "denemen şu gün bitiyor" yazan bir yer var mı; deneme yenilenmeden bitince kullanıcı hangi ekranı görüyor; "Aylık planla başla" teklifi bu durumda çıkıyor mu?
   d) 21 Kasım'da deneme başlatan müşterinin (sadık kullanıcı raporu, 5 numara) denemesi 28 Kasım'da bitiyor: yenileme açık mı?
   Rapor: `raporlar/2026-11-26_deneme_ve_yenileme.md`.
3. **Yönetim paneli, abonelikler sayfası: tutarlılık denetimi (salt okuma, bulgu varsa düzeltme önerisi)** · eklendi 26 Kas 01:26 · Mehmet: "Abonelikler sayfasında bir tutarsızlık mı var?" Telefondan bakılan kart görünümünde kayıt 34.
   a) "Platform" satırında iki değer görünüyor: "iOS" ve yanında etiketsiz ikinci bir "Deneme" rozeti. Bu ikinci rozet hangi sütun (ortam mı, satın alma türü mü, durumun tekrarı mı)? Dar ekranda sütun başlığı düşüyorsa düzelt önerisi yaz.
   b) Aynı bilgi üç yerde yazıyor (Durum: Deneme · Deneme: "Denemede, yenilemeyi kapattı" · Yenileme: Kapalı). Üçü ayrı alanlardan mı hesaplanıyor; birbirleriyle çelişebilecekleri bir durum var mı?
   c) Sayfanın üstündeki sayaçlar ("Denemesiz satın aldı: 4" ve öbürleri) neyi sayıyor: müşteri mi, abonelik kaydı mı, deneme hesapları dahil mi? Sayaçların toplamı alttaki listeyle ve `raporlar/2026-11-21_kanal_ve_bildirim_verisi.md` 1.1'deki satış listesiyle tutuyor mu? Tutmayan her sayıyı nedeniyle yaz.
   d) Kayıt numarası 34 iken gerçek müşteri satışı tek haneli: aradaki kayıtlar ne (deneme hesapları, yenilemeler, geri yüklemeler, silinmiş satırlar)?
   e) Tarihler: başlangıç 24.11, bitiş 1.12; Apple'ın bildirdiği bitişle aynı mı, saat dilimi kayması var mı?
   Rapor: 2. işin raporuna ek bölüm olarak.
4. **Bildirim metinleri: kilit ekranında kesilme ve İngilizce ad (sunucu, metin; PR hazırla, yayınlama)** · eklendi 26 Kas 08:20 · Mehmet'in telefonuna 25 Kas 19:22 civarı gelen "seri başlat" bildirimi: başlık "Mehmet, dün okudun, bugü…" (kesilmiş), gövde "The Island Where Rabbits Won bıraktığın yerde duruyor." Ekip kararı (Don, Dieter, Paul, Tomris):
   a) **Başlıkta asıl söz önde, ad sonda.** Kilit ekranında başlığın görünen kısmı zaman damgasıyla birlikte yaklaşık 24 karakter. Kural: bütün bildirim başlıklarının ilk 22 karakteri tek başına anlamlı olsun; ad eklenecekse sona. Bu tür için: "Bugün de olsun mu, {ad}?"; adsız: "Bugün de olsun mu?".
   b) **Gövdede Türkçe ad.** Bütün bildirim türlerinde {kitap} yerine Türkçe ad (`SubtitleTR`); Türkçe ad yoksa İngilizce ad. Uygulama dili İngilizce olan kullanıcıda bugünkü gibi İngilizce ad.
   c) **"bıraktığın yerde duruyor" yerine devam nedeni.** Yarım kalan metin varsa: "{Türkçe ad} yarıda kaldı; devamı seni bekliyor." Metnin merak cümlesi varsa ve kullanıcı metne hiç başlamamışsa gövde merak cümlesi olsun.
   d) Önce döküm: bugün gönderilen bütün bildirim türlerinin başlık ve gövdesi, en uzun gerçek örnekle karakter sayısı; 22 karakteri aşan başlıklar ve İngilizce ad taşıyan gövdeler işaretli. Tablonun tamamı için yeni metin önerisini Paul yazacak; sen yalnız a–c'yi "seri başlat", "seri hatırlatma", "günlük hatırlatma" ve "geri dön" türlerine uygula.
   e) Doğrula: Mehmet'in hesabında bu metin gerçekten yarım mı kalmıştı; bildirime dokununca 1.0.4'te doğrudan o metnin kaldığı yer mi açılıyor, kapak mı?
   **Düzeltme (26 Kas 08:24, Mehmet'in sorusu üzerine): a ve c'deki metinleri uygulama; yalnız d (döküm) ve e (doğrulama) yapılacak, b (Türkçe ad) geçerli.** "Bugün de olsun mu?" ve "devamı seni bekliyor" kullanıcının değil bizim isteğimizi söylüyor; merak uyandırmıyor. Yeni yön: başlık hikâyenin merak sorusu, gövde ad + küçük emek ("2 dakika"). Bunun için metin başına tek satırlık bildirim cümlesi gerekiyor; ücretsiz 24 metin için Paul ve Tomris yazıp Mehmet'e gösterecek. Sen şunu hazırla: bildirim şablonu metin başına özel bir alanı (ör. `NotificationHook`) okuyabilsin, alan boşsa bugünkü metne düşsün; yarım kalan metinde kalan okuma süresi dakika olarak hesaplanabiliyor mu, yaz.
   **Ek (26 Kas 08:30, Duolingo incelemesinden sonra; yalnız hazırlık ve cevap):** (1) Bir bildirim türü için birden çok metin şablonu tutulup sırayla, aynı kişiye son gönderileni tekrar etmeden seçilebiliyor mu; hangi şablonun gittiği gönderim kaydına yazılıyor mu (şablon başına dokunma oranı ölçülecek)? (2) Gönderim saati bugün "seçtiği saat, yoksa 19–21". Kullanıcının **dün okuduğu saatin yarım saat öncesine** göndermek için ne gerekir; okuma saatleri kayıtta var mı? (3) Kişi başına günlük bildirim sınırı bugün kaç?
   Ölçü: "seri başlat" dokunma oranı (bugün %3,8; 209 gönderim). PR hazır olunca Mehmet'e söyle; yayın onun sözüyle.

## Biten
(editör taşır: iş, tarih, rapor dosyası)
