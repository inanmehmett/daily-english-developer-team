# Editör görevi: 21 Kasım toplu iş

**Veren:** ekip (Mehmet "editöre verelim" dedi, 21 Kas 12:09). **Dayanak:** `raporlar/2026-11-21_sadik_kullanicilar_ekip_karari.md`, `ortak/guncel_is_listesi.md`.
**Sıra önemli.** 1.0.4'ü geciktirecek hiçbir şey yok: A ve B sürüm yolunda, C–E sürümü beklemez ve derleme 50'ye girmez.
**Dokunulmaz:** canlıya yazma, PR birleştirme, üretime yayın, mağaza gönderimi yalnız Mehmet'in açık sözüyle.

## A. Sunucu PR #15 (yayından önce)
1. "Geri dön" bildirimi üç cevapsız susturma kuralının **dışında** kalsın (deneme bitiş uyarısı gibi).
2. "Geri dön" son etkinlikten 3, 7, 14 gün sonra **öbür türlerin önünde** gitsin; o gün başka tür gitmesin. 30. gün kalsın.
3. Bırakmış kişiye (3 cevapsız) kelime tekrarı ve günün quizi gitmez; bu zaten var, değişmesin.
4. Tam test koşusunu tekrarla (düzeltmeden sonra yalnız kısmi koşulmuştu). Sonucu yaz.
5. Yayınlama. Hazır olunca Mehmet'e "PR 15 hazır" de.
"Geri dön" metinlerini Paul yazacak; şimdilik mevcut metin kalır.

## B. Açılışta kendiliğinden satın alma ekranı (yalnız inceleme, sonra en küçük düzeltme)
Sadık kullanıcı raporunda 1 numaraya uygulama açılır açılmaz, bir şeye dokunmadan satın alma ekranı çıkmış (sürüm 1.0.2).
1. 1.0.4 kodunda, kullanıcı bir şeye dokunmadan açılışta teklif açan bir yol var mı? Hangi kural, hangi koşul?
2. Varsa: onboarding sonu teklifi dışında hepsi kapansın (tek anahtar yeter). Karar: satış anı bitişte ve kullanıcının dokunduğu kilitte; kapıda değil.
3. Yoksa yalnız "yok" yaz, hangi dosyalara baktığını ekle.
Derleme 50'ye girer.

## C. Dizilerin ilk bölümü (yalnız sayı, canlıya yazma yok)
Kaç dizi var; her birinin ilk bölümü hangi seviyede, kaç kelime, merak cümlesi dolu mu. İlk bölümler ücretsiz olursa seviye başına ücretsiz metin sayısı ne olur (bugün A1 9, A2 8, B1 5, B2 2). Karışık seviyeli beş derleme (Game Day, Passport, Signal, Spotlight, Wild) ayrı gösterilsin.

## D. Ad ve açıklama dökümü (bekleyen)
`ortak/editor_gorevi_2026-11-21_seviye_quiz_guncelleme_verisi.md`, bölüm 5. Çıktı: `raporlar/veri_2026-11-21/adlar_ve_aciklamalar.csv`.

## E. Kariyer sayfası okunabilirlik taslağı (kod değil, görüntü; derleme 50'ye girmez)
Mehmet'in ekran görüntüsü (277 XP, Çaylak kazanılmış) üzerinden Dieter ve Don'un bulguları. Ayrı dalda, gerçek ekranda, **aynı kullanıcı durumuyla** (277 XP) görüntü üret. Rütbe adları ve rozet çizimleri değişmez.

**Her iki seçenekte ortak:**
1. **Yol kenardan kenara.** Yol bir rozetin kenarından çıkar, sıradaki rozetin kenarında biter; hiçbir nokta rozetin üstünden ya da altından geçmez (Mehmet).
2. **Yol dolar.** Geçilen kısım dolu ve renkli, kalan kısım noktalı. Kullanıcının bulunduğu yerde küçük bir işaret (bayrak buraya taşınabilir). 277 XP, Çaylak (200) ile Meraklı (900) arasında yolun %11'i.
3. **Sıradaki rütbe öne çıkar.** Meraklı yarı renkli, çevresinde dolan halka, altında "Sıradaki: Meraklı". Uzak rütbeler daha küçük ve soluk, **kilitsiz**.
4. **Alt şerit tek cümle.** İlerleme çubuğu ve "Meraklı'ya yaklaşık 5 günlük okuma kaldı". "~" ve ok yok. Kalan XP 60'ın altındaysa `ortak/uygulamanin_sesi.md` tablosundaki cümle.
5. **Üst kenar.** En üstteki rozet durum çubuğunun altında kesilmesin; geri düğmesi rozetle çakışmasın.
6. **Arka plan sakinleşsin.** Üçgen dağlar yolla karışmasın (daha soluk ya da kaldırılmış; hangisi temizse).
7. **Kayıt kartı.** Başlık "İlerlemeni güvene al", alt satır "Kayıt ol; rütben ve ilerlemen cihaz değişse de seninle kalsın." Kart yolu kapatmayacak yükseklikte.

**İki seçenek:**
- **E1, kapısız:** yalnız yukarıdakiler.
- **E2, eşikli:** sıradaki rütbenin (Meraklı) yolun bağlandığı kenarında küçük bir temsili kapı/eşik işareti; kilidin yerini alır. Uzak rütbelerde kapı da kilit de yok.

**Görüntüler** (`raporlar/ekran_2026-11-21/`): bugünkü hâl, E1, E2 yan yana tek pano; SE 3 ve büyük yazıda E1 ve E2 birer kare; bir de eşikler 20 / 350 / 1.000 olsaydı aynı kullanıcı (Meraklı'ya 73 XP) nasıl görünürdü, tek kare (yerelde, sunucu değeri değişmeden).
Ölçerek yaz: sıradaki rütbe adının zeminle karşıtlığı, alt şerit yazı boyu, en küçük dokunma alanı.
Karar Mehmet'in; onay olmadan ana dala girmez.

## Rapor
`raporlar/2026-11-21_editor_toplu_is.md`: A–E için ne yapıldı, ne yapılamadı, Mehmet'ten ne bekleniyor.
