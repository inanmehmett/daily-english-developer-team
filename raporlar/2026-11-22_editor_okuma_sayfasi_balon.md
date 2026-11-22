# Editörden: okuma sayfasında balon şikâyetleri (Mehmet, 22 Kasım akşam)

**Tarih:** 22 Kasım 2026, 20:20 · **Kimden:** editör · **Kime:** ekip (Charles, Paul; bilgi: Dieter, Don)
**Mehmet (19:50):** özel isme dokununca çizgi önce tek kelimede, yarım saniye sonra adın tamamında ("Savile" → "Savile Row") · çizgi iki kelimedeyken seslendirme yalnız ilkini okuyor · özel isimlerin altında "Türkçede de aynı" yazıyor · "and he leaves late" cümlesinde "late" için "ayrıca: ölmüş" · "The lamp is off" cümlesinde "off" → "uzağa". Sonra: "Diğer işleri de uygula."

## Sizden beklenen karar
**"Ayrıca" satırı için kural** (aşağıda 4. madde). İki seçenek ve ölçümü var; ben kuralı değiştirmedim.

## Ne yapıldı
| # | Şikâyet | Neden | Yapılan |
|---|---|---|---|
| 1 | Çizgi önce tek kelimede, sonra adda | Çizgi dokunulan kelimeye hemen çiziliyor; adın tamamını sunucu söylüyor, cevap gelince çizgi genişliyor | **Düzeltildi** (uygulama, `2687ee03` ve `6e07653f`): yalnız boşlukla ayrılmış büyük harfli kelimeler dizisi cümlenin ortasındaysa çizgi **hemen dizinin tamamına** çizilir; sunucu farklı derse düzeltir. Dizi cümleyi başlatıyorsa ("Yesterday Tom" gibi belirsiz durum) çizgi sunucunun cevabını bekler, en çok 0,6 sn. Öbür kelimelerde bugünkü gibi anında. (Mehmet: "1 saniye geç değil mi" → ilk hâldeki bekleme kaldırıldı.) |
| 2 | Yalnız ilk kelime okunuyor | Balon ilk dokunulan kelimeyi tutuyordu | **Düzeltildi** (aynı commit): seslendirme altı çizili ifadenin tamamını okur |
| 3 | Özel isimde "Türkçede de aynı" | Satır, yazımı aynı kalan kelimeler için ("kilometre"); özel isim de çevrilmediği için ona da çıkıyordu | **Kaldırıldı** (aynı commit), yalnız özel isimde. Balonda türü ("yer", "kişi") zaten yazıyor. Paul'e: itirazın varsa geri alınır |
| 4 | "late" → "ayrıca: ölmüş" | Aşağıda | **Kural değişmedi**; bu cümle ek turla düzeltilecek |
| 5 | "off" → "uzağa" | Sözlükte "off"un birincil anlamı "uzağa" (zarf); "kapalı" kayıtlı ama seçilmiyor. Cümleye özel düzeltme yok | Ek tur (aşağıda). Motor kuralı ("be + off → kapalı") ayrı iş, ölçümle |

1–3 uygulamada, derleme 51 ister. Bu hatalar derleme 50 ile gelmedi; 1.0.2'de de var. Tam test turu temiz (1.325).

## 4. "Ayrıca" satırı: neden "ölmüş" çıktı, ne ölçtüm
Kural (`BalloonSecondaryMeaning`): birincil anlamla aynı türden, en az onun kadar puanlı, kısa ve kalıp işareti taşımayan **ilk** anlam gösterilir. "late" için sıfat anlamları sırayla: geç · …sonuna doğru (kalıp, elenir) · **ölmüş** · merhum · eski. Yani kural doğru çalışıyor, sonuç kötü. Cümlede "late" zarf; birincil yine sıfat anlamından geliyor.

Canlı sözlükle benzetim (8.083 kelime; bağlam puanı yok sayıldı, kaba ölçüm): bugün 4.414 kelimede "ayrıca" çıkıyor. Seçilen anlamın birincile sözlük sırasıyla uzaklığı: 1 sıra 2.407 · 2 sıra 990 · 3 ve üstü 397.

| Seçenek | Ne yapar | Ölçüm |
|---|---|---|
| A. Uzaklık sınırı: "ayrıca" birincilden en çok 2 sıra sonraki anlamdan gelir | 397 kelimede satır kalkar, hiçbirinde başka anlama dönmez | Kalkanlar karışık. İyi ki kalkanlar: late → ölmüş, cold → duygusuz, flat → sıkıcı, pet → tatlı çocuk, sails → deniz yolculuğu, forty → kırk yaşı. Kaybedilenler: light → lamba, free → serbest, quiet → sakin, trip → seyahat, fine → hoş, top → kapak |
| B. Tür uyumu: cümlede kelimenin türü birincil anlamın türünden farklıysa "ayrıca" hiç gösterilmez | "leaves late" gibi durumları hedefler | Ölçmedim: motoru katalogun tamamında çalıştırmak gerekiyor |

Kendi görüşüm: A körlemesine keser (yarısı yararlı satır); B daha isabetli olabilir ama ölçülmeden yayınlanmaz. Karar ve ölçüm isteği sizde.

## 5. Daha büyük bulgu: 12 yolculuk hikâyesi düzeltme işine hiç girmemiş
Cümle içi balon düzeltmesi (bugün son turu biten iş) yalnız Premium metinleri alıyordu. Yolculuklardaki 44 hikâyenin 22'si önceki turlarda, 10'u son turda; **12'si hiçbirinde yok**: 120, 124, 127, 916, 1019, 1023, 1024, 1045, 1059, 1070 ("The Cat Knows the Time", şikâyetin geldiği hikâye), 1083, 1085. Bunlar yeni okurun ilk okuduğu hikâyeler.
- **Ek tur başladı** (tur05): 12 hikâye, 368 cümle, 3.533 kelime, 7 parça. Aynı yöntem: düzeltme, kör kontrol, kabul. Canlıya yazma Mehmet'in sözüyle.
- Düzeltme turu yalnız ana karşılığa bakar, "ayrıca" satırını görmez; "late" cümlesine ana karşılığı ("geç") elle kayıt olarak ekleyeceğim, böylece o cümlede "ayrıca" da çıkmaz.

## Çeviri işinin durumu (bilgi)
Son tur (213 Premium metin, 399.533 kelime) 21.702 düzeltme önerisi üretti (%5,4; yaklaşık 19.200 yanlış anlam, 2.500 boş balon). Kör kontrol 19:45'te başladı: 43.404 kart, 272 parça, 8 işçi; yarın öğlene doğru biter. Önceki iki turda kabul oranı %91 ve %86 idi. Canlıya yazmadan önce Mehmet'e sayı ve örneklerle sorulacak.
