# Editör görevi – metin seviyeleri, testler, günün quizi, güncelleme düzeni (veri)

**Tarih:** 21 Kasım 2026 · **Dayanak:** `raporlar/2026-11-21_mehmet_notlari_degerlendirme.md` · Salt okuma; kod ve veritabanı değişikliği yok (küçük düzeltmeler iş listesinde ayrı). Canlıya salt okunur; yalnız müşteri hesapları; kişisel bilgi yok. Rapor: `raporlar/2026-11-2X_seviye_quiz_guncelleme_verisi.md`; metin dökümü `raporlar/veri_2026-11-21/` altına.

## 1. A1 ve A2 metinleri (denetimi ekip yapacak)
1. Etkin A1 ve A2 metinlerinin (84 metin) gövdeleri: metin başına bir dosya ya da tek dosya (kimlik, ad, seviye, kelime sayısı, dizi/bölüm, gövde). Depo özel; içerik bizim.
2. Metin başına kullanıcı verisi: başlayan, bitiren, bitirme oranı; 100 kelimede dokunma sayısı; bitirenlerde okuma hızı (kelime/dk); başlayanların seviye dağılımı.
3. 6 Eylül'deki katalog seviye ölçümü (`KatalogSeviyeOlcumu`) ve 15 Ekim'deki yeniden etiketleme (`RelabelTextLevels`) neye göre yapıldı; hangi metinlerin etiketi değişti.
4. Okuma hızında dokunup bakma süresi ayrıştırılabiliyor mu?

## 2. Seviye ölçümü ve seviye belgesi (Charles inceleyecek)
1. İki testin akışı, adım adım ve ekran görüntüsüyle (SE 3): "Seviyeni yeniden ölç" ve "Seviyeni belgele". Kullanıcı A1 iken ve B1 iken ilk üç soru ne oluyor?
2. Karar kuralları sade Türkçeyle: hangi cevaptan sonra hangi seviyeye gidiliyor, test ne zaman bitiyor, seviye hangi koşulda yazılıyor.
3. Her seviyeden 5'er soru örneği (iki testten de); 176 soruluk havuzun seviyeye ve soru türüne göre dağılımı.
4. 97 tamamlanmış ölçüm: sonuç seviyesi dağılımı; kullanıcının kendi seçtiği seviyeyle farkı (kaç kişi yukarı, kaç kişi aşağı, kaç basamak); yarıda bırakılan 10 ölçüm hangi adımda bırakılmış.
5. "Seviyeni belgele" satırı sunucudan gizlenebiliyor mu, yoksa uygulama değişikliği mi gerekiyor?

## 3. Günün quizi
1. Kelimeler nasıl seçiliyor (herkese aynı mı, seviyeye göre mi); çeldiriciler nasıl üretiliyor. "healthy" sorusunda "a" şıkkı nereden geldi; tek harfli ya da anlamsız şık kaç soruda var?
2. Skor dağılımı, kullanıcının seviyesine göre; ilk quizinde 5'in altında alanların ertesi gün dönüşü ile 5 ve üstü alanlarınki (az veri notuyla).
3. "Haftalık Şampiyon" rozeti hangi koşulda veriliyor; kaç kişiye, hangi skorlarla verilmiş.
4. Derleme 49'da Quiz sekmesindeki rozet hangi koşulda görünmeli; Mehmet'in telefonunda neden görünmedi?

## 4. Güncelleme düzeni
1. Müşterilerin sürüm dağılımı: son 7 günde uygulamayı açanlar ve bütün müşteriler ayrı ayrı.
2. Sunucudaki güncelleme ayarı (`MobileUpdateOptions`) ne yapabiliyor: öneri mi, zorunlu mu, ikisi de mi? Hangi uygulama sürümleri bu ayara uyuyor (denetim hangi derlemeden beri uygulamada)? Eski sürümde kullanıcı ne görüyor (ekran görüntüsü varsa)?
3. Kullanıcıyı kilitleyen bilinen bir hatası olan sürümler hangileri (ör. onboarding'deki ipucu hatası hangi derlemelerde vardı); o sürümlerde kaç müşteri kaldı?

## 5. Adlar ve açıklamalar (Mehmet, 21 Kas 00:44; inceleme ekipte)
Dayanak: `raporlar/2026-11-21_baslik_ve_aciklama_incelemesi.md`.
1. 287 etkin metnin tamamı için tek dosya (`raporlar/veri_2026-11-21/adlar_ve_aciklamalar.csv`): kimlik, İngilizce ad, Türkçe ad, **İngilizce açıklama**, **Türkçe açıklama**, tür, seviye, kelime sayısı, dizi ve bölüm, ücretsiz/günlük/Premium, başlangıç yolculuğunda mı, metnin ilk 80 kelimesi, merak cümlesi (varsa).
2. Kullanıcı bu alanları nerede görüyor: kartta, kapak sayfasında, yolculuk sayfasında hangi alan yazıyor (ekran görüntüsüyle birer örnek). Tür (kurgu / gerçek hikâye / efsane / klasik) kullanıcıya bir yerde gösteriliyor mu?
3. Sayılar: İngilizce açıklaması boş olan, Türkçe açıklaması boş olan, 40 karakterden kısa olan, aynı açıklamayı paylaşan metinler.
4. Dizilerde açıklama dizinin mi, bölümün mü? Bölüm kendi açıklamasını taşıyor mu?
