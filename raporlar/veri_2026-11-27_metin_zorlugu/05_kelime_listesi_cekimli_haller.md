# 5. Kelime listesi çekimli hâlleri liste dışı mı sayıyor?

**Kısa cevap: evet, sayıyor;** köke indirgeyerek yeniden ölçüldü. Ama köke indirgemek A1 ile A2'yi yine de ayırmıyor; asıl sorun listenin kendisi.

## Ne yapıldı
- 21 Kasım ölçümünü üreten betik saklanmamış; aynı kaynakla (genel İngilizce sıklık listesi, en sık 1.000 / 2.000 / 3.000 kelime) yeniden yazıldı. Canlıdaki 74 etkin A1–A2 metni ölçüldü (24 A1, 50 A2; dokuz metin 21 Kasım'dan sonra B1'e alındığı için sayı 84'ten düştü).
- **Eski yöntem (yüzey):** kelime metinde yazıldığı hâliyle listede aranır.
- **Yeni yöntem (kök):** kelime kökü de aranır (drank → drink, stood → stand, glasses → glass) ve cümle ortasında büyük harfle yazılan özel adlar sayılmaz.
- Sayılar 21 Kasım dosyasıyla birebir aynı değil (kelime ayırma ve metin kümesi farklı); iki yöntem burada aynı betikle karşılaştırıldı.

## Sonuç
| En sık … kelimenin dışında kalan oran (ortanca) | A1, yüzey | A2, yüzey | A1, kök | A2, kök |
|---|---|---|---|---|
| 1.000 | %25,5 | %23,9 | %19,8 | %18,9 |
| 2.000 | %16,9 | %16,7 | **%10,8** | **%11,6** |
| 3.000 | %8,8 | %11,5 | **%4,2** | **%7,6** |

- Çekimli hâller oranı gerçekten şişiriyordu: 2.000 listesinde yüzeyle %17, kökle %11.
- **2.000 listesinde A1 ile A2 kökle de ayrışmıyor** (%10,8'e %11,6). Ayrım ancak 3.000 listesinde görünüyor (%4,2'ye %7,6).
- Görevde adı geçen üç kelime: "drank" köke inince listede (drink). **"washed" ve "stairs" köke inince de ilk 2.000'de değil** (wash, stair). Yani bu ikisi çekim yüzünden değil, liste yüzünden dışarıda.

## Asıl sorun: sıklık listesi öğrenci seviyesini ölçmüyor
Kökle bile "liste dışı" kalan kelimeler A1 öğrencisinin ilk öğrendiği gündelik kelimeler: *kitchen, breakfast, rain, shoes, sugar, stairs, wet, grass, tomato*. Genel sıklık listesi internet ve haber dilinden çıkıyor; orada "government" sık, "kitchen" seyrek. Bu yüzden "en sık 2.000 dışı" oranı A1 metnini olduğundan zor gösteriyor ve iki seviyeyi ayıramıyor.
- Seviye için doğru ölçü, öğrenci kelime listesidir (CEFR seviyeli bir liste: A1'de hangi kelimeler beklenir). Böyle bir liste bu bilgisayarda ve depoda **yok**; ekip bir liste seçerse aynı betik onunla çalışır.
- Gerçek zorluk için elimizdeki en iyi ölçü listeler değil, okurun dokunduğu kelimeler (madde 1): Two Cups'ta başlayanların yarısı "bucket" ve "stairs"e dokunmuş.

## Üç başlangıç metni
| Metin | Yüzey, 2.000 dışı | Kök, 2.000 dışı | Köke inince listeye girenler | Kökle de liste dışı kalanlar |
|---|---|---|---|---|
| 916 Two Cups (A1) | %14,7 | %10,7 | cleans, drank, glasses, stood, talked | stairs, bucket, shoes, wet, rain, sugar, kitchen, pot |
| 1083 Thirty-One Mornings (A1) | %23,5 | %14,9 | closes, eats, learns, sees, sits, stands, stays, stops, trees, tries | fox, thirty, grass, forest, forty, boring, twenty, rain |
| 1023 Rabbit Island (A2) | %16,9 | %13,5 | asks, buildings, cats, chosen, maps, trees, visited, walls, weapon, worker | rabbits, visitors, factory, empty, ferries, rabbit, thirty |

Two Cups'ta kökle de liste dışı kalan sekiz kelimenin altısı, okurların en çok dokunduğu yirmi kelimenin içinde (stairs, bucket, wet, pot ve öbürleri): bu metinde liste ile okurun davranışı aynı kelimeleri gösteriyor.

**Metin başına tam tablo:** `05_kelime_listesi_kokle.csv` (74 metin; üç liste, iki yöntem, örnek kelimeler).

**Sınır:** kök bulma otomatik bir araçla yapıldı (her kelimeyi doğru çözmez); özel ad ayırma büyük harfe bakıyor, cümle başındaki özel adı kaçırabilir.
