# Mehmet'in cihaz testi – ekip kararları

**Tarih:** 18 Kasım 2026 · Tek geçiş; üyeler kurgusaldır. **Dayanak:** `raporlar/2026-11-18_mehmet_cihaz_geri_bildirimi.md`. Editörün önerdiği sıra onaylandı; aşağıdaki kararlarla başlanır.

## Ders (ekip için)
Harita sayfasının görünümü Mehmet görmeden değişti ve beğenilmedi. **Kural:** var olan bir ekranın görünümünü değiştiren iş, önce ekran taslağı (görüntü) olarak Mehmet'e gösterilir; kod sonra. Ürün kararı ekipte kalır, ama görsel sonuç görülmeden yayına girmez.

## Kararlar
| # | Konu | Karar |
|---|---|---|
| 1 | "Durak" kelimesi | **Kullanıcıya görünen her yerde "hikâye".** "Yolculuk" kalır. "Sıradaki hikâye", "Sıradaki hikâye yarın açılır", "Yolculuğunun ilk 4 hikâyesi", "Ücretsiz başla: günde bir hikâye", "Bütün hikâyeler açık, beklemek yok". Gerekçe (Paul): okur için sıcak, uygulama zaten bu kelimeyi kullanıyor; kurgu olmayan metinlere de bugün "hikâye" deniyor. Ekip belgelerinde "durak" iç terim olarak kalır. |
| 2 | Yolculuk (harita) sayfası | Bu sürümde **eski sayfa geri gelir.** "Eski düzen + kutularda kitap kapakları" sonraki sürüm; önce Dieter'in taslağı, Mehmet görür, sonra kod. Rütbe adlarını kaldırma kararı askıya alındı; taslakla birlikte yeniden bakılır. |
| 3 | Kapaklar | **Evet, iki yerde:** bitiş ekranı ve onboarding plan ekranı. Bitiş ekranı (Dieter): kapak solda küçük (yaklaşık 64×96), sağında "SIRADAKİ HİKÂYE · 3/4" ve ad; merak cümlesi altında tam genişlik, en çok 4 satır (cümle kesilmez; sığmıyorsa XP ve Paylaş satırı küçülür). Plan ekranı: dört kapak yatay sıra, altında adlar; ilkinde "Bugün". |
| 4 | Kelime balonu | **Ciddiye alındı, ayrı ve hemen sonraki küçük sürüm.** Bu pakete girmez (paket büyük; balon onboarding'i kilitleyen hatanın çıktığı yer). Şimdi: kod değiştirmeden ölçüm + 2 seçenek ekran taslağı. Yön (Don): ilk dokunuşta kelimenin hemen üstünde/altında tek satır anlam, metinle aynı yazı boyuna yakın; ayrıntı (diğer anlamlar, örnek, deftere ekle) ikinci dokunuşta. Balon sayfadaki hiçbir şeyi itmez. Mehmet taslağı görür, sonra kod. |
| 5 | Eski uygulama (1.0.2) | İstek metin kimliği taşımıyorsa **eski sayım** (yalnız sözlük dışı); taşıyorsa yeni sayım. 1.0.2'nin 402'yi düzgün karşıladığı doğrulanır. |
| 6 | Onboarding teklifi için sunucu anahtarı | **Evet.** Sunucudan açılıp kapanır; varsayılan açık. |
| 7 | "İlk gün 2 hak" | **Takvim günü kalır.** 23:50'de başlayan kullanıcı gece yarısından sonra yeni günün hakkıyla ikinci hikâyeyi yine açabilir; kayıp yok. |
| 8 | Onboarding teklifinin başlığı | Koşullu: deneme süresi biliniyorsa "Beklemeden oku: {n} gün ücretsiz", bilinmiyorsa "Beklemeden oku". |

## Sıra
Editörün önerdiği sıra geçerli (1 → 10). Balon ölçümü ve taslakları (8) diğer işlerle birlikte hazırlanabilir. Sunucu yayını, `NextHook` yazımı ve TestFlight Mehmet'te.

## İtirazlar
- **Nassim:** Kapak ve kelime değişikliği paketi yine büyütüyor; ama ikisi de aynı ekranlara tek geçişte giriyor, ayrı sürüm daha pahalı olurdu.
- **Paul:** Merak cümlelerinde "durak" geçmiyor; 4. cümlelerdeki "Başlangıç bitti. Sıradaki yolculuk…" ifadesi yeni kelimeyle uyumlu, değişmez.

## Ek (18 Kas 14:19): kariyer yolculuğu kalıyor
**Mehmet:** "Kariyer yolculuğu kalsa mı? Kullanıcılar ilerlemelerini görse."
**Karar:** Kalır; rütbe adlarını kaldırma kararı geri alındı.
- Veri (17 Kas, 243 müşteri): sayfayı %10 açmış, zararı da ölçülebilir faydası da görünmüyor. Sorun sayfanın kendisi değil, **görünmemesi**: ana sayfadan gelen açılış 0.
- Tek ilerleme, iki ölçek: **kariyer yolu = uzun yol** (seviye ve rütbe), **hikâyeler = o yolun adımları.** Kutuların içinde yolculuğun kitap kapakları; okunan işaretli, sıradaki belirgin, kilitli olan kilitli.
- Görünürlük: ana sayfa yolculuk kartı ve bitiş ekranındaki ilerleme çizgisi bu sayfaya açılır.
- Sıra değişmez: bu sürümde eski sayfa olduğu gibi; kapaklı tasarım sonraki sürüm, önce taslak Mehmet'e.
- Ölçüm: sayfanın açılışı (kaynağıyla) ve açılıştan sonra okumaya geçiş; 4 hafta sonra yeniden bakılır.

> **Güncelleme (18 Kas 15:55):** Bu ek ve rütbeyle ilgili sonraki ifadeler `raporlar/2026-11-18_yolculuk_sayfasi_toplantisi.md` kararıyla kesinleşti: tek sayfa, yol hikâyelerden, rütbe üstte unvan, rütbe mantığı değişmez.
