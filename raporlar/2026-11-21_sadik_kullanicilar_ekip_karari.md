# Sadık kullanıcılar: ekip okuması ve kararlar

**Tarih:** 21 Kasım 2026 · Tek geçiş; üyeler kurgusaldır. **Dayanak:** `2026-11-21_sadik_kullanicilar.md`, `2026-11-21_editor_durum_raporu.md` (editör).
**Uyarı (Nate, Nassim):** 17 kişi, gidenler 6 kişi. Aşağıdakiler hipotez; hüküm değil.

## Veri ne diyor
1. Sadık kullanıcı 4–9 gün üst üste geliyor, günde tek kısa metin okuyor (ortanca 4 dakika, 291 kelime), sonra **bir anda** bırakıyor. Kaydın 6.–14. gününde.
2. Giden altı kişinin dördü son ziyaretinde uygulamayı açtı, **hiçbir metin açmadan** çıktı. Beşi son gün hiçbir sınıra çarpmadı. Yani onları sınır ya da fiyat kovmadı; ana sayfa içeri alamadı.
3. En çok istedikleri şey diziler: 14 kişi kilitli dizi bölümüne 99 kez dokundu. Hiçbiri tek bölüm deneyemedi; ilk bölüm de kilitli.
4. Gittikten sonra 46 bildirim, sıfır dokunma. Yarısı kelime tekrarı sorusu; "geri dön" bildirimi altı kişiden yalnız birine gitmiş.
5. En çok okuyan kişinin (9 gün üst üste) son ziyaretinde uygulama açılır açılmaz satın alma ekranı çıkmış.
6. Beşinci satış: beş gündür okuyan bir müşteri, günlük metni bitirdikten bir dakika sonra yıllık denemeyi başlattı. "Bitişte iki kapı" tezine uyan ilk örnek; tek örnek.
7. 17 kişinin 16'sı eski sürümde. Yolculuğu, "yarın açılacak"ı hiçbiri görmedi.

## Kararlar
| No | Karar | Kim | Not |
|---|---|---|---|
| K1 | **1.0.4 bu hafta sonu mağazaya.** 16–17 Kasım'da başlayan altı sadık kullanıcı 4.–5. gününde; eğri aynıysa 23–26 Kasım'da gidecekler. Her bekleme günü bu grubu eski ana sayfada bırakıyor | Mehmet (telefon kontrolleri, gönderim) | Derleme 50 küçük düzeltmelerle aday |
| K2 | **"Geri dön" bildirimi susturma kuralının dışında** ve 3., 7., 14. günde öbür türlerin önünde. Bırakmış kişiye kelime tekrarı ve günün quizi gitmez (3 cevapsızdan sonra susar, olduğu gibi) | Editör, PR #15 yayınlanmadan | Metni Paul yazıyor: sıradaki hikâyenin adıyla, sıcak |
| K3 | **Açılışta kendiliğinden satın alma ekranı yok.** 1.0.4'te uygulama açılırken, kullanıcı bir şeye dokunmadan teklif açan bir yol kalmış mı? Kaldıysa kapatılır (onboarding sonu teklifi hariç) | Editör doğrular | Satış anı bitişte; kapıda değil |
| K4 | **Her dizinin ilk bölümü ücretsiz** (sonraki sürüm hazırlığı; uygulanması canlıya yazma olduğu için Mehmet'in "yap"ı gerekir). Bölüm sonunda merak cümlesi ve iki kapı zaten var | Sean, Paul; editör sayıyı çıkarır | Ölçüm: ilk bölümü bitirenlerin kaçı ikinci bölüm kilidinde satın al'a basıyor |
| K5 | **Günlük havuz gözden geçirilir.** 89 kelimelik metin bir günün ödülü olamaz; B1'de 5, B2'de 2 ücretsiz metin var. Seviye başına en az 8, en az 200 kelime | Paul, Charles | Seviye denetimiyle birlikte |
| K6 | **Gidenlere tek seferlik çağrı**, 1.0.4 mağazaya çıktıktan sonra. Eski ana sayfaya geri çağırmanın anlamı yok. Metin önce Mehmet'e taslak | Tony, Paul | Altı kişi; sonuç tek tek izlenir |
| K7 | **Ölçüm:** 1.0.4 sonrası "açtı, metin açmadı" oturumlarının payı ve 4+ gün okuyanların 14. günde hâlâ gelme oranı haftalık tabloya girer | Nate | Uygulama hangi ekranda olduğunu kaydetmiyor; yolculuk kartı gösterildi / dokunuldu sayımı yeter |

## Bilmediğimiz
Neden bıraktıklarını ancak kendileri söyler. K6'daki çağrıya dönenlere tek soruluk "seni ne geri getirdi / ne eksikti" sormak sonraki adım; şimdi değil.
