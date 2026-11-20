# Editör görevi – ilerleme verisi ("İngilizce Yolculuğun" planı için)

**Tarih:** 20 Kasım 2026 · **Dayanak:** `raporlar/2026-11-20_ingilizce_yolculugu_incelemesi.md` · **Öncelik:** derleme 49 işlerinden sonra; yayını geciktirmez.
Kod ve veritabanı değişikliği yok. Canlıya salt okunur bağlan; yalnız `AccountKind='customer'`; kişisel bilgi yok. Önceki raporlarda olan sayıyı yeniden hesaplama, raporu göster. Bilinmeyene "bilinmiyor" yaz. Rapor: `raporlar/2026-11-2X_ilerleme_verisi.md`.

## 1. Bugün ne tutuluyor (koddan)
- Sunucu, kullanıcı başına şunları tutuyor mu, nerede: okunan hikâye sayısı; **okunan kelime sayısı** (bitirilen hikâyelerin kelime toplamı olarak hesaplanabilir mi); okuma süresi; okuma yapılan gün sayısı; defterdeki kelime sayısı ve "öğrenildi" sayılanlar (tekrar düzeninde hangi aşama "öğrenildi" demek).
- Bu sayılar bugünkü müşteriler için geriye dönük hesaplanabilir mi, yoksa yalnız bundan sonrası mı?

## 2. Dağılım (müşteriler)
- Müşteri başına: bitirilen hikâye, okunan kelime, deftere eklenen ve öğrenilen kelime, okuma günü (ortanca, %75, %90, en çok).
- İlk hafta sonunda tipik bir "kalan" kullanıcı (7. gün dönen 4 kişi ve en az 3 gün okuyanlar) bu dört sayıda nerede.

## 3. Rütbe ve kutlama
- Rütbe atlayınca tam olarak ne oluyor: hangi ekran, hangi metin, nereye götürüyor; aynı anda başka hangi kutlamalar tetiklenebiliyor. Ekran görüntüsüyle.
- Önerilen eşikler (20 / 350; üçüncü için 800 ve 1.000 ayrı ayrı) uygulanırsa: yeni kullanıcı 1., 4., 7. gün sonunda hangi rütbede olur (tipik etkin kullanıcı için); bugünkü müşterilerin kaçı hangi rütbeye yükselir. İlk bitişteki kutlamaları tek ana indirmek için kodda neresi değişir (kabaca büyüklük).

## 4. Seviye altyapısı
- `LevelReadinessService`, seviye geçiş sınavı tabloları, yerleştirme ve "Seviyeni belgele" (okuma değerlendirmesi): her biri ne yapıyor, bugün müşteriye ne açık, ne kapalı, ne yarım.
- Bir kullanıcının seviyesi bugün hangi yollarla değişebiliyor; kaç müşterinin seviyesi kayıttan sonra değişmiş.
- Seviye başına etkin hikâye sayısı ve bir kullanıcının o seviyenin tamamını okuması için gereken yaklaşık süre (günde bir hikâyeyle).

## 5. Kariyer sayfası (1.0.4 canlıya çıktıktan bir hafta sonra, ek olarak)
- `career_opened` kaynağına göre (bitiş ekranı satırı, kişi kartı, kutlama); `journey_page_shown` kaynağına göre; yolculuk sayfasından kapak sayfasına ve okumaya geçiş oranları.

## 6. Senin görüşün
- Yol haritasındaki dört aşamadan hangisi en az kodla en çok şeyi değiştirir; hangisi göründüğünden pahalı.
