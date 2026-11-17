# Ücretsiz sınır – gözden geçirme

**Tarih:** 17 Kasım 2026 · Tek geçiş; üyeler kurgusaldır. **Tetikleyen:** Mehmet: "hiç kullanmayanlar almış, kullananların hiçbiri almamış; bedavaya alışmak iyi değil."
**Onaylananlar (Mehmet, 17 Kas 18:16):** V8 geri alınır; paywall tetikleyicisi kaydedilir; plan görünürlüğü raporlanır.

## Bugünkü ücretsiz model (koddan, 17 Kas)
| Alan | Ücretsiz | Premium |
|---|---|---|
| Okuma | Başlangıç paketi (her zaman) + günde 1 açılış | Hepsi |
| Kelimeye dokunma (çeviri) | Günde 25 | Sınırsız |
| Deftere kelime ekleme | İlk 7 gün sınırsız, sonra toplam 15 | Sınırsız |
| Sesler | Temel | Premium sesler |
| Quiz ödülü | x1 | x2 |

Kodda tutarsızlık: Flutter `freemium_limits.dart` "7 günden sonra günde 3 okuma" diyor; backend erişimi başlangıç paketi + günlük açılışla veriyor. Hangisinin geçerli olduğu editörden istenecek.

## Okuma
- Kullananların ortanca davranışı (tamamlamayan 10 alıcı adayı): 1 metin, 11 dokunma. 25 dokunma sınırına, ilk 7 gün de deftere ekleme sınırına muhtemelen kimse çarpmıyor. Yani ilk hafta ücretsiz kullanıcı pratikte her şeye sahip; satın alma için bir neden doğmuyor. Mehmet'in teşhisiyle uyumlu.
- Düzeltme: "kullananların hiçbiri almadı" tam doğru değil. B, 2 gün 18 saat kullandıktan sonra aylık aldı. Ama 4'ün 3'ü kullanmadan aldı.
- Sayı küçük (4 alıcı): hipotez.

## Üyeler
- **Sean:** Sınır, kullanıcının ilk gün içinde hissedeceği yerde olmalı. En güçlü aday deftere ekleme: "ilk 7 gün sınırsız" kalksın, ilk günden toplam 15 olsun (veya daha az). Defter, tekrar ve quizle birleşince Premium'un asıl değeri.
- **Paul:** Dokunmayı çok kısarsanız A1/A2 okuyucu metni bitiremez; bitiremeyen geri gelmez (D1: hiç bitirmeyen 3/58, bir bitiren 19/53). Dokunma sınırı ancak veriyle ve dikkatle düşürülsün; bugünün durağında dokunma serbest kalabilir.
- **Don:** Sınıra çarpan kullanıcıya ne olacağı net olmalı: "Bugünlük 25 kelimen bitti, yarın yenilenir — ya da Premium ile sınırsız." Gizli kilit yok.
- **Nate:** Önce kaç kişinin hangi sınıra çarptığını görelim. Ayrıca V8 geri alma ile sınır değişikliği aynı sürümde çıkarsa hangisinin işe yaradığını ayıramayız; ya ayrı sürüm ya da tarihleri not edilerek.
- **Nassim:** Sınırı daraltmak satışı artırabilir ama tutmayı düşürebilir; asıl sorun hâlâ ilk gün kalmayanlar (%64 ≤1 gün). Ölçü olarak hem "satın alma / yeni kullanıcı" hem "ertesi gün dönüş" birlikte izlensin; biri düşerken diğeri artarsa geri alınır.

## Öneri (veri gelince kesinleşir)
1. Deftere ekleme: ilk 7 gün sınırsız kaldırılsın; ilk günden ücretsiz toplam sınır (15 veya daha az). Defter sınırı dolunca açık teklif.
2. Dokunma: günde 25 → daha düşük bir sayı, editör verisine göre (çoğunluğun ilk metni bitirebileceği yerde). Bugünün durağında dokunma sınırdan sayılmasın mı? Mehmet'e soru.
3. Okuma: değişmez (başlangıç + günde 1).
4. Premium sesler ve quiz x2 değişmez.
5. Geri alma kuralı: değişiklikten sonraki 2 haftada ertesi gün dönüş belirgin düşerse sınırlar eski hâline döner.

Veri isteği: `ortak/editor_gorevi_2026-11-17_ucretsiz_sinirlar.md`.
