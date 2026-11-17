# Editör görevi – ücretsiz sınırlar kime değiyor (salt okuma)

**Tarih:** 17 Kasım 2026 · **İsteyen:** Nate Gümüş, Sean Büyüt · **Kod/DB değişikliği yok.**
Canlı veritabanına önceki gibi salt okunur bağlan; yalnız `AccountKind='customer'`; e-posta/ad rapora girmez. Rapor: `raporlar/2026-11-17_ucretsiz_sinirlar_verisi.md`.

## Sorular
1. **Dokunma:** Müşterilerin günlük çeviri sayısı dağılımı (ortanca, %75, %90, en çok). Kaç kişi kaç gün 25 sınırına çarptı? Sınıra çarpan gün sonrası ne yaptı (paywall gördü mü, ertesi gün döndü mü)?
2. **İlk metin:** İlk metnini bitirenler o metinde kaç dokunma yaptı (ortanca, %75, %90)? Seviyeye göre ayır (A1/A2/B1+). Amaç: dokunma sınırı X olsaydı ilk metni bitirebilecek kullanıcı oranı (X = 10, 15, 20).
3. **Defter:** Müşterilerin kaydettiği kelime sayısı dağılımı. Kaç kişi 15'i geçti, kaçı 7. günden sonra sınıra çarptı? İlk gün kaç kelime kaydediliyor?
4. **Okuma kilidi:** Kaç müşteri kilitli bir metne/bölüme dokundu, kaçı günlük açılışını kullandı?
5. **Tutarsızlık:** Flutter `freemium_limits.dart` 7 günden sonra "günde 3 okuma" diyor; backend erişimi başlangıç paketi + günde 1 açılışla veriyor. Canlıda gerçekte hangisi uygulanıyor?
6. **Alıcılar:** 4 alıcı ve 10 tamamlamayan, satın alma öncesinde herhangi bir sınıra çarpmış mıydı?
