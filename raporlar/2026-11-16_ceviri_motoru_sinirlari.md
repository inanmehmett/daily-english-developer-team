# Çeviri motoru: neyi düzeltebilir, neyi düzeltemez — 16 Kasım 2026

Hedef: dil modeli kullanmadan, yalnız motoru (kurallar, etiketleyici, sözlük önceliği) geliştirerek ulaşılabilecek en yüksek balon doğruluğu. Taban: premium metinlerden rastgele 1.000 vaka (önceki rapor: `2026-11-16_ceviri_dogruluk_olcumu.md`).

## Sonuç

| | Doğru | Yakın | Yanlış | Boş |
|---|---|---|---|---|
| Bugün | %77,6 | %13,5 | %7,2 | %1,7 |
| Yalnız motor kuralları ve etiketleyici | ~%81 | ~%12 | ~%5 | ~%1,5 |
| + sözlük önceliğinin düzeltilmesi | **~%83–84** | ~%12 | **~%4** | ~%1,5 |
| + sözlük karşılıklarının editörle düzeltilmesi (motor dışı) | ~%90 | — | ~%2 | ~%0,5 |

**Motorun tavanı yaklaşık %84 doğru, %4 yanlış.** Bunun üstü motorla değil, sözlüğün kendisiyle ya da bağlam seçimiyle gelir.

## Hataların dağılımı (224 doğru olmayan balon)

| Sınıf | Vaka | Yanlış | Motorla düzelir mi | Örnek |
|---|---|---|---|---|
| A. Kural kelimeleri | 34 | 16 | **Evet**, çoğu | that → "o"; like → "benzeri"; "the way" → yol; "one of"; "half past ten" |
| B. Tür (etiket) hatası | 6 | 6 | **Evet**, çoğu | "Flat nine" → düz (daire); "more long" → uzun süre |
| C. Aynı türde yanlış anlam, kelime çoğunlukla tek anlamda kullanılıyor | ~20 | ~6 | **Evet**, sözlük önceliğiyle | floor → "zemin, kat" (hep kat); slip → kayma (hep fiş); cabin → kulübe (gemide kamara) |
| D. Aynı türde yanlış anlam, anlam cümleye göre değişiyor | ~19 | ~6 | **Hayır** | left → ayrılmak / bırakmak; time → zaman / fırsat; stopped → durmak / durdurmak |
| E. Sözlük karşılığı kaba, birleşik ya da eksik | 142 | 31 | **Hayır**, editör işi | "taşınmak, hareket etmek"; people → kişi; old → "eski, yaşlı" |
| F. Kalıp ve özel isim | 13 | 7 | **Kısmen** | başlıkta "The Man Who Walked" isim sanıldı; "came up" hep "gündeme gelmek"; "Ninety-eight" çevrilmiyor |
| Boş balon | 17 | — | **Kısmen** | tireli sayılar evet; nadir kelimeler (baroque, arc) sözlük işi |

**Motorla düzelebilen** yaklaşık 70 vaka (A, B, C, F'nin bir kısmı, tireli sayılar). **Düzelemeyen** yaklaşık 160 vaka (D ve E).

## C ile D'yi nasıl ayırdım

Aynı türde yanlış anlam seçilen 37 kelimenin premium metinlerdeki bütün geçişleri (270) tek tek işaretlendi (Haiku, listeden seçim). Ardından her kelime için şu soruldu: sözlükte bu türün birincil anlamı değiştirilirse kaç geçiş düzelir, kaçı bozulur?

- **24 kelimede değişiklik net kazanç.** move: 18 geçişin 14'ünde "yer değiştirmek"; floor: 10'un 9'unda "kat"; slip: 6'nın 6'sında "fiş"; cabin: 3'te 3 "kamara".
- **21 kelimede değişiklik kazandırmıyor.** stop, leave, look, turn, follow: anlam cümleye göre değişiyor. Motor bunları kuralla ayıramaz.
- **Sözlüğün anahtar kelimeleriyle bağlam seçimi** denendi. 42 balon değişti; 33'ü doğruydu ve bozuldu, yalnız 5 yanlış düzeldi. Bu yol kapalı.

**Sınır.** Birincil anlam yalnız 22 metindeki kullanımla seçilirse bütün katalogda yanlış olabilir. Değişiklikler 263 premium metnin tamamındaki kullanımla doğrulanmalı.

## Bozmama güvencesi

Her motor değişikliği şu kapıdan geçer; geçemeyen birleşmez.

1. **Kural testi.** Her kural için hem uyması gereken hem uymaması gereken cümlelerle birim testi. Örnek: "that night" → "o", ama "said that he…" → "…dığını".
2. **Fark taraması.** Dört sabit vaka kümesi her değişiklikten önce ve sonra canlı sözlüğe karşı salt okuma ile çözülür:
   - 9.511 vakalık katalog havuzu,
   - 1.000 premium vaka,
   - 482 gerçek dokunuş vakası,
   - 480 katalog vakası.
3. **Değişen her balon değerlendirilir.** Eski ve yeni karşılık, hangisinin hangisi olduğu bilinmeden değerlendiriciye verilir. Kötüleşen her vakayı elle okurum.
4. **Kabul ölçütü.**
   - Net kazanç pozitif olmalı.
   - Açıklanamayan kötüleşme olmamalı.
   - Ücretsiz rafın elle doğrulanmış 495 karşılığında değişiklik olmamalı.
5. **Rapor.** Her değişiklik "değişen balon sayısı / düzelen / bozulan / sonuç oranı" satırıyla kayda geçer.

Fark taraması bugün yaklaşık 2 saat sürüyor (9.511 vaka). Hızlı tur için değerlendirilmiş 1.962 vaka yeterli; tam tarama birleşmeden önce.

## Önerilen sıra

| # | İş | Tahmini kazanç (1.000 vakada) | Emek |
|---|---|---|---|
| 1 | Fark kapısını kurmak (yukarıdaki 2–4) | — | yarım gün |
| 2 | Kural kelimeleri: that, like, the way, one of, saat ifadeleri, tireli sayılar | +25–30 doğru, −14 yanlış | 1 gün |
| 3 | Etiketleyici düzeltmeleri: belirleyici ve sayıdan sonra isim ("the flat", "Flat nine"); "more + sıfat" | +4–5 | yarım gün |
| 4 | Başlıkta sahte özel isim; çevrilmeyen sayılar | +3–4 | yarım gün |
| 5 | Sözlük önceliği: bütün premium katalogdaki kullanıma göre, net kazancı ölçülen kelimelerde birincil anlamı değiştirmek | +15–20 | 1–2 gün (ölçüm dahil) |
| 6 | Kalıp anlamı: kalıp kayıtlarında birincil anlamı aynı yöntemle düzeltmek ("come up") | +3–5 | yarım gün |

Toplam: doğru %77,6 → yaklaşık %83–84; yanlış %7,2 → yaklaşık %4.

**Motor dışında kalanlar:**
- E sınıfı: sözlük karşılıklarının yalınlaştırılması ve eksik anlamlar; editör işi, en büyük kalan pay.
- D sınıfı: cümleye göre anlam seçimi; dil modeliyle önceden seçim (önceki rapor).
