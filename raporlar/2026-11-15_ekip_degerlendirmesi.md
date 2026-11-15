# Ekip değerlendirmesi: uygulamada ışık var mı

> **DÜZELTME (15 Kas 2026, akşam):** Bu rapordaki Firebase sayıları uygulamanın kendi kayıtlarıyla uyuşmadı. Canlı veritabanına göre onboarding'i bitiren müşterilerin %81–85'i okumaya başlıyor (11–15 Kas: 34 kişiden 29; 29 Eki–10 Kas: 114 kişiden 92). "26 kişiden 18'i başlamadı" sayısı ve ona dayanan "en büyük kayıp onboarding ile ilk metin arasında" hipotezi **geçersizdir.** Bu rapordaki diğer Firebase sayıları da (okumayan 52 kişi, quize giriş, sonraki okumaya geçiş, paywall hunisi) aynı kaynaktan geldiği için doğrulanmış sayılmaz. Doğru sayılar: `raporlar/2026-11-15_editor_bolum1_ek.md`. Hata, tek ve yeni bir kaynağı (4 günlük Firebase verisi) uygulamanın kendi kayıtlarıyla karşılaştırmadan karara dayanak yapmaktı.


**Tarih:** 15 Kasım 2026 · Tek geçiş. Üyeler kurgusaldır; her görüş, üyenin el kitabındaki belgelenmiş çerçevenin eldeki gerçek veriye uygulanmasıdır, gerçek kişilerin görüşü değildir.
**Veri:** `raporlar/2026-11-15_ilk_analitik_okumasi.md`, `ortak/hedef.md` (15 Kas kayıtları).

- **Steve İşler (ürün, ekip başı):** Ürün okurken iyi; sorun insanların okumaya varmaması. Önümüzdeki iki hafta tek iş: yeni geleni ilk metne sokmak. Reklam, yeni özellik, yeni format bu sürede "hayır".
- **Don Normal (UX):** Onboarding bitince kullanıcı ana sayfada seçeneklerin önüne bırakılıyor; ne yapacağını gösteren tek bir net işaret yok. Seçimi kaldır, metnin içine al. Tooltip hatası aynı sınıf bir hata: tasarım kendi akışını bozuyor.
- **Sean Büyüt (büyüme):** Delik kovaya su taşınmaz. Yeni gelen 30 kişiden 9'u okuyor; bu düzelmeden trafik büyütmek (reklam dahil) parayı ve takipçiyi yakar. Sıra: aktivasyon, sonra metni bitiren kullanıcılara "artık kullanamasan ne hissederdin" anketi, en son trafik.
- **Nate Gümüş (veri):** 4 gün, 84 kullanıcı; bu bir hipotez (1/5), ders değil. Haftalık tek sayı izlenir: onboarding'i bitirenlerden okumaya başlayanların oranı (şu an 8/26). Platform ayrımı, günün quizi girişi ve ses dinleme ölçülmüyor; eklenmeli.
- **Kent Bekçi (geliştirme):** En küçük değişiklik yeter: onboarding sonunda ana sayfa yerine zaten seçilmiş ilk hikâyeyi aç. Yanına iki düzeltme: tooltip katmanı, Android satın alma akışının test hesabıyla denenmesi.
- **Tony Şeyh (destek):** Bu gece yazan kullanıcı, yazmadan giden çok kişiyi temsil eder. Ödeyen 3 kişiye ve deneme sonunda çıkan 1 kişiye birer kısa mesajla "neden" sorulmalı; beş kullanıcıyla konuşmak bu tablodan fazlasını söyler.
- **Nassim Talip (şüpheci):** "İçerik iyi" sonucu hayatta kalanlardan çıkıyor: metni bitirenleri görüyoruz, açıp beğenmeyeni değil. Veride Mehmet'in test cihazları olabilir. Asıl rahatsız edici soru yanıtsız: 142 bin takipçiden iki haftada ~240 indirme geldiyse bu kitle bir okuma uygulaması istiyor mu? Aktivasyon düzelse bile bu ayrıca sınanmalı.

**Ortak karar önerisi:** "Zaman kaybı" hükmü için erken. İki hafta tek hedef: aktivasyon (8/26'yı yükseltmek). Reklam ve yeni özellik bu sürede yok. İki hafta sonunda oran kıpırdamadıysa Nassim'in sorusu masaya gelir.
**Ayrışma:** Nassim talep sorusunun aktivasyonla aynı anda sınanmasını istiyor; Steve sırayla gidilmesini.
