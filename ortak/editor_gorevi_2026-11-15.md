# Editör görevi – 15 Kasım 2026

Bu dosya, editördeki asistanın (uygulama kodunun ve çalışan uygulamanın olduğu oturum) yapacağı işleri tanımlar. Üç bölüm var; her bölüm ayrı bir sohbette çalıştırılabilir. **Her bölümün sonunda dur ve Mehmet'in onayını bekle.**

## Önce oku
1. `README.md` (ekip, kurallar; özellikle madde 9: davranışsal tasarım sınırları)
2. `ortak/durum.md`, `ortak/hedef.md`
3. `raporlar/2026-11-15_ilk_analitik_okumasi.md`, `raporlar/2026-11-15_kriz_toplantisi.md`, `raporlar/2026-11-15_ilk_okumaya_gecis_tasarimi.md`
4. Çalışacağın bölümdeki üyenin el kitabı (`uyeler/`)

## Genel kurallar
- Hangi üye rolünde çalıştığını her raporun başına yaz. Üyeler kurgusaldır; el kitabındaki çerçeveyi ve kontrol listesini uygula.
- Veri varken varsayımla konuşma: bulguyu ekran görüntüsü, dosya/satır ya da sayı ile göster. Doğrulayamadığını "doğrulanmadı" diye yaz.
- Onboarding'e yeni soru ya da yeni ekran ekleme.
- Mağazaya sürüm gönderme, mağaza ayarı değiştirme. Yayın kararı Mehmet'in.
- Kod değişikliklerini küçük, ayrı commit'lerle yap; her birinin ne ölçtüğünü/değiştirdiğini commit mesajına yaz.
- Raporları bu depoda `raporlar/` altına kaydet ve gönder. Ekran görüntüleri `raporlar/ekran_2026-11-15/` altına, küçültülmüş olarak.
- Rapor biçimi: en üstte 5 satırlık özet; sonra bulgular tablosu (bulgu · kanıt · önem: yüksek/orta/düşük · öneri); sonra "Bilinmeyenler" ve "İtirazlar".

---

## Bölüm 1 – Ekip kararlarının uygulanması (Kent Bekçi; tasarım için Don Normal)

**1a. Onboarding'den ilk okumaya geçiş.** Sorun: onboarding'i bitiren 26 kişiden 18'i ilk metne başlamadı (4 günlük veri). Tasarım önerisi `raporlar/2026-11-15_ilk_okumaya_gecis_tasarimi.md` içinde:
- Son onboarding ekranı (`step_14_trial_guide.dart`) kullanıcı için seçilen hikâyeyi göstersin (kapak, başlık, seviye, tahmini süre). Hikâye, ana sayfadaki "İlk okumana başla" kartının seçtiğiyle aynı olsun (`FirstReadCard.pickBook`).
- Ana düğme "İlk hikâyeni oku" olsun ve doğrudan okuyucuyu açsın; geri tuşu ana sayfaya dönsün. "Ücretsiz, kart gerekmez" bilgisi düğmenin altında küçük not olarak kalsın.
- Altında sessiz ikinci seçenek: "Önce uygulamaya göz atayım" → ana sayfa.
- Ana sayfadaki kart yerinde kalsın. Ertelenmiş paywall mantığına dokunma.
- **Sıra:** Don Normal rolünde önce mevcut son ekranın ve ana sayfanın (yeni kullanıcı) görüntüsünü al, öneriyi ekrana bakarak doğrula ya da düzelt, yeni ekranın taslak görüntüsünü Mehmet'e göster. Onaydan sonra Kent Bekçi rolünde uygula.
- **Ölçüm:** "Önce göz atayım" seçimi ve "İlk hikâyeni oku" dokunuşu için ayrı analitik olayı gönder.

