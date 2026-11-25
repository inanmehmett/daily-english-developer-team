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

## Biten
(editör taşır: iş, tarih, rapor dosyası)
