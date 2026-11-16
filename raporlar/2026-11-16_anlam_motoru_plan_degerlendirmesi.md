# Anlam motoru iyileştirme planı – ekip değerlendirmesi

**Tarih:** 16 Kasım 2026 · Tek geçiş; üyeler kurgusaldır. **Değerlendirilen:** editörün planı (1.000 premium vakada 224 hata; motorla ~70'i, sözlük editörlüğüyle ~142'si düzeltilebilir; bozmama kapısı + 6 adım).
**Bağlam:** `raporlar/2026-11-16_neden_kalmiyorlar.md` (kayıp ilk günde, ilk metnin içinde; dönüşle en çok birlikte görülen davranış ilk gün bir metni bitirmek), `raporlar/2026-11-15_paul_ulus_icerik_incelemesi.md` → "Düzeltme" (11 yanlış anlamın 10'u ölçüm hatasıydı).

## Üyeler
- **Kent Bekçi (geliştirme):** Yöntem sağlam. Bozmama kapısı (birim testi, sabit vaka kümeleri, kör değerlendirme, net kazanç, ücretsiz raftaki 495 karşılığın korunması) bu planın en değerli parçası; motor değişsin değişmesin kurulmalı. Her adım ayrı birleşsin ve tek başına geri alınabilsin.
- **Nate Gümüş (veri):** Plan "1.000 premium vakada %22 hata" ile ölçüyor. Kullanıcının hissettiği sayı bu değil: 482 gerçek dokunuştan kaçı yanlış, bunun kaçı ücretsiz rafta, kaçı premiumda? Önce bu verilmeli. İkincisi, dün içerik incelemesi kelimenin cümledeki yerini göndermeden ölçtüğü için 11 hatanın 10'unu yanlış saydı. Plandaki 1.000 vaka uygulamanın gerçek isteğiyle (kelime + cümle + kelime sırası) mi ölçüldü, doğrulanmalı. Üçüncüsü, kurallar aynı örneklemden çıkarıldı; tahmini kazanç ayrılmış bir sınama kümesinde ölçülmeli.
- **Paul Ulus (içerik):** Kalan hatanın en büyük payı (142 vaka) sözlük karşılığının kaba ya da eksik olması ve plan bunu takvime koymuyor. "Taşınmak, hareket etmek" tek karşılık, people → kişi gibi hatalar okuru en çok yanıltanlar. 5. adım (birincil anlam değişikliği) yalnız balonu değil, kelime defterine kaydedilmiş anlamları ve quiz cevaplarını da etkiler; o etki ayrıca ölçülmeli. Cümleye göre değişen kelimeler (left, stop, time) için dil modeliyle önceden seçim fikri doğru yön; şimdilik bekleyebilir.
- **Steve İşler (ürün):** Öncelik sorusu var. Kayıp ilk metinde: A2 ve B1 seçenlerin çoğuna düşen "Why Penguins Can't Fly" 63 okurun 23'ünde bitiyor. İlk metinler ücretsiz rafta ve oradaki anlamlar zaten elle doğrulanmış; bu plan o rafa bilerek dokunmuyor. Yani plan kalıcı ürün kalitesini artırır ama 29 Kasım sınavını ve ilk gün kaybını değiştirmez.
- **Sean Büyüt (büyüme/gelir):** Premium metinleri bugün 3 aktif abone okuyor. Abone sayısı büyümeden premium kalitesine 4–5 gün yatırmak, satışı artıracak bir kanıt olmadan yapılıyor. Kısmi onaydan yanayım.
- **Nassim Talip (şüpheci):** "Doğru oran ~%90'a çıkar" bir tahmin; aynı veriden kural türetip aynı veride ölçmek kazancı şişirir. Dün tek kaynaklı bir sayıyla karar verdik ve yanıldık; burada da kazanç ancak ayrılmış kümede ve gerçek dokunuşlarda görülürse sayılsın.
- **Don Normal / Dieter Koç:** Arayüz değişikliği yok; görüş yok.

## Karar önerisi (Steve İşler)
1. **Şimdi:** Adım 1 (bozmama kapısı) ve adım 2 (kural kelimeleri). Toplam ~1,5 gün. Kapıya iki ek: (a) ölçüm uygulamanın gerçek isteğiyle yapılsın, (b) ayrılmış bir sınama kümesi olsun.
2. **Adım 2'den önce bir sayı:** 482 gerçek dokunuştaki hata oranı, ücretsiz raf / premium ayrımıyla.
3. **Bekletilsin:** Adım 3, 4, 6 (küçük kazanç). Adım 5, kelime defteri ve quiz etkisi ölçülüp raporlandıktan sonra.
4. **Öncelik sırası:** Bu iş, ilk metin sorununun (A2 okuruna B1 metin düşmesi, "Penguins" %37 bitirme) önüne geçmesin. İlk metin işi ayrı bir görev olarak tanımlanmalı.
5. **Takvime alınmalı:** 142 vakalık sözlük editörlüğü; en çok dokunulan kelimelerden başlayarak.

## Ayrışma
Kent tüm planın sırayla yapılmasını istiyor (kapı kurulduktan sonra her adım ucuz). Sean ve Steve kısmi onaydan yana. Karar Mehmet'in.
