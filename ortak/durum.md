# Durum (tek doğru kaynak)

> Bu dosya uygulamanın o anki gerçek durumunu tutar. Her üye işe başlamadan önce burayı okur; bir şey değiştiğinde burada güncellenir.

## Uygulama
- Ad: **Daily English: İngilizce Oku**
- 2 yıldır geliştiriliyor; gamification sistemi var; Xcode'da (iOS) ve VS Code üzerinden sohbetle de geliştiriliyor.
- Backend: api.getdailyenglish.com (domain: getdailyenglish.com, elinde)
- Hesap sistemi var; XP kazanımı hesaba bağlı.
- Özellik: metin seslendirme — kullanıcı kitap okurken aynı anda dinleyebiliyor.
- Tanıtım görsellerinde/videolarında Mehmet'in kendi fotoğrafı yerine demo kullanıcı **"Sarah"** kullanılıyor.

## Mağaza durumu — ⚠️ UYGULAMA YAYINDA (6 Kas 2026 itibarıyla)
- **Android:** Google Play'de **canlı** (30 Eki 2026'da yayınlandı).
- **iOS:** App Store Connect'te yayınlandı, "Ready for Distribution" (31 Eki 2026).
- App Store: apps.apple.com/tr/app/daily-english-i-ngilizce-oku/id6795319092
- Play Store: play.google.com/store/apps/details?id=com.getdailyenglish.app
- **Beta/test aşaması bitti.** Aşağıdaki "test/beta" bölümü artık tarihsel — ekip buna göre çalışmayı bıraktı, gerçek kullanıcı/mağaza verisine geçti.

## Fiyatlandırma (4 Kas 2026 — güncellendi)
- Haftalık: 79 TL
- Aylık: 200 TL
- Yıllık: 999 TL'den başlayıp ~6 ay sonra 1.299 TL'ye çıkacak bir introductory offer kurulmuştu, ancak **Apple aynı üründe hem free trial hem introductory offer'a izin vermiyor** — bu yüzden eski sisteme (kaldırılan launch ürününü geri ekleyerek) dönüldü. Nate Gümüş: bu, abonelik ürün yapısında Apple politika kısıtı olduğu için not edilmeli, bir "hipotez" değil kesin bir platform kuralı.
- Abonelik altyapısı hazır.