**1b. Analitik eksikleri.**
- Günün quizi her başlatıldığında olay gönder (şu an yalnız ilk seferde `quiz_intro_shown` gidiyor).
- Ses dinleme: `sentence_listened` Firebase'e gitmiyor gibi görünüyor (`analytics_service.dart`, ~441. satırdaki küme). Doğrula; ses dinleme Firebase olay listesinde görünür olsun.
- `word_lookup` olayına metnin kimliğini, seviyesini ve metnin toplam kelime sayısını ekle (Paul Ulus'un "50 kelimede 1" ölçüsü için).
- Olaylarda platform ayrımının (iOS/Android) raporlanabildiğini doğrula.

**1c. Android satın alma.** Android'de 15 günde satış yok; analitikte 3 kullanıcı satın almayı başlatmış, 1'i tamamlamış. Android satın alma akışının kodunu ve hata kayıtlarını incele; bilinen bir hata var mı yaz. Mehmet'in test hesabıyla baştan sona deneyebilmesi için adım adım test tarifi hazırla. Kod değişikliği gerekiyorsa önce bulguyu raporla.

**1d. Tooltip düzeltmesi.** `e9130b9` ile yapıldı. Tooltip'in sayfa akışında yer kaplamayan bir katman olarak açıldığını ve "Devam" düğmesinin en büyük yazı boyutunda görünür kaldığını ekran görüntüsüyle doğrula.

**Bölüm sonu:** Yapılanları ve doğrulananları `raporlar/2026-11-15_editor_bolum1.md` olarak yaz, `ortak/durum.md`'deki ilgili açık maddeleri güncelle. Dur.

---

## Bölüm 2 – İçerik incelemesi (Paul Ulus) – yalnız okuma, kod değişikliği yok

Amaç: "Metinler mi, çeviriler mi, ses mi kötü" sorusuna ilk kanıtlı cevap. El kitabı: `uyeler/paul_ulus_icerik.md`.

- **Örneklem:** Her seviye için yeni kullanıcıya ilk önerilen metin (`FirstReadCard.pickBook`'un seçeceği) ve her zaman ücretsiz olan üç metin. Yetmezse seviye başına bir metin daha.
- **Her metin için:** kelime sayısı, ortalama cümle uzunluğu, seviyenin üstünde kalan kelimeler (liste), ilk paragraf okumaya devam ettiriyor mu, başlık ve açıklama Mehmet'in standartlarına uyuyor mu.
- **Çeviri:** metin başına 10 kelimenin dokununca gelen anlamı o cümledeki anlam mı; 5 cümle çevirisi doğal Türkçe mi. Yanlışları tek tek yaz.
- **Ses:** ses dosyaları var mı, metinle eşzamanlama verisi tutarlı mı. Dinleyemiyorsan bunu açıkça yaz; kaliteyi tahmin etme.
- **Quiz:** metin başına 5 soru; metinden cevaplanabiliyor mu, tek doğru cevap var mı. `quiz_question_reported` kayıtları varsa listele.
- **Rapor:** `raporlar/2026-11-15_paul_ulus_icerik_incelemesi.md`. En üstte: "içerikte kullanıcıyı kaçıracak düzeyde sorun var mı" sorusuna tek cümlelik cevap ve dayandığı örnek sayısı. Dur.

---

## Bölüm 3 – Arayüz taraması (Dieter Koç) – önce rapor, sonra iş

El kitabı ve kontrol listesi: `uyeler/dieter_koc_arayuz.md`.

**Aşama 1 – Tarama (kod değişikliği yok).**
- Uygulamayı sıfırdan kurulmuş gibi çalıştır. Kapsam: onboarding'in 17 ekranı, ana sayfa (yeni kullanıcı ve okumuş kullanıcı), keşfet, okuyucu (kelime tooltip'i, cümle çevirisi, ses çubuğu), metin bitiş ekranı, quiz, kelime defteri, profil, paywall, ayarlar.
- Her ekranı iki koşulda görüntüle: (a) desteklenen en küçük ekran + en büyük sistem yazı boyutu, (b) yaygın bir ekran + varsayılan yazı boyutu. Mümkünse hem iOS hem Android.
- Kontrol listesinin yedi maddesini her ekrana uygula. Animasyonlar için: hangi animasyon var, ne işe yarıyor, ne kadar sürüyor, kullanıcıyı bekletiyor mu.
- **Rapor:** `raporlar/2026-11-15_dieter_koc_arayuz_taramasi.md`. Bulguları öneme göre sırala; her bulguya ekran görüntüsü ve dosya/satır ekle. Sonunda "önerilen iş listesi" (her iş için tahmini büyüklük: küçük/orta/büyük). Dur ve Mehmet'in hangi işleri onayladığını bekle.

**Aşama 2 – Uygulama (yalnız onaylanan işler).**
- Önce "yüksek" önemdekiler. Her düzeltmeden sonra aynı iki koşulda yeniden görüntü al ve öncesi/sonrası olarak rapora ekle.
- Tutarlılık için ortak bileşen/tema dosyalarını kullan; ekran bazında tek tek yama yapma.
