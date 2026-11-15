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
- **[Kodda düzeltildi, 15 Kas: `e9130b9`, sürüm 1.0.4 (47) hazırlandı; mağazalarda yayınlandığı doğrulanmadı]** Onboarding 1. ekranda kullanıcı takılıyor (15 Kas, gerçek kullanıcı bildirimi, Reeder S19 Pro Max)** — "Bilmediğin kelimeye dokun" adımında (`step_01_tap_word.dart`) içerik kaydırılamıyor; telefon yazı boyutu büyükse kelime kartı ekrana sığmıyor ve "Devam" düğmesi ekranın altında kalıp basılamıyor. Diğer bazı adımlarda kaydırma var, bunda yok. Düzeltme isteği: içerik kaydırılabilir olsun, "Devam" düğmesi altta sabit kalsın; kaydırması olmayan diğer onboarding adımları (00, 06, 08, review_proof, progress_promise) da büyük yazı boyutuyla denensin. İlk ekran olduğu için öncelik yüksek. Kullanıcının netleştirmesi: düğme kelimeye dokununca görünüyor, "Deftere ekle"ye basınca kayboluyor ("✓ Defterde" etiketi genişleyip anlam metnini daha çok satıra bölüyor, kart uzuyor).
  - **Doğrulama (15 Kas, editör):** iOS simülatöründe varsayılan ve en büyük sistem yazı boyutunda tooltip sayfayı itmiyor, "Devam" görünür kalıyor (görüntüler `raporlar/ekran_2026-11-15/1d_*`). Küçük ekran yalnız otomatik testle doğrulandı; Android cihazda denenmedi.
