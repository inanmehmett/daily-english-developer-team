# Başlangıç durakları: "sıradaki" cümleleri (taslak)

**Tarih:** 18 Kasım 2026. **Görev:** `ortak/editor_gorevi_2026-11-18_surum1_ilk_oturum.md`, madde 12.
**Durum:** Taslak. Canlıya yazılmadı. Metinler yerel içerik kopyasından (`de_olcum`) gövdesiyle okundu.

## Nasıl çalışıyor
- Cümle **biten durağın** `NextHook` alanında durur ve **sıradaki durağı** tanıtır. Bitiş ekranında "Sıradaki: {ad}" satırının altında görünür.
- Alan boşsa bitiş ekranı sıradaki durağın Türkçe açıklamasını (`DescriptionTR`) gösterir.
- 4. durağın cümlesi sonraki yolculuğun ilk bölümünü tanıtır, seviye yolculuklarının son bölümünde olduğu gibi. Ancak ücretsiz kullanıcı başlangıcı bitirince bitiş ekranında ilerleme kartı ve teklif gösteriliyor, bu cümle değil. 4. durağın cümlesini yalnız Premium kullanıcı görür.
- Yazım kuralı (seviye yolculuklarındaki 32 cümleyle aynı): şimdiki zaman, kısa cümle, sonu söylenmez, 300 karakter sınırı.

## Taslak

| Yolculuk | Biten durak (cümlenin yazılacağı metin) | Sıradaki | Cümle |
|---|---|---|---|
| A1 | `first-ramadan-in-london` · First Ramadan in London | Two Cups | Her sabah altıda biri çay koyuyor, biri merdiven siliyor. Bu sabah masada iki bardak var. |
| A1 | `kitchen-table-two-cups` · Two Cups | Thirty-One Mornings | Büyük kayanın yanında her sabah aynı tilki var. Emma her gün biraz daha yaklaşıyor; tilki her gün kaçıyor. Şimdilik. |
| A1 | `nature-thirty-one-mornings-v2` · Thirty-One Mornings | The Bench | Final sabahı hoca isimleri okuyor. Tom'un adı listede yok. Babası çitin arkasında bekliyor. |
| A1 | `sports-the-bench-v2` · The Bench | New in Town · Box Number Twelve | Başlangıç bitti. Sıradaki yolculukta Maya yeni bir şehre taşınıyor. Kapının arkasında, istemediği eski bir kutu duruyor. |
| A2 | `ali's-first-snow` · Ali's First Snow | The Cat Knows the Time | Turuncu kedi iki yıldır her sabah tam yedi buçukta karşı pencerede. Bir salı sabahı pencere boş. |
| A2 | `daily-life-the-cat-knows-the-time-v2` · The Cat Knows the Time | Baba Yaga | Ormanın derinliğinde tavuk bacakları üstünde yürüyen bir kulübe var. Üvey anne Vasilisa'yı oraya ateş almaya yolluyor. Oradan kimse dönmüyor. |
| A2 | `legends-baba-yaga` · Baba Yaga | The Island Where Rabbits Won | Japonya'da dokuz yüz tavşanın yaşadığı küçük bir ada var. Otuz yıl boyunca haritada yoktu, çünkü biri onu bilerek silmişti. |
| A2 | `island-where-rabbits-won` · The Island Where Rabbits Won | Coffee Shop Stories · The Empty Chair | Başlangıç bitti. Sıradaki yolculuk bir kafede: Howard her sabah 8.15'te aynı sandalyeye oturur. Bu sabah sandalye boş. |
| B1 | `village-that-whistles` · The Village That Whistles | Why Penguins Can't Fly | Penguen buzdan atlıyor ve suya taş gibi düşüyor. Sonra su altında tuhaf bir şey oluyor: uçmaya başlıyor. |
| B1 | `why-penguins-can't-fly` · Why Penguins Can't Fly | The Note That Opened the Berlin Wall | 9 Kasım 1989 akşamı bir yetkili, az önce eline tutuşturulan bir notu yüksek sesle okuyor. İki saat sonra binlerce kişi sınır kapısında. |
| B1 | `the-note-that-opened-the-berlin-wall` · The Note That Opened the Berlin Wall | The Girl Who Fell From the Sky | 1971'de Noel arifesinde bir uçak Amazon üzerinde fırtınada parçalanıyor. On yedi yaşında bir kız koltuğuyla birlikte ormana düşüyor ve uyanıyor. Asıl zor kısım o zaman başlıyor. |
| B1 | `survival-the-girl-who-fell-from-the-sky` · The Girl Who Fell From the Sky | World Cities · Rome | Başlangıç bitti. Sıradaki yolculuk Roma'dan başlıyor: metro kazan mühendisler her birkaç metrede başka bir şehre çarpıyor. |

## Kontrol notları
- Her cümle tanıttığı metnin ilk yarısından alındı; son söylenmiyor (tilkinin dokunduğu an, Tom'un penaltısı, kedinin taşınması, Juliane'nin kurtuluşu).
- Sayılar gövdeden: "iki yıldır, yedi buçuk", "dokuz yüz tavşan, otuz yıl", "9 Kasım 1989, iki saat", "1971, on yedi yaşında".
- "Two Cups" cümlesi metnin anlatıcısını adlandırmıyor; gövdede ad yok.
- Başlangıç A1'in 1. durağı (First Ramadan in London) için cümle yok, çünkü önünde durak yok; onboarding'in plan ekranı 4 durağın adını gösteriyor.

## Yazmadan önce
1. Mehmet ya da editör cümleleri onaylar.
2. Seviye yolculuklarının betiğine (`MigrationScripts/SetJourneyNextHooks_2026_11_18.sql`) 12 satır eklenir: yedek tablo, slug ile bağlama, sayı 44 değilse geri alma.
3. Canlıdaki gövde yazmadan önce bir kez daha okunur; yerel kopya `2026-11-15` tarihli.
