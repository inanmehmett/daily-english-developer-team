# ASO incelemesi — gerçek veri (App Store Connect + Play Console)

**Tarih:** 6 Kasım 2026 · **Hazırlayan:** Sean Büyüt · **Sebep:** Büyüme planının 1. önceliği — ücretsiz, hemen yapılabilir.

## 1. Mevcut metaveri (gerçek, kopyalanmış)

| Alan | iOS (App Store Connect) | Android (Play Console) |
|---|---|---|
| Ad/Başlık | Daily English: İngilizce Oku (28/30 karakter) | Daily English: İngilizce Oku (28/30 karakter) |
| Alt başlık / Kısa açıklama | "Hikâye oku, kelime biriktir" (27/30) | "Seviyene uygun İngilizce hikâyeler oku, kelime öğren, quizlerle test ol. A1-C2." (79/80) |
| Anahtar kelimeler (yalnızca iOS) | hikaye,seviye,a1,a2,b1,b2,c1,pratik,çeviri,sözlük,dinleme,telaffuz,kitap,sınav,**yds,toefl,ielts**,öğren (100/100 — tamamen dolu) | *(Play'de ayrı anahtar kelime alanı yok; başlık+açıklama metninden çıkarılıyor)* |
| Tam açıklama | 2.287 karakter kullanılmış (4000 limit) | 1.725 karakter kullanılmış (4000 limit), CEFR vurgusu, kalın başlıklar |
| Kategori | Education > Books | — |
| Yaş sınırı | 4+ | — |

## 2. Dönüşüm — her iki platformda da sektör ortalamasının üzerinde

| Platform | Sayfa görüntüleme → indirme dönüşümü | Sektör ortalaması |
|---|---|---|
| iOS (App Store Connect, 90 gün) | **%35,5** (217 sayfa görüntüleme → 77 ilk indirme) | %25 (ABD, [AppTweak](https://www.apptweak.com/en/aso-blog/app-store-conversion-rate?format=md)) |
| Android (Play Console, son 28 gün) | **%74-75** (72 ziyaretçi → 54 yükleme tıklaması) | %27,3 ([AppTweak](https://www.apptweak.com/en/aso-blog/app-store-conversion-rate?format=md)) |

**Sonuç: Mağaza sayfası (ekran görüntüleri, başlık, açıklama) zaten işe yarıyor — sorun orada değil.** İki platformda da aynı yönde (Hipotez, 2/5 — platform sayısı veri noktası sayılmaz, bu gözlemseldir, "ders" değildir).

## 3. Gerçek darboğaz: keşfedilme

- **iOS:** Gösterim 1.810 → sayfa görüntüleme 217 = **%12.** Çok sayıda gösterim var ama sayfaya tıklama/gösterim-to-view oranı düşük — bu arama sıralaması ya da ikon/başlık çekiciliği sorunu olabilir.
- **Android:** Son 90 günde "Keşfet"ten yalnızca +12 kullanıcı edinimi görüldü (Play Console "Kullanıcı sayısını artırın" ekranı) — organik keşif kanalından gelen trafik çok düşük.

**Teşhis: Darboğaz dönüşümde değil, görünürlükte.** ASO eforu ekran görüntüsü/metin değişikliğine değil, anahtar kelime ve kategori/sıralama çalışmasına gitmeli.

## 4. Somut bulgular ve öneriler

1. **Android'de sınav terimleri eksik.** iOS anahtar kelimelerinde `yds,toefl,ielts` var ama Android'in başlık/kısa/tam açıklamasında bu terimler hiç geçmiyor — Play'de ayrı anahtar kelime alanı olmadığından görünürlük tamamen bu metinlere bağlı. **Öneri:** Kısa veya tam açıklamaya "YDS, TOEFL, IELTS hazırlığına da yardımcı" gibi doğal bir cümle eklenebilir (AppTweak: anahtar kelimeler doğal dille, zorlama olmadan metne işlenmeli).
2. **iOS'ta görünürlük düşük (%12 gösterim→sayfa).** Anahtar kelime alanı zaten dolu (100/100); sorun muhtemelen arama sıralamasında (rank) ya da ikon/başlığın arama sonuçlarında çekiciliğinde. **Öneri:** "Search Results" önizlemesi (App Store Connect'te zaten bir sekme olarak var) kontrol edilmeli — ikon ve başlık küçük boyutta nasıl görünüyor.
3. **Ekran görüntüleri incelenmedi** (bu turda zaman/maliyet sınırı nedeniyle sayfaya girilmedi) — "göz atma testi" ve karanlık mod önerisi (AppTweak) bir sonraki turda görsel olarak kontrol edilebilir.
4. **Ölçüm devam etmeli:** Her iki platformun da gösterim/ziyaretçi, sayfa görüntüleme, indirme rakamları haftalık Nate Gümüş raporuna eklenmeli — ASO değişikliklerinin etkisini görmek için "önce/sonra" referans noktası bu.

## İtirazlar
- **Nassim Talip:** İki platformdaki benzer "sayfa iyi, keşif zayıf" örüntüsü ilginç ama 2 platform 2 veri noktasıdır, "ders" değildir — her platformun kendi dinamiği (Apple arama algoritması vs Play Store algoritması) farklı olabilir, aynı nedenden olduğu varsayılmamalı.

## Kaynaklar
- [AppTweak — App Store Conversion Rate](https://www.apptweak.com/en/aso-blog/app-store-conversion-rate?format=md)