- **[Mehmet onayladı, 15 Kas; bekleme anı düzeltildi; `main`'e alınması ekran doğrulamasını bekliyor]** **Onboarding'den ilk okumaya geçiş: taslak hazır, Mehmet'in onayını bekliyor (15 Kas)** — son ekran seçilen hikâyeyi gösteriyor, "İlk hikâyeni oku" okuyucuyu doğrudan açıyor. Flutter dalı `feat/onboarding-first-story` (yerel, `main`'e girmedi). Üç karar noktası ve görüntüler: `raporlar/2026-11-15_editor_bolum1.md` → 1a.
- **Analitik eksikleri kodda kapandı, sürüm bekliyor (15 Kas)** — `daily_quiz_started`, `practice_quiz_started`, `audio_listened`; `word_lookup`'a metin kimliği, seviye ve kelime sayısı. Flutter dalı `feat/editor-bolum1` (yerel). Google Analytics'te özel tanımlar Mehmet tarafından açılacak.
- **Sınav taban sayısı yanlış çıktı (15 Kas, canlı veriyle doğrulandı)** — Firebase "26 bitirenden 18'i okumaya başlamadı" diyordu; uygulamanın kendi kayıtlarında onboarding'i bitiren müşterilerin %81–85'i okumaya başlıyor (11–15 Kas: 29/34; 29 Eki–10 Kas: 92/114; olaysız 19 müşteri en kötü durumda sayılırsa %72). Kriz toplantısının 1. kararının hedefi ("oranı ikiye katla") yeniden yazılmalı; 29 Kasım'da sayı uygulamanın kendi kayıtlarından okunmalı. Ayrıntı: `raporlar/2026-11-15_editor_bolum1_ek.md`.
- **[Kodda düzeltildi, Android emülatöründe doğrulandı; iOS doğrulaması ve `main` bekliyor]** **En büyük sistem yazı boyutunda ana sayfa ve okuyucu bozuluyor (15 Kas)** — kart ekranın altına düşüyor, sekme etiketleri kesiliyor; okuyucuda 4 sayfalık metin 43 sayfa oluyor. Bölüm 3'ün (Dieter Koç) işi; görüntüler `raporlar/ekran_2026-11-15/yan_*`.
- **Geliştirme Mac'inin diski (15 Kas)** — yer açıldı (yaklaşık 16 GB boş). Yan etki: iOS 26.1 simülatör platformu yanlışlıkla silindi, yeniden indiriliyor; indirme bitene kadar iOS derlemesi çalışmaz.
- **iOS'ta iptal edilen deneme (15 Kas, canlı veri)** — kullanıcı hesabı açıldıktan 35 sn sonra, hiçbir şey okumadan denemeyi başlatmış; bir daha uygulamayı açmamış; son gün yenilemeyi kapatmış.
- **Veriden çıkan, sahibi belli olmayan üç iş (15 Kas)** — yeni müşterilerin ~%76'sına ilk iki dakikada Premium şeridi kaydı düşüyor; Apple/Google abonelik bildirimleri sunucuda hiç kaydedilmemiş; onboarding'i yarıda bırakanları sayan sayaç hesap açılmadan önceki ekranları saymıyor. Ayrıntı ek raporda (V8, V9, V12).
- **Kapalı test kanalı hâlâ etkin (15 Kas)** — eski testçiler mağazada "(Beta)" görüyor, bir kullanıcıda "Yükle" düğmesi çıkmadı. Kanalı duraklatma kararı Mehmet'te.
- **Android'de 15 günde satış yok, iOS'ta var (15 Kas)** — Android satın alma akışı test hesabıyla denenmeli. **Kod incelendi (15 Kas, editör):** kesinleşmiş hata yok, üç risk var (açılışta mağaza bağlantısı kurulamazsa oturum boyunca satın alma başlamıyor; ödeme sonrası doğrulama düşerse Android'de kendiliğinden yeniden denenmiyor; sunucu Play anahtarının varlığını denetlemiyor). Hata kayıtları okunamadı. Adım adım test tarifi: `raporlar/2026-11-15_editor_bolum1.md` → 1c. Test Mehmet'te. **Canlı veri (15 Kas):** Android'de test satın alması çalışıyor (son: 1 Kas); gerçek müşterilerden yalnız 2'si satın almaya basmış, ödeme yapmadan çıkmış (iOS: 10 basan, 4 tamamlayan). Başarısız ödeme kaydı yok; iptal/hata kaydı eksikti, kodda eklendi.
- **[11 Kas'tan beri veri akıyor, bkz. `raporlar/2026-11-15_ilk_analitik_okumasi.md`]** **Firebase Analytics hiç veri toplamıyor (6 Kas, yeni bulgu)** — `push_opened` dahil her şey (screen_view, session_start) son 28 günde 0. Kod (backend + Flutter) zaten doğru yazılmış; sorun veri akışında. Ayrıntı: `raporlar/2026-11-06_tutma_bulgulari.md`. Bu, debug işi — ekip spesifikasyon üretemez, Mehmet/editör uygulamayı debug modunda çalıştırmalı.
- Kaynak etiketi standardı (Nate Gümüş ↔ Nate Gold, 6 Kas çapraz toplantıda kararlaştırıldı) — **spesifikasyon hazır** (bkz. `raporlar/2026-11-06_kaynak_etiketi_spesifikasyonu.md`), yalnızca Android (Play Referrer), onboarding'e dokunmuyor. Uygulama henüz yapılmadı. iOS tarafı çözümsüz kaldı.
- PMF anketi (Sean Ellis çerçevesi) mevcut kullanıcılara hiç uygulanmadı — checkpoint'in (ortak/hedef.md) 4. maddesi.
- Akşam seri bildirimi kodu (`UsesEveningHour`) **zaten commit'li** (`1c31040`) — varsayıldığı gibi "uncommitted" değilmiş. Derlendiği doğrulanamadı: bu bulut ortamında NuGet erişimi yok (ağ kısıtı), Mehmet'in Mac'inde `dotnet build` ile 2 dakikalık doğrulama bekliyor.
- Gerçek kullanıcı verisi şu an elle (Play Console/App Store Connect'e tek tek bakarak) çekiliyor; sistemli/otomatik toplama henüz yok — Nate Gümüş'ün asıl işi bu.

~~Lansman reeli/carousel'inin gerçekten yayınlanıp yayınlanmadığı teyit edilmeli~~ — çözüldü (6 Kas, bkz. raporlar/2026-11-06_lansman_incelemesi.md).
~~Sayısal hedef yok~~ — çözüldü (6 Kas, checkpoint olarak ortak/hedef.md'de).

## Güncelleme günlüğü
- 2026-10-29: Dosya oluşturuldu, mevcut bilgiler Mehmet'in önceki konuşmalarından derlendi.
- 2026-11-06: Uygulama canlı — Android ve iOS yayında. Fiyatlandırma, leaderboard kaldırma, yaş sınırı düzeltmesi işlendi. Pazarlamanın Instagram ekibiyle ortak yürütüleceği not edildi.
- 2026-11-06: Ekibin çalışma şekli netleştirildi — ekip kod yazmaz, ihtiyaç/tasarım/gerekçe tanımlar; kod editörde yazılır.
- 2026-11-15: Editör Bölüm 1 raporu işlendi (`raporlar/2026-11-15_editor_bolum1.md`): tooltip doğrulandı, ilk okumaya geçiş taslağı onay bekliyor, analitik eksikleri kodda, Android satın alma test tarifi hazır.
- 2026-11-15 (öğleden sonra): Editör ek raporu işlendi (`raporlar/2026-11-15_editor_bolum1_ek.md`): canlı veriyle taban sayı, Android satın alma ve iOS denemesi netleşti.
- 2026-11-15 (akşamüstü): Mehmet bu turdaki kararları ekibe bıraktı; kararlar ek raporda ("Ekip kararları"). Android emülatöründe tooltip, yeni son ekran ve yazı tavanı doğrulandı.
