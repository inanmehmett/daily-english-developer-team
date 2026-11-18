# Editör görevi – genel durum raporu (yol haritası toplantısı için)

**Tarih:** 18 Kasım 2026 · **İsteyen:** Mehmet ve bütün ekip · **Amaç:** Ekip bu raporu okuyup toplanacak ve yol haritasını belirleyecek. Rapor, ekibin uygulamayı senin gördüğün kadar iyi tanımasını sağlamalı.
**Kurallar:** Kod ve veritabanı değişikliği yok. Canlıya önceki gibi salt okunur bağlan; yalnız `AccountKind='customer'`; kişisel bilgi yok. Önceki raporlarda olan sayıyı yeniden hesaplama, raporun adını ver; yalnız eksik olanı sorgula. Bilmediğin yere "bilinmiyor" yaz, tahmin yazma. Sürüm 1'in kalan işleri bu rapordan önce gelmez; rapor önce.
**Rapor:** `raporlar/2026-11-1X_genel_durum.md`, görüntüler `raporlar/ekran_genel/`.

## 1. Ne canlıda, ne bekliyor (Kent, Steve)
- Müşterilerin kullandığı sürümler (sürüm başına kişi), canlı sunucunun sürümü.
- Dallar: hangi dalda ne var, hangisi birleşmedi, hangisi yayına hazır; sırası.
- `ortak/guncel_is_listesi.md` A bölümündeki her madde: bitti / yarım / başlanmadı.
- **Yarım kalmış bütün işler** (yalnız Sürüm 1 değil): çeviri işi, anlam motoru, ölçüm olayları, kapalı duran özellikler, dalda bekleyen kodlar. Her biri için: ne durumda, bitmesi için ne gerek, kabaca büyüklüğü (küçük/orta/büyük).
- Kırılgan gördüğün yerler: son iki haftada en çok hata çıkan dosya ve akışlar; çökme panelindeki ilk beş kayıt.

## 2. Uygulama turu (Don, Dieter – ekip ekranları göremiyor)
Yeni bir kullanıcının gözünden, Sürüm 1 dalıyla, SE 3'te sırayla ekran görüntüsü ve her ekran için bir satır ("burada kullanıcı ne yapar, sonra nereye gider"):
onboarding'in her adımı → teklif → ana sayfa → kapak sayfası → okuyucu (balon, cümle çevirisi, dinleme) → bitiş → quiz → kelime defteri → kelime tekrarı → günün quizi → kariyer sayfası → profil → ayarlar → bildirim izni → kilitli içerik → sınır ekranları → paywall.
Ayrıca ikinci gün dönen kullanıcının ana sayfası ve yedinci gün ana sayfası (hangi kartlar çıkıyor).

## 3. Sayılar – tek sayfa (Nate, Sean)
Hepsi uygulamanın kendi kayıtlarından, bugüne kadar ve son 7 gün ayrı:
- Müşteri sayısı (platform, hafta); onboarding'i bitiren; ilk hikâyeye başlayan, bitiren; ikinci hikâyeyi bitiren; 1., 3., 7. gün dönen.
- Satış hunisi: paywall gören, satın al'a basan, alan; yüzeye ve platforma göre. Bugün etkin ödeyen abone, deneme durumunda olan, iptal eden.
- Özellik kullanımı (kullanan kişi ve kişi başı sıklık): kelimeye dokunma, cümle çevirisi, dinleme, deftere ekleme, kelime tekrarı, metin quizi, günün quizi, seri, kariyer sayfası.
- **Dönenleri dönmeyenlerden ayıran ne:** ilk gün yapılan hangi eylemler ertesi gün dönüşle birlikte görülüyor (önceki rapora ek olarak: quiz çözen, deftere ekleyen, dinleyen, bildirim izni veren).
- Bildirim: izin veren oranı (platforma göre), türe göre gönderilen ve açılan.
- XP ve rütbe: `ortak/editor_gorevi_2026-11-18_xp_ekonomisi.md` maddeleri (veri kısmı) bu rapora girer.

## 4. İçerik (Paul)
- Seviyeye göre etkin metin; kapak, ses, quiz, Türkçe açıklama, merak cümlesi eksikleri (sayı).
- Tanımlı yolculuklar ve her seviyede yolculuk yapılabilecek diziler/gruplar (ad, metin sayısı).
- En çok başlanan ve en çok yarıda bırakılan 10 metin (bitirme oranıyla).
- Çeviri kalitesinde bilinen açık sorunlar.

## 5. Destek ve geri bildirim (Tony)
- Uygulama içinden, e-postadan ya da mağaza yorumlarından gelen her şikâyet ve istek (özet, tarih); çözüldü mü.
- Hata kayıtlarında kullanıcının gördüğü en sık üç hata iletisi.

## 6. Senin görüşün (Nassim için)
- Kullanıcıya en çok zarar verdiğini düşündüğün beş şey (kanıtıyla).
- Ekipten gelen görevlerde seni yavaşlatan ya da çelişen talimatlar: açıkça yaz.
- Bir ay içinde tek bir şey yapabilseydik hangisi olurdu, neden.