## Ürün değişiklikleri (4 Kas 2026)
- **Leaderboard (sıralama tablosu) kaldırıldı.**
- Bunun yan etkisi: App Store yaş sınırı yanlışlıkla 13+ görünüyordu (leaderboard'un "Contests" anketi işaretlemesinden). Leaderboard kaldırılıp anket yeniden dolduruldu, yeni hesaplanan puan **4+**. Kent Bekçi notu: bu tür anket/yaş sınıflandırma hataları başka özelliklerde de olabilir — her yeni özellik eklenip kaldırıldığında App Store yaş anketi tekrar kontrol edilmeli.

## Test / beta (tarihsel — mağaza yayınından önceki döneme ait)
- Test başvuru sayfası: getdailyenglish.com/beta (artık öncelik değil, uygulama mağazada).
- İlk duyuru reeli (6 Eki 2026) tutmadı: izleyicinin yarısı 2. saniyede çıktı, ilk saatte başvuru gelmedi. Ders: uygulama ve haber ilk 2 saniyede görünmeli.
- **Lansman kararı (30 Eki 2026):** Lansman reeli uygulama yayınlanır yayınlanmaz paylaşılacaktı, deneme reeli yok; "A beautiful day to start" lansmanı carousel olarak (ilk slayt 8 yıl önceki ilk gönderinin orijinali, ikincide "8 yıl önce ilk bunu paylaşmıştım, şu an 3.030 gönderi var", sonra uygulamanın ilk günü). **Kontrol edilecek: bu lansman içeriği gerçekten yayınlandı mı — gunluk-ingilizce-ekip ile koordine edilmeli.**

## Kaynak kitle ve çapraz ekip koordinasyonu
- @gunluk_ingilizce Instagram hesabı (~140K+ takipçi) — birincil kazanım kanalı. İçerik tarafı `gunluk-ingilizce-ekip` reposunda yönetiliyor; bu ekip yalnızca linkten gelen trafiği/dönüşümü izler, içerik üretmez.
- Instagram ekibi tarafında (6 Kas 2026 itibarıyla bilinen): uygulama yayına girdiğinden beri sabit A2 seviye sistemi yerine değişken reel seviyelerine geçildi, öncelik daha fazla kullanıcıya ulaşmak ve uygulamayı daha iyi tanıtmak. Reel paragraf metinlerine karakter adı konmuyor.
- **Pazarlama, Instagram ekibiyle ortak yürütülüyor** (Mehmet'in kararı, 6 Kas 2026). İki ekip başı (Steve İşler ↔ Adam Koseri) düzenli koordinasyon toplantısı yapar — bkz. `raporlar/` altındaki ortak toplantı notları.

## Ekibin çalışma şekli (6 Kas 2026 — netleştirildi)
- **Ekip kod yazmaz.** Mehmet'in ihtiyacı: uygulama ihtiyaçlarının, tasarımların, ürün/iş kararlarının (ne yapılmalı, neden, hangi öncelikle) net tanımını çıkarmak.
- Kodun kendisi başka yerde (Mehmet'in kullandığı editördeki asistan) yazılır. Ekip bu kodu yazdırmak için gereken spesifikasyonu, kabul kriterlerini ve gerekçeyi hazırlar.
- Bu yüzden GitHub repo erişimi (Flutter/DailyEnglish private repoları) artık acil bir engel değil — derleme/test yapmamız gerekmiyor. Yine de uygulamayı daha iyi anlamak için kod tabanına salt-okunur erişim faydalı olurdu, ama zorunlu değil.
- Kent Bekçi'nin (geliştirme) rolü de buna göre: "nasıl kodlanır" değil, "ne kodlanmalı ve neden" — gerçek Kent Beck'in YAGNI/basitlik ilkesini spesifikasyon kalitesine uygular.

## Açık sorular / takip edilecekler
- push_opened ölçümü hâlâ kurulmadı (bkz. raporlar/2026-10-29_bildirim-psikoloji-plani.md, madde 1) — bu olmadan "bildirimler etkili mi" sorusu cevaplanamaz, öncelik bu.
- Kaynak etiketi standardı (Nate Gümüş ↔ Nate Gold, 6 Kas çapraz toplantıda kararlaştırıldı) — **spesifikasyon hazır** (bkz. `raporlar/2026-11-06_kaynak_etiketi_spesifikasyonu.md`), uygulama henüz yapılmadı. Özet: onboarding'de "nereden duydun" sorusu (her iki platform) + Android'de Play Install Referrer (doğrulama katmanı).
- PMF anketi (Sean Ellis çerçevesi) mevcut kullanıcılara hiç uygulanmadı — checkpoint'in (ortak/hedef.md) 4. maddesi.
- Akşam seri bildirimi kod değişikliği (29 Eki) hâlâ derlenmedi/test edilmedi — Mehmet'in Mac'inde kontrol beklemede.
- Gerçek kullanıcı verisi şu an elle (Play Console/App Store Connect'e tek tek bakarak) çekiliyor; sistemli/otomatik toplama henüz yok — Nate Gümüş'ün asıl işi bu.

~~Lansman reeli/carousel'inin gerçekten yayınlanıp yayınlanmadığı teyit edilmeli~~ — çözüldü (6 Kas, bkz. raporlar/2026-11-06_lansman_incelemesi.md).
~~Sayısal hedef yok~~ — çözüldü (6 Kas, checkpoint olarak ortak/hedef.md'de).

## Güncelleme günlüğü
- 2026-10-29: Dosya oluşturuldu, mevcut bilgiler Mehmet'in önceki konuşmalarından derlendi.
- 2026-11-06: Uygulama canlı — Android ve iOS yayında. Fiyatlandırma, leaderboard kaldırma, yaş sınırı düzeltmesi işlendi. Pazarlamanın Instagram ekibiyle ortak yürütüleceği not edildi.
- 2026-11-06: Ekibin çalışma şekli netleştirildi — ekip kod yazmaz, ihtiyaç/tasarım/gerekçe tanımlar; kod editörde yazılır.
