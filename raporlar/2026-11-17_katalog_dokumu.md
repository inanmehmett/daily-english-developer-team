# Katalog dökümü – yolculuk adayları için

**Rol:** Paul Ulus (içerik), Nate Gümüş (veri). **Tarih:** 17 Kasım 2026.
**Görev:** `ortak/editor_gorevi_2026-11-17_katalog_dokumu.md`. Yalnız okuma yapıldı. Bağlantı `default_transaction_read_only = on` ile açıldı; canlıda hiçbir satır değişmedi.
**Tam katalog:** `raporlar/2026-11-17_katalog.csv` (287 satır, okunma sütunlarıyla birlikte).

## En üstte: seviye başına

Canlıda 287 metin var ve hepsi etkin; etkin olmayan metin yok. Pasif metinler 15 Eylül'de silinmişti.

| Seviye | Metin | Başlıca gruplar |
|---|---|---|
| A1 | 24 | New in Town dizisi 10 · the-measure kümesi 3 · eski tek parçalar 3 · kitchen-table kümesi 2 · diğer gruplarda birer metin 6 |
| A2 | 60 | Coffee Shop dizisi 12 · daily-life 7 · klasik romanlar 5 · travel 5 · nearly kümesi 4 · kitchen-table kümesi 3 · eski tek parçalar 3 · küçük gruplarda 21 |
| B1 | 107 | Lending Library dizisi 10 · Room 214 dizisi 10 · klasik romanlar 9 · şehir belgeselleri 8 · Why dizisi 7 · Lighthouse Letters dizisi 6 · survival 6 · eski tek parçalar 6 · legends 5 · merak tek parçaları 5 · Roma 2 · diğerleri 33 |
| B2 | 72 | şehir belgeselleri 14 · Second Chances dizisi 12 · Lighthouse Letters dizisi 6 · eski tek parçalar 6 · klasik romanlar 4 · four-seconds kümesi 3 · merak 3 · survival 3 · Roma 1 · diğerleri 20 |
| C1 | 20 | klasik öyküler 5 · Originals tek parçalar 5 · Sherlock Holmes 4 · klasik romanlar 2 · dört dizinin birer bölümü |
| C2 | 4 | klasik romanlar 3 · klasik öykü 1 |

| Seviye | Etkin | Her zaman açık (`IsStarterPack`) | Günlük açma havuzu (`IsDailyUnlock`) | `Series` dizisinde | Dizi dışı bir grupta | Gruba ait değil | 2+ bölümlü | Toplam kelime |
|---|---|---|---|---|---|---|---|---|
| A1 | 24 | 2 | 7 | 13 | 8 | 3 | 0 | 7.250 |
| A2 | 60 | 1 | 7 | 18 | 38 | 4 | 7 | 69.091 |
| B1 | 107 | 0 | 5 | 39 | 59 | 9 | 11 | 154.532 |
| B2 | 72 | 0 | 2 | 25 | 38 | 9 | 7 | 119.447 |
| C1 | 20 | 0 | 0 | 4 | 11 | 5 | 7 | 57.007 |
| C2 | 4 | 0 | 0 | 0 | 4 | 0 | 4 | 31.593 |
| **Toplam** | **287** | **3** | **21** | **99** | **158** | **30** | **36** | **438.920** |

Göze çarpanlar (bulgu olarak, öneri değil):
- **`NextHook` hiçbir metinde dolu değil.** 287 metnin ve 379 bölümün (`Chapter`) hepsinde boş. `FinishLine` da 287 metnin hepsinde boş.
- **Ücretsizlik kuralı (kod, `ReadingTextsController.CanAccessReadingTextAsync`):** `IsStarterPack` olan metin herkese açık. `IsDailyUnlock` olan metin, ücretsiz kullanıcının o gün açtığı tek metinse açık. Geri kalan her şey premium. Dizi bölümlerinde de aynı kural geçiyor (`SeriesController`: `CanAccess = isPremium || IsStarterPack`).
- **Dizi sayılan ama `Series` tablosunda olmayan kümeler var:** kitchen-table, nearly, four-seconds, one-turn, the-small-hours, the-measure ve shift. Bu kümelerin üyeleri slug önekiyle birbirine bağlanıyor, veritabanında ortak bir alan yok.
- **A1'de çok az metin var:** 24 metnin 10'u tek bir dizi (New in Town), toplam 7.250 kelime. C1–C2'de her zaman açık ya da günlük açılan metin yok.

## Gruplar

Gruplama sırası:
1. `SeriesId` dolu olan metin "Dizi: <slug>" grubuna girer.
2. Slug'ı `rome-` ile başlayanlar Roma grubuna girer.
3. 994–1015 kimlikli "Daily English Originals" Culture parçaları şehir belgeselidir.
4. 1016–1024 merak tek parçalarıdır. 1 Ağustos teslim notundaki "Merak serileri" parçalarıdır; veritabanında dizi olarak bağlı değiller.
5. Yazarı Arthur Conan Doyle olanlar Sherlock Holmes grubuna girer.
6. `literature-` önekliler bölüm sayısına göre ayrılır: 5 ve üzeri bölüm roman, 0–4 bölüm öykü.
7. Kalanlar slug önekine göre gruplanır.
8. Hiçbir gruba girmeyen metin "Tek parça" sayılır.

`Series` tablosunda 12 dizi var ve hepsi etkin. "Okur / bitiren" sütunu 29 Ekim'den beri müşteri hesaplarını sayar.

| Grup | Metin | A1 | A2 | B1 | B2+ | Kelime aralığı | 2+ bölümlü | Açık / günlük | NextHook | Okur / bitiren |
|---|---|---|---|---|---|---|---|---|---|---|
| Klasik roman (literature-, 5+ bölüm) | 23 | 0 | 5 | 9 | 9 | 7022–14131 | 23 | 0 / 0 | 0 | 0 / 0 |
| Şehir belgeselleri | 22 | 0 | 0 | 8 | 14 | 423–535 | 0 | 0 / 0 | 0 | 0 / 0 |
| Tek parça (eski Daily English) | 18 | 3 | 3 | 6 | 6 | 89–467 | 0 | 0 / 6 | 0 | 113 / 75 |
| Dizi: coffee-shop-stories | 12 | 0 | 12 | 0 | 0 | 564–722 | 0 | 0 / 0 | 0 | 2 / 0 |
| Dizi: lighthouse-letters | 12 | 0 | 0 | 6 | 6 | 954–1315 | 0 | 0 / 0 | 0 | 0 / 0 |
| Dizi: second-chances | 12 | 0 | 0 | 0 | 12 | 792–1220 | 0 | 0 / 0 | 0 | 0 / 0 |
| Tek parça (Originals) | 12 | 0 | 1 | 3 | 8 | 326–844 | 0 | 0 / 1 | 0 | 1 / 0 |
| Dizi: lending-library | 10 | 0 | 0 | 10 | 0 | 827–1057 | 0 | 0 / 0 | 0 | 0 / 0 |
| Dizi: new-in-town | 10 | 10 | 0 | 0 | 0 | 384–487 | 0 | 0 / 0 | 0 | 2 / 2 |
| Dizi: room-214 | 10 | 0 | 0 | 10 | 0 | 697–818 | 0 | 0 / 0 | 0 | 0 / 0 |
| Dizi: why | 9 | 0 | 0 | 7 | 2 | 516–661 | 0 | 0 / 0 | 0 | 0 / 0 |
| Klasik öykü (literature-, 0–4 bölüm) | 9 | 0 | 1 | 1 | 7 | 191–2911 | 4 | 0 / 0 | 0 | 2 / 0 |
| legends* | 9 | 0 | 2 | 5 | 2 | 364–577 | 0 | 0 / 2 | 0 | 3 / 3 |
| Merak tek parçaları | 9 | 0 | 1 | 5 | 3 | 281–489 | 0 | 1 / 2 | 0 | 83 / 56 |
| survival* | 9 | 0 | 0 | 6 | 3 | 445–656 | 0 | 0 / 1 | 0 | 3 / 1 |
| daily-life* | 8 | 0 | 7 | 0 | 1 | 232–496 | 0 | 0 / 1 | 0 | 3 / 2 |
| travel* | 8 | 1 | 5 | 2 | 0 | 132–445 | 0 | 0 / 2 | 0 | 3 / 1 |
| culture* | 7 | 0 | 2 | 4 | 1 | 177–376 | 0 | 0 / 0 | 0 | 3 / 1 |
| Diziye bağlanmamış küme: kitchen-table* | 6 | 2 | 3 | 1 | 0 | 217–492 | 0 | 1 / 1 | 0 | 98 / 68 |
| Diziye bağlanmamış küme: shift* | 6 | 0 | 1 | 4 | 1 | 552–672 | 0 | 0 / 0 | 0 | 0 / 0 |
| Dizi: passport | 5 | 1 | 1 | 1 | 2 | 270–1094 | 0 | 0 / 0 | 0 | 2 / 1 |
| Dizi: signal | 5 | 0 | 2 | 1 | 2 | 435–1147 | 0 | 0 / 0 | 0 | 0 / 0 |
| Dizi: spotlight | 5 | 0 | 1 | 2 | 2 | 481–1107 | 0 | 0 / 0 | 0 | 0 / 0 |
| Dizi: wild | 5 | 1 | 1 | 1 | 2 | 288–1000 | 0 | 0 / 0 | 0 | 0 / 0 |
| Diziye bağlanmamış küme: nearly* | 5 | 0 | 4 | 1 | 0 | 315–425 | 0 | 0 / 1 | 0 | 0 / 0 |
| Dizi: game-day | 4 | 1 | 1 | 1 | 1 | 318–907 | 0 | 0 / 0 | 0 | 0 / 0 |
| Diziye bağlanmamış küme: four-seconds* | 4 | 0 | 0 | 1 | 3 | 485–616 | 0 | 0 / 0 | 0 | 0 / 0 |
| Diziye bağlanmamış küme: one-turn* | 4 | 0 | 1 | 3 | 0 | 364–428 | 0 | 0 / 0 | 0 | 0 / 0 |
| Diziye bağlanmamış küme: the-measure* | 4 | 3 | 1 | 0 | 0 | 189–309 | 0 | 0 / 2 | 0 | 2 / 1 |
| Diziye bağlanmamış küme: the-small-hours* | 4 | 0 | 1 | 3 | 0 | 495–550 | 0 | 0 / 0 | 0 | 0 / 0 |
| Sherlock Holmes | 4 | 0 | 0 | 0 | 4 | 2874–3462 | 4 | 0 / 0 | 0 | 0 / 0 |
| nature* | 3 | 1 | 0 | 2 | 0 | 254–404 | 0 | 1 / 0 | 0 | 18 / 14 |
| Roma belgeselleri | 3 | 0 | 0 | 2 | 1 | 435–744 | 0 | 0 / 0 | 0 | 0 / 0 |
| adventure* | 2 | 0 | 1 | 0 | 1 | 5593–11457 | 2 | 0 / 0 | 0 | 0 / 0 |
| family* | 2 | 0 | 2 | 0 | 0 | 264–280 | 0 | 0 / 1 | 0 | 1 / 0 |
| famous-people* | 2 | 0 | 0 | 1 | 1 | 452–3150 | 1 | 0 / 0 | 0 | 0 / 0 |
| sports* | 2 | 1 | 0 | 1 | 0 | 251–5651 | 1 | 0 / 1 | 0 | 4 / 2 |
| inspiration* | 1 | 0 | 1 | 0 | 0 | 290–290 | 0 | 0 / 0 | 0 | 0 / 0 |
| mystery* | 1 | 0 | 0 | 0 | 1 | 11008–11008 | 1 | 0 / 0 | 0 | 0 / 0 |
| technology* | 1 | 0 | 0 | 0 | 1 | 548–548 | 0 | 0 / 0 | 0 | 0 / 0 |

Diziler ve sıralı olup olmadıkları (`IsSequential`): coffee-shop-stories, new-in-town, lighthouse-letters, lending-library, room-214 ve second-chances sıralı. why, passport, wild, signal, game-day ve spotlight sırasız. Uzun kitaplardan beşi `literature-` öneki taşımıyor: `adventure-the-jungle-book` (A2, 10 bölüm), `adventure-the-invisible-man` (B2, 12), `mystery-dracula` (B2, 14), `sports-sixty-kilos-suleymanoglu` (B1, 9), `famous-people-saint-exupery` (B1, 8).

## Okunma (29 Ekim'den beri, müşteri hesapları)

287 metnin 32'si en az bir müşteri tarafından açılmış; 255 metni hiçbir müşteri açmamış. Okumaların neredeyse hepsi ilk deneyimde önerilen dört metinde toplanıyor:

| Metin | Seviye | Kelime | Okur | Bitiren | 50 kelimede bakış (ortanca) |
|---|---|---|---|---|---|
| kitchen-table-two-cups | A1 | 217 | 96 | 66 | 1,6 |
| why-penguins-can't-fly | B1 | 332 | 84 | 48 | 1,7 |
| island-where-rabbits-won | A2 | 287 | 47 | 33 | 3,3 |
| village-that-whistles | B1 | 281 | 36 | 23 | 1,2 |
| nature-thirty-one-mornings-v2 | A1 | 254 | 18 | 14 | 1,2 (az veri) |
| first-ramadan-in-london | A1 | 137 | 10 | 9 | 2,9 (az veri) |
| Diğer 26 metin | | | 1–6 | | az veri |

Tanımlar:
- **Okur:** `ReadingProgresses` kaydı ya da `reading_started` olayı olan müşteri.
- **Bitiren:** `IsCompleted` ya da `reading_completed`.
- **Bakış:** müşteri sürümlerinin `word_lookup` olayı metin kimliği taşımıyor. Bu yüzden bakışlar, metnin ilk açılışından itibaren 60 dakika içinde ya da başka bir metin açılana kadar sayıldı. Böylece metne zaman aralığıyla bağlandı ve sonuç 50 kelimeye oranlandı.

Metin başına sayılar CSV'de: `customer_readers`, `customer_finishers`, `lookups_per50_median`, `lookups_sample`. Bu ölçüme göre yolculuk adayı grupların hemen hepsi (şehirler, Roma, klasikler, diziler) müşteri okumasına göre değerlendirilemez. Okunmamış olmalarının nedeni büyük olasılıkla önerilmemeleri ya da premium olmaları; bu bir **hipotezdir**.

## Roma

Canlıda başlığında Rome geçen **3 metin** var, üçü de etkin. Gövdesinde "Rome" ya da "Roma" geçen 7 metin daha var. Etkin olmayan Roma metni yok. 15 Eylül'de silinen pasif metinlerin yedeğinde de Roma parçası yok.

| Id | Slug | Başlık | Seviye | Kelime | Durum | Nerede geçiyor | Grup | Okur / bitiren |
|---|---|---|---|---|---|---|---|---|
| 991 | rome-city-built-on-itself | Rome: The City Built on Top of Itself | B1 | 435 | etkin | başlıkta | Roma belgeselleri | 0 / 0 |
| 990 | rome-city-the-world-built | Rome: The City the World Built | B2 | 744 | etkin | başlıkta | Roma belgeselleri | 0 / 0 |
| 992 | rome-fountain-not-a-monument | Rome: The Fountain That Is Not a Monument | B1 | 469 | etkin | başlıkta | Roma belgeselleri | 0 / 0 |
| 998 | cairo-city-that-ate-a-pyramid | Cairo: The City That Ate a Pyramid | B2 | 473 | etkin | yalnız gövdede | Şehir belgeselleri | 0 / 0 |
| 1078 | daily-life-marta-orders-v2 | Marta and the Peaches | A2 | 255 | etkin | yalnız gövdede | daily-life* | 0 / 0 |
| 1001 | florence-city-bankers-built | Florence: The City That Bankers Built | B2 | 506 | etkin | yalnız gövdede | Şehir belgeselleri | 0 / 0 |
| 1003 | istanbul-one-city-three-names | Istanbul: One City, Three Names | B2 | 535 | etkin | yalnız gövdede | Şehir belgeselleri | 0 / 0 |
| 1004 | jerusalem-city-everyone-wanted | Jerusalem: The City Everyone Wanted | B2 | 515 | etkin | yalnız gövdede | Şehir belgeselleri | 0 / 0 |
| 1008 | petra-carved-from-cliff | Petra: The City Carved from a Cliff | B1 | 423 | etkin | yalnız gövdede | Şehir belgeselleri | 0 / 0 |
| 1056 | survival-nine-days-in-the-sahara | Nine Days in the Sahara | B1 | 485 | etkin | yalnız gövdede | survival* | 0 / 0 |

**Dördüncü parça:** Mehmet'in hatırladığı dördüncü parça teslim edilmiş ama veritabanına hiç yüklenmemiş. 1 Ağustos teslim notunda (`Downloads/ARSIV/TESLIM - TAM PAKET (5 Eki 2026)/Teslim 1 Agu 2026/TESLİM NOTU.md`) Roma için dört parça sayılıyor:
1. The City the World Built (B2)
2. Built on Top of Itself (B1)
3. The Fountain That Is Not a Monument (B1)
4. **The Oldest Sound (B1, `rome-the-oldest-sound`)**

Notta 3 ve 4 için "biri seçilir" yazıyor. Seçilen 3 yüklenmiş, 4 dosyada kalmış (`Belgesel Motoru Test - Rome v2b.md` ve ilk sürüm `Belgesel Motoru Test - Rome.md`). Aynı klasörde beşinci bir taslak da var: "Rome: The Water Never Stops" (B1, `rome-the-water-never-stops`). Bu da yüklenmemiş. `MigrationScripts/AddRomeDocumentaries_2026_08_01.sql` yalnız üç slug'ı ekliyor.

## İtirazlar ve sınırlar

- **Grup sınırları elle çizildi.** Şehir belgeselleri ve merak parçaları kimlik aralığıyla (994–1015, 1016–1024) ve 1 Ağustos teslim listesiyle eşlendi. Veritabanında bunları birbirine bağlayan bir alan yok. Teslim notundaki merak dizi adları ("You Still Live by Their Rules", "Nobody Builds Here" ve diğerleri) da canlıda yok.
- **Kelime sayısı güvenilir değil.** 15 Kasım raporuna göre `WordCount` 287 metnin 81'inde %15'ten fazla sapıyor; düzeltme betiği çalıştırılmadı. Tablodaki kelime sayıları bu yüzden yaklaşıktır.
- **Okunma verisi küçük ve yanlı.** 243 müşteri var ve okumalar ilk deneyimde önerilen dört metinde toplanıyor. Okunmamış bir metin hakkında okunma verisiyle hüküm verilemez.
- **Seviye etiketi elle girildi.** 15 Ekim katalog denetimi 24 seviyeyi düzeltmişti; etiketlerin geri kalanı yeniden ölçülmedi.

## Ek: tam katalog

Sütunlar: kimlik, slug, başlık, Türkçe alt başlık (`SubtitleTR`), kategori, seviye, kelime, bölüm sayısı, dizi ve sezon/bölüm, erişim (her zaman açık / günlük açma / premium), NextHook, okur / bitiren, 50 kelimede bakış ortancası. Veritabanında ayrı bir Türkçe başlık alanı yok; Türkçe olarak kartta `SubtitleTR` görünüyor. Aynı veri CSV'de de var.

| Id | Slug | Başlık | SubtitleTR | Kategori | Seviye | Kelime | Bölüm | Dizi | Erişim | NextHook | Okur / bitiren | Bakış/50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1103 | adventure-the-jungle-book | The Jungle Book | Orman Kitabı | Adventure | A2 | 5593 | 10 |  | premium |  | 0 / 0 |  |
| 1104 | adventure-the-invisible-man | The Invisible Man | Görünmez Adam | Adventure | B2 | 11457 | 12 |  | premium |  | 0 / 0 |  |
| 1063 | culture-spain-morning-v2 | The Country That Eats Breakfast Twice | İspanya’nın Kahvaltı Kültürü | Culture | A2 | 322 | 0 |  | premium |  | 1 / 0 | 0.0 |
| 1067 | culture-tokyo-umbrella-v2 | The See-Through Umbrella | Şeffaf Şemsiye | Culture | A2 | 313 | 0 |  | premium |  | 1 / 0 | 0.8 |
| 1032 | culture-egypt-say-no-to-the-tea | Egypt: Say No to the Tea (At First) | Mısır’da Çay Nazlanması | Culture | B1 | 177 | 0 |  | premium |  | 0 / 0 |  |
| 1065 | culture-istanbul-market-v2 | The Market That Moves | İstanbul’un Yer Değiştiren Pazarı | Culture | B1 | 347 | 0 |  | premium |  | 1 / 1 | 7.2 |
| 1068 | culture-japanese-village-v2 | The Village That Throws Away Almost Nothing | Çöp Kamyonu Gelmeyen Köy | Culture | B1 | 333 | 0 |  | premium |  | 0 / 0 |  |
| 1064 | culture-sushi-v2 | The Fish That Needs No Sauce | Sos İstemeyen Balık | Culture | B1 | 365 | 0 |  | premium |  | 0 / 0 |  |
| 1066 | culture-diwali-v2 | The Night India Turns On Its Lights | Hindistan’ın Işıl Işıl Gecesi | Culture | B2 | 376 | 0 |  | premium |  | 0 / 0 |  |
| 1078 | daily-life-marta-orders-v2 | Marta and the Peaches | Şeftali Pazarlığı | Daily Life | A2 | 255 | 0 |  | premium |  | 0 / 0 |  |
| 1076 | daily-life-old-fridge-v2 | The Old Fridge's Last Night | Eski Buzdolabının Son Gecesi | Daily Life | A2 | 256 | 0 |  | premium |  | 0 / 0 |  |
| 1069 | daily-life-table-six-v2 | Table Six | Altı Numaralı Masa | Daily Life | A2 | 279 | 0 |  | premium |  | 0 / 0 |  |
| 1070 | daily-life-the-cat-knows-the-time-v2 | The Cat Knows the Time | Saati Bilen Kedi | Daily Life | A2 | 291 | 0 |  | günlük |  | 3 / 2 | 0.3 |
| 1071 | daily-life-the-plant-war-v2 | The Plant War | Bitki Savaşı | Daily Life | A2 | 270 | 0 |  | premium |  | 0 / 0 |  |
| 1079 | daily-life-the-wrong-bag-v2 | The Wrong Bag | Yanlış Çanta | Daily Life | A2 | 232 | 0 |  | premium |  | 0 / 0 |  |
| 1077 | daily-life-three-stops-v2 | Three Stops Too Far | Üç Durak Fazla | Daily Life | A2 | 242 | 0 |  | premium |  | 0 / 0 |  |
| 1072 | daily-life-buy-nothing-v2 | The Year They Bought Nothing | Alışverişsiz Bir Sene | Daily Life | B2 | 496 | 0 |  | premium |  | 0 / 0 |  |
| 817 | coffee-shop-s1e1-the-empty-chair | The Empty Chair | Boş Sandalye | Daily Life | A2 | 603 | 0 | coffee-shop-stories S1E1 | premium |  | 2 / 0 | 0.0 |
| 818 | coffee-shop-s1e2-black-one-sugar | Black, One Sugar | Sütsüz, Tek Şekerli | Daily Life | A2 | 590 | 0 | coffee-shop-stories S1E2 | premium |  | 0 / 0 |  |
| 819 | coffee-shop-s1e3-the-first-customer | The First Customer | İlk Müşteri | Daily Life | A2 | 647 | 0 | coffee-shop-stories S1E3 | premium |  | 0 / 0 |  |
| 820 | coffee-shop-s1e4-the-closed-sign | The Closed Sign | ‘Kapalı’ Yazan Tabela | Daily Life | A2 | 606 | 0 | coffee-shop-stories S1E4 | premium |  | 0 / 0 |  |
| 821 | coffee-shop-s1e5-flowers-on-tuesday | Flowers on Tuesday | Salı Çiçekleri | Daily Life | A2 | 564 | 0 | coffee-shop-stories S1E5 | premium |  | 0 / 0 |  |
| 822 | coffee-shop-s1e6-the-woman-in-the-photo | The Woman in the Photo | Fotoğraftaki Kadın | Daily Life | A2 | 585 | 0 | coffee-shop-stories S1E6 | premium |  | 0 / 0 |  |
| 823 | coffee-shop-s1e7-rosas-phone | Rosa's Phone | Rosa’nın Telefonu | Daily Life | A2 | 606 | 0 | coffee-shop-stories S1E7 | premium |  | 0 / 0 |  |
| 824 | coffee-shop-s1e8-the-letter | The Letter | Altı Kelimelik Mektup | Daily Life | A2 | 656 | 0 | coffee-shop-stories S1E8 | premium |  | 0 / 0 |  |
| 825 | coffee-shop-s1e9-small-talk | Small Talk | Havadan Sudan | Daily Life | A2 | 587 | 0 | coffee-shop-stories S1E9 | premium |  | 0 / 0 |  |
| 826 | coffee-shop-s1e10-the-broken-mug | The Broken Mug | Kırık Fincan | Daily Life | A2 | 603 | 0 | coffee-shop-stories S1E10 | premium |  | 0 / 0 |  |
| 827 | coffee-shop-s1e11-before-emma | Before Emma | Emma’dan Önce | Daily Life | A2 | 722 | 0 | coffee-shop-stories S1E11 | premium |  | 0 / 0 |  |
| 828 | coffee-shop-s1e12-eight-fifteen | Eight Fifteen | Sekizi Çeyrek Geçe | Daily Life | A2 | 677 | 0 | coffee-shop-stories S1E12 | premium |  | 0 / 0 |  |
| 910 | game-day-the-red-shirt | The Red Shirt | Kırmızı Forma | Sports | A1 | 318 | 0 | game-day S1E4 | premium |  | 0 / 0 |  |
| 907 | game-day-second-half | Second Half | İkinci Yarı | Sports | A2 | 446 | 0 | game-day S1E1 | premium |  | 0 / 0 |  |
| 909 | game-day-the-marathon | The Marathon | Pankartsız Maraton | Sports | B1 | 653 | 0 | game-day S1E3 | premium |  | 0 / 0 |  |
| 908 | game-day-the-coach | The Coach | Antrenör | Sports | B2 | 907 | 0 | game-day S1E2 | premium |  | 0 / 0 |  |
| 851 | lending-library-s1e1-the-shelf-at-the-back | The Shelf at the Back | Arkadaki Raf | Fantasy | B1 | 1057 | 0 | lending-library S1E1 | premium |  | 0 / 0 |  |
| 852 | lending-library-s1e2-sams-four-days | Sam's Four Days | Sam’in Dört Günü | Fantasy | B1 | 992 | 0 | lending-library S1E2 | premium |  | 0 / 0 |  |
| 853 | lending-library-s1e3-a-short-history-of-rope | A Short History of Rope | Halatın Kısa Tarihi | Fantasy | B1 | 987 | 0 | lending-library S1E3 | premium |  | 0 / 0 |  |
| 854 | lending-library-s1e4-kitchen-latin | Kitchen Latin | Mutfak Latincesi | Fantasy | B1 | 949 | 0 | lending-library S1E4 | premium |  | 0 / 0 |  |
| 855 | lending-library-s1e5-the-fourth-wall | The Fourth Wall | Dördüncü Duvar | Fantasy | B1 | 893 | 0 | lending-library S1E5 | premium |  | 0 / 0 |  |
| 856 | lending-library-s1e6-three-thin-volumes | Three Thin Volumes | Üç İnce Cilt | Fantasy | B1 | 827 | 0 | lending-library S1E6 | premium |  | 0 / 0 |  |
| 857 | lending-library-s1e7-birds-of-the-estuary | Birds of the Estuary | Nehir Ağzı Kuşları | Fantasy | B1 | 932 | 0 | lending-library S1E7 | premium |  | 0 / 0 |  |
| 858 | lending-library-s1e8-tide-tables-1988 | Tide Tables 1988 | Gelgit Tabloları 1988 | Fantasy | B1 | 879 | 0 | lending-library S1E8 | premium |  | 0 / 0 |  |
| 859 | lending-library-s1e9-the-lending-book | The Lending Book | Veresiye Defteri | Fantasy | B1 | 924 | 0 | lending-library S1E9 | premium |  | 0 / 0 |  |
| 860 | lending-library-s1e10-the-ninth-of-april | The Ninth of April | Dokuz Nisan | Fantasy | B1 | 1004 | 0 | lending-library S1E10 | premium |  | 0 / 0 |  |
| 839 | lighthouse-letters-s1e1-the-box-in-the-lighthouse | The Box in the Lighthouse | Deniz Fenerindeki Kutu | Mystery | B1 | 954 | 0 | lighthouse-letters S1E1 | premium |  | 0 / 0 |  |
| 840 | lighthouse-letters-s1e2-a-letter-with-no-name | A Letter with No Name | İsimsiz Bir Mektup | Mystery | B1 | 1012 | 0 | lighthouse-letters S1E2 | premium |  | 0 / 0 |  |
| 841 | lighthouse-letters-s1e3-the-fishermans-daughter | The Fisherman's Daughter | Balıkçının Kızı | Mystery | B1 | 1094 | 0 | lighthouse-letters S1E3 | premium |  | 0 / 0 |  |
| 842 | lighthouse-letters-s1e4-return-to-sender | Return to Sender | Göndericiye İade | Mystery | B1 | 1126 | 0 | lighthouse-letters S1E4 | premium |  | 0 / 0 |  |
| 843 | lighthouse-letters-s1e5-the-second-letter | The Second Letter | İkinci Mektup | Mystery | B1 | 1109 | 0 | lighthouse-letters S1E5 | premium |  | 0 / 0 |  |
| 844 | lighthouse-letters-s1e6-the-house-on-the-cliff | The House on the Cliff | Uçurumdaki Ev | Mystery | B1 | 1214 | 0 | lighthouse-letters S1E6 | premium |  | 0 / 0 |  |
| 845 | lighthouse-letters-s1e7-what-the-postman-knew | What the Postman Knew | Postacının Bildiği | Mystery | B2 | 1162 | 0 | lighthouse-letters S1E7 | premium |  | 0 / 0 |  |
| 846 | lighthouse-letters-s1e8-the-locked-drawer | The Locked Drawer | Kilitli Çekmece | Mystery | B2 | 1219 | 0 | lighthouse-letters S1E8 | premium |  | 0 / 0 |  |
| 847 | lighthouse-letters-s1e9-names-and-dates | Names and Dates | İsimler ve Tarihler | Mystery | B2 | 1303 | 0 | lighthouse-letters S1E9 | premium |  | 0 / 0 |  |
| 848 | lighthouse-letters-s1e10-the-last-letter | The Last Letter | Son Mektup | Mystery | B2 | 1180 | 0 | lighthouse-letters S1E10 | premium |  | 0 / 0 |  |
| 849 | lighthouse-letters-s1e11-the-man-who-never-left | The Man Who Never Left | Hiç Gitmeyen Adam | Mystery | B2 | 1315 | 0 | lighthouse-letters S1E11 | premium |  | 0 / 0 |  |
| 850 | lighthouse-letters-s1e12-high-tide | High Tide | Sular Yükselirken | Mystery | B2 | 1301 | 0 | lighthouse-letters S1E12 | premium |  | 0 / 0 |  |
| 829 | new-in-town-s1e1-box-number-twelve | Box Number Twelve | On İki Numaralı Kutu | Daily Life | A1 | 390 | 0 | new-in-town S1E1 | premium |  | 1 / 1 | 0.0 |
| 830 | new-in-town-s1e2-the-wrong-key | The Wrong Key | Yanlış Anahtar | Daily Life | A1 | 432 | 0 | new-in-town S1E2 | premium |  | 1 / 1 | 0.0 |
| 831 | new-in-town-s1e3-milk-and-bread | Milk and Bread | Süt ve Ekmek | Daily Life | A1 | 427 | 0 | new-in-town S1E3 | premium |  | 0 / 0 |  |
| 832 | new-in-town-s1e4-the-cat-at-the-door | The Cat at the Door | Kapıdaki Kedi | Daily Life | A1 | 435 | 0 | new-in-town S1E4 | premium |  | 0 / 0 |  |
| 833 | new-in-town-s1e5-bus-number-7 | Bus Number 7 | 7 Numaralı Otobüs | Daily Life | A1 | 487 | 0 | new-in-town S1E5 | premium |  | 0 / 0 |  |
| 834 | new-in-town-s1e6-a-name-on-the-mailbox | A Name on the Mailbox | Posta Kutusundaki İsim | Daily Life | A1 | 410 | 0 | new-in-town S1E6 | premium |  | 0 / 0 |  |
| 835 | new-in-town-s1e7-rain-and-an-umbrella | Rain and an Umbrella | Yağmur ve Bir Şemsiye | Daily Life | A1 | 434 | 0 | new-in-town S1E7 | premium |  | 0 / 0 |  |
| 836 | new-in-town-s1e8-the-neighbours-radio | The Neighbour's Radio | Komşunun Radyosu | Daily Life | A1 | 444 | 0 | new-in-town S1E8 | premium |  | 0 / 0 |  |
| 837 | new-in-town-s1e9-saturday-market | Saturday Market | Cumartesi Pazarı | Daily Life | A1 | 384 | 0 | new-in-town S1E9 | premium |  | 0 / 0 |  |
| 838 | new-in-town-s1e10-home | Home | Yuva | Daily Life | A1 | 445 | 0 | new-in-town S1E10 | premium |  | 0 / 0 |  |
| 895 | passport-the-wrong-platform | The Wrong Platform | Yanlış Peron | Travel | A1 | 270 | 0 | passport S1E4 | premium |  | 0 / 0 |  |
| 892 | passport-one-night-in-lisbon | One Night in Lisbon | Lizbon’da Bir Gece | Travel | A2 | 400 | 0 | passport S1E1 | premium |  | 1 / 1 | 1.1 |
| 896 | passport-the-wrong-suitcase | The Wrong Suitcase | Başkasının Bavulu | Travel | B1 | 659 | 0 | passport S1E5 | premium |  | 0 / 0 |  |
| 894 | passport-the-overnight-bus | The Overnight Bus | Yan Koltuktaki Kadın | Travel | B2 | 776 | 0 | passport S1E3 | premium |  | 0 / 0 |  |
| 893 | passport-the-last-ferry | The Last Ferry | Son Vapur | Travel | C1 | 1094 | 0 | passport S1E2 | premium |  | 1 / 0 |  |
| 861 | room-214-s1e1-the-name-on-the-badge | The Name on the Badge | Yaka Kartındaki İsim | Thriller | B1 | 755 | 0 | room-214 S1E1 | premium |  | 0 / 0 |  |
| 862 | room-214-s1e2-the-man-who-never-sleeps | The Man Who Never Sleeps | Hiç Uyumayan Adam | Thriller | B1 | 725 | 0 | room-214 S1E2 | premium |  | 0 / 0 |  |
| 863 | room-214-s1e3-the-luggage-book | The Luggage Book | Ivo’nun İki Çantası | Thriller | B1 | 727 | 0 | room-214 S1E3 | premium |  | 0 / 0 |  |
| 864 | room-214-s1e4-half-past-three | Half Past Three | Gece Üç Buçuk | Thriller | B1 | 708 | 0 | room-214 S1E4 | premium |  | 0 / 0 |  |
| 865 | room-214-s1e5-the-fire-escape | The Fire Escape | Yangın Merdiveni | Thriller | B1 | 736 | 0 | room-214 S1E5 | premium |  | 0 / 0 |  |
| 866 | room-214-s1e6-the-guest-in-302 | The Guest in 302 | 302’deki Konuk | Thriller | B1 | 796 | 0 | room-214 S1E6 | premium |  | 0 / 0 |  |
| 867 | room-214-s1e7-ivo | Ivo | Kayıkhanedeki Kardeş | Thriller | B1 | 779 | 0 | room-214 S1E7 | premium |  | 0 / 0 |  |
| 868 | room-214-s1e8-sunday-comes-on-saturday | Sunday Comes on Saturday | Tersine Soygun | Thriller | B1 | 697 | 0 | room-214 S1E8 | premium |  | 0 / 0 |  |
| 869 | room-214-s1e9-the-tea-tray | The Tea Tray | Çay Tepsisi | Thriller | B1 | 818 | 0 | room-214 S1E9 | premium |  | 0 / 0 |  |
| 870 | room-214-s1e10-check-out | Check-out | Son Hesap | Thriller | B1 | 801 | 0 | room-214 S1E10 | premium |  | 0 / 0 |  |
| 880 | second-chances-s1e1-back-to-millbrook | Back to Millbrook | Millbrook’a Dönüş | Romance | B2 | 792 | 0 | second-chances S1E1 | premium |  | 0 / 0 |  |
| 881 | second-chances-s1e2-the-shop-with-the-green-door | The Shop with the Green Door | Yeşil Kapılı Dükkân | Romance | B2 | 831 | 0 | second-chances S1E2 | premium |  | 0 / 0 |  |
| 882 | second-chances-s1e3-his-handwriting | His Handwriting | Onun El Yazısı | Romance | B2 | 1038 | 0 | second-chances S1E3 | premium |  | 0 / 0 |  |
| 883 | second-chances-s1e4-show-trade | Show Trade | Dükkân Yeniden Açık | Romance | B2 | 1220 | 0 | second-chances S1E4 | premium |  | 0 / 0 |  |
| 884 | second-chances-s1e5-the-kinder-version | The Kinder Version | Hikâyenin Nazik Hâli | Romance | B2 | 1139 | 0 | second-chances S1E5 | premium |  | 0 / 0 |  |
| 885 | second-chances-s1e6-gone-to-good-homes | Gone to Good Homes | İyi Ellere Gitti | Romance | B2 | 1101 | 0 | second-chances S1E6 | premium |  | 0 / 0 |  |
| 886 | second-chances-s1e7-the-rope-and-the-timetable | The Rope and the Timetable | Salıncak ve Tren Saati | Romance | B2 | 1110 | 0 | second-chances S1E7 | premium |  | 0 / 0 |  |
| 887 | second-chances-s1e8-thursday-is-a-meeting | “Thursday Is a Meeting” | “Perşembe Bir Toplantı” | Romance | B2 | 982 | 0 | second-chances S1E8 | premium |  | 0 / 0 |  |
| 888 | second-chances-s1e9-nobodys-name | Nobody's Name | Kimsenin Adı | Romance | B2 | 1076 | 0 | second-chances S1E9 | premium |  | 0 / 0 |  |
| 889 | second-chances-s1e10-the-marks-inside-the-shelf | The Marks Inside the Shelf | Rafın İçindeki İşaretler | Romance | B2 | 1057 | 0 | second-chances S1E10 | premium |  | 0 / 0 |  |
| 890 | second-chances-s1e11-forty-letters-no-envelopes | Forty Letters, No Envelopes | Zarfsız Kırk Mektup | Romance | B2 | 1080 | 0 | second-chances S1E11 | premium |  | 0 / 0 |  |
| 891 | second-chances-s1e12-six-weeks-and-a-stool | Six Weeks and a Stool | Altı Hafta ve Bir Tabure | Romance | B2 | 1146 | 0 | second-chances S1E12 | premium |  | 0 / 0 |  |
| 903 | signal-delivery-for-mr-kim | Delivery for Mr Kim | Bay Kim’e Teslimat | Technology | A2 | 472 | 0 | signal S1E2 | premium |  | 0 / 0 |  |
| 906 | signal-the-old-phone | The Old Phone | Eski Telefondaki Ses | Technology | A2 | 435 | 0 | signal S1E5 | premium |  | 0 / 0 |  |
| 905 | signal-the-group-chat | The Group Chat | Gruptaki Yedinci Numara | Technology | B1 | 824 | 0 | signal S1E4 | premium |  | 0 / 0 |  |
| 904 | signal-followers | Followers | Takipçiler | Technology | B2 | 920 | 0 | signal S1E3 | premium |  | 0 / 0 |  |
| 902 | signal-autocomplete | Autocomplete | Otomatik Tamamlama | Technology | C1 | 1147 | 0 | signal S1E1 | premium |  | 0 / 0 |  |
| 915 | spotlight-the-singer-in-the-cafe | The Singer in the Cafe | Kafedeki Şarkıcı | Entertainment | A2 | 481 | 0 | spotlight S1E5 | premium |  | 0 / 0 |  |
| 911 | spotlight-the-autograph | The Autograph | 1994’ten Kalan İmza | Entertainment | B1 | 703 | 0 | spotlight S1E1 | premium |  | 0 / 0 |  |
| 912 | spotlight-the-extra | The Extra | Figüran | Entertainment | B1 | 719 | 0 | spotlight S1E2 | premium |  | 0 / 0 |  |
| 913 | spotlight-the-interview | The Interview | Röportaj | Entertainment | B2 | 925 | 0 | spotlight S1E3 | premium |  | 0 / 0 |  |
| 914 | spotlight-the-piano-upstairs | The Piano Upstairs | Üst Kattaki Piyano | Entertainment | C1 | 1107 | 0 | spotlight S1E4 | premium |  | 0 / 0 |  |
| 871 | why-bread-goes-stale | Why Does Bread Go Stale? | Ekmek Neden Bayatlar? | Science | B1 | 598 | 0 | why S1E1 | premium |  | 0 / 0 |  |
| 874 | why-mirrors-are-slightly-green | Why Are Mirrors Slightly Green? | Aynalar Neden Yeşilimsi? | Science | B1 | 516 | 0 | why S1E4 | premium |  | 0 / 0 |  |
| 875 | why-old-photos-turn-orange | Why Do Old Photographs Turn Orange? | Fotoğraflar Neden Sararır? | Science | B1 | 562 | 0 | why S1E5 | premium |  | 0 / 0 |  |
| 876 | why-onions-make-you-cry | Why Do Onions Make You Cry? | Soğan Neden Ağlatır? | Science | B1 | 617 | 0 | why S1E6 | premium |  | 0 / 0 |  |
| 877 | why-planes-leave-white-lines | Why Do Planes Leave White Lines? | Uçaklar Neden İz Bırakır? | Science | B1 | 551 | 0 | why S1E7 | premium |  | 0 / 0 |  |
| 878 | why-roads-have-cracks-in-lines | Why Do Roads Have Lines Across Them? | Yoldaki Çizgiler Neden Var? | Science | B1 | 570 | 0 | why S1E8 | premium |  | 0 / 0 |  |
| 879 | why-ships-float | Why Do Steel Ships Float? | Çelik Gemiler Neden Batmaz? | Science | B1 | 661 | 0 | why S1E9 | premium |  | 0 / 0 |  |
| 872 | why-you-cannot-tickle-yourself | Why Can't You Tickle Yourself? | Kendini Neden Gıdıklayamazsın? | Science | B2 | 580 | 0 | why S1E2 | premium |  | 0 / 0 |  |
| 873 | why-some-doors-pull-and-push | Why Do We Push Some Doors and Pull Others? | Bazı Kapılar Neden Dışa Açılır? | Science | B2 | 615 | 0 | why S1E3 | premium |  | 0 / 0 |  |
| 899 | wild-the-bird-on-the-balcony | The Bird on the Balcony | Balkondaki Kuş | Nature | A1 | 288 | 0 | wild S1E3 | premium |  | 0 / 0 |  |
| 901 | wild-the-storm | The Storm | Fırtına | Nature | A2 | 419 | 0 | wild S1E5 | premium |  | 0 / 0 |  |
| 900 | wild-the-garden-next-door | The Garden Next Door | Boş Evin Bahçesi | Nature | B1 | 668 | 0 | wild S1E4 | premium |  | 0 / 0 |  |
| 898 | wild-fire-season | Fire Season | Yangın Mevsimi | Nature | B2 | 839 | 0 | wild S1E2 | premium |  | 0 / 0 |  |
| 897 | wild-a-photograph-of-snow | A Photograph of Snow | Bir Kar Fotoğrafı | Nature | C1 | 1000 | 0 | wild S1E1 | premium |  | 0 / 0 |  |
| 930 | four-seconds-four-seconds | Four Seconds | Dört Saniye | Drama | B1 | 616 | 0 |  | premium |  | 0 / 0 |  |
| 959 | four-seconds-room-eleven | Room Eleven | On Bir Numaralı Oda | Drama | B2 | 582 | 0 |  | premium |  | 0 / 0 |  |
| 957 | four-seconds-the-platform | The Platform | Yirmi Dakika Daha | Drama | B2 | 485 | 0 |  | premium |  | 0 / 0 |  |
| 958 | four-seconds-the-second-page | The Second Page | İkinci Sayfa | Drama | B2 | 541 | 0 |  | premium |  | 0 / 0 |  |
| 917 | kitchen-table-fish-on-friday | Fish on Friday | Küçük Balıklar, Lütfen | Daily Life | A1 | 222 | 0 |  | günlük |  | 2 / 2 | 0.8 |
| 916 | kitchen-table-two-cups | Two Cups | İki Bardak Çay | Daily Life | A1 | 217 | 0 |  | açık |  | 96 / 66 | 1.6 |
| 919 | kitchen-table-salt | Salt | Komşudan Biraz Tuz | Daily Life | A2 | 492 | 0 |  | premium |  | 0 / 0 |  |
| 950 | kitchen-table-the-bowl | The Bowl | Bayan Ana’nın Kâsesi | Daily Life | A2 | 414 | 0 |  | premium |  | 0 / 0 |  |
| 918 | kitchen-table-the-neighbours-pot | The Neighbour's Pot | Komşunun Tenceresi | Daily Life | A2 | 312 | 0 |  | premium |  | 0 / 0 |  |
| 949 | kitchen-table-the-oven | The Oven | Fırının Bozulduğu Perşembe | Daily Life | B1 | 426 | 0 |  | premium |  | 0 / 0 |  |
| 920 | nearly-assembly-required | Assembly Required | Kılavuzsuz Dolap | Daily Life | A2 | 362 | 0 |  | premium |  | 0 / 0 |  |
| 921 | nearly-i-am-good-with-maps | I Am Good with Maps | Kırmızı Kapılı Dükkân | Daily Life | A2 | 315 | 0 |  | premium |  | 0 / 0 |  |
| 922 | nearly-the-shelf | The Shelf | Bir Raf, İki Hikâye | Daily Life | A2 | 378 | 0 |  | premium |  | 0 / 0 |  |
| 952 | nearly-wet-paint | Wet Paint | Dikkat, Boyalı | Daily Life | A2 | 381 | 0 |  | günlük |  | 0 / 0 |  |
| 951 | nearly-the-tent | The Tent | Üç Dakikalık Çadır | Daily Life | B1 | 425 | 0 |  | premium |  | 0 / 0 |  |
| 923 | one-turn-thirty-six-instalments | Thirty-Six Payments | Otuz Altı Taksit | Technology | A2 | 428 | 0 |  | premium |  | 0 / 0 |  |
| 961 | one-turn-the-frame | The Frame | Kırk Yıllık Çerçeve | Family | B1 | 390 | 0 |  | premium |  | 0 / 0 |  |
| 960 | one-turn-the-good-plates | The Good Plates | Misafir Tabakları | Family | B1 | 364 | 0 |  | premium |  | 0 / 0 |  |
| 962 | one-turn-the-tin-teapot | The Tin Teapot | Teneke Çaydanlık | Family | B1 | 366 | 0 |  | premium |  | 0 / 0 |  |
| 925 | shift-the-deposit | The Deposit | Depozito | Work | A2 | 565 | 0 |  | premium |  | 0 / 0 |  |
| 927 | shift-group-project | Group Project | Grup Ödevi | Work | B1 | 602 | 0 |  | premium |  | 0 / 0 |  |
| 926 | shift-overtime | Overtime | Fazla Mesai | Work | B1 | 672 | 0 |  | premium |  | 0 / 0 |  |
| 953 | shift-the-list | The List | Cam Arkasındaki Liste | Work | B1 | 575 | 0 |  | premium |  | 0 / 0 |  |
| 924 | shift-the-rota | The Saturday List | Cumartesi Listesi | Work | B1 | 552 | 0 |  | premium |  | 0 / 0 |  |
| 954 | shift-the-code | The Code | On Dokuz Yıllık Kâğıt | Work | B2 | 590 | 0 |  | premium |  | 0 / 0 |  |
| 929 | the-measure-eleven-minutes | Eleven Minutes | On Bir Dakika | Sports | A1 | 256 | 0 |  | günlük |  | 1 / 1 | 2.1 |
| 956 | the-measure-one-hundred | One Hundred | Altmış Birden Yüze | Sports | A1 | 189 | 0 |  | premium |  | 0 / 0 |  |
| 928 | the-measure-ten-steps | Ten Steps | Denize On Adım | Sports | A1 | 235 | 0 |  | günlük |  | 1 / 0 | 0.0 |
| 955 | the-measure-the-third-lamp | The Third Lamp | Üçüncü Lamba | Sports | A2 | 309 | 0 |  | premium |  | 0 / 0 |  |
| 931 | the-small-hours-the-third-ring | The Third Ring | Üçüncü Zil | Mystery | A2 | 550 | 0 |  | premium |  | 0 / 0 |  |
| 963 | the-small-hours-almond-street | Almond Street | Badem Sokağı | Mystery | B1 | 495 | 0 |  | premium |  | 0 / 0 |  |
| 965 | the-small-hours-pump-four | Pump Four | Dört Numaralı Pompa | Mystery | B1 | 522 | 0 |  | premium |  | 0 / 0 |  |
| 964 | the-small-hours-the-ninth-sack | The Ninth Sack | Dokuzuncu Çuval | Mystery | B1 | 498 | 0 |  | premium |  | 0 / 0 |  |
| 1081 | family-ten-oclock-v2 | Ten O'Clock | Saat On | Family | A2 | 264 | 0 |  | premium |  | 0 / 0 |  |
| 1073 | family-the-photo-nobody-took-v2 | The Photo Nobody Took | Çekilemeyen Fotoğraf | Family | A2 | 280 | 0 |  | günlük |  | 1 / 0 |  |
| 1111 | famous-people-saint-exupery | Saint-Exupéry: The Pilot Who Fell from the Sky | Küçük Prens’i Yazan Pilot | Famous People | B1 | 3150 | 8 |  | premium |  | 0 / 0 |  |
| 1074 | famous-people-bob-dylan-v2 | Bob Dylan: The Singer They Booed | Bob Dylan’ın Yuhalandığı Gece | Famous People | B2 | 452 | 0 |  | premium |  | 0 / 0 |  |
| 1075 | inspiration-the-sea-is-never-still-v2 | The Sea Is Never Still | Yerinde Durmayan Deniz | Inspiration | A2 | 290 | 0 |  | premium |  | 0 / 0 |  |
| 1110 | literature-the-happy-prince | The Happy Prince | Mutlu Prens | Literature | A2 | 1589 | 4 |  | premium |  | 2 / 0 | 0.2 |
| 1033 | literature-shakespeare-made-up-words | Shakespeare: The Man Who Made Up Words | Shakespeare: Kelime İcat Eden Adam | Literature | B1 | 191 | 0 |  | premium |  | 0 / 0 |  |
| 1100 | literature-canterville-ghost | The Canterville Ghost | Canterville Hayaleti | Literature | B2 | 2293 | 3 |  | premium |  | 0 / 0 |  |
| 1102 | literature-lady-with-the-dog | The Lady with the Dog | Köpekli Kadın | Literature | C1 | 2911 | 2 |  | premium |  | 0 / 0 |  |
| 1025 | literature-the-last-leaf | The Last Leaf | Son Yaprak | Literature | C1 | 2347 | 0 |  | premium |  | 0 / 0 |  |
| 1028 | literature-the-necklace | The Necklace | Gerdanlık | Literature | C1 | 2750 | 0 |  | premium |  | 0 / 0 |  |
| 1026 | literature-the-open-window | The Open Window | Açık Pencere | Literature | C1 | 1211 | 0 |  | premium |  | 0 / 0 |  |
| 1027 | literature-the-tell-tale-heart | The Tell-Tale Heart | Gammaz Yürek | Literature | C1 | 2047 | 0 |  | premium |  | 0 / 0 |  |
| 1101 | literature-the-dead | The Dead | Ölüler | Literature | C2 | 2012 | 3 |  | premium |  | 0 / 0 |  |
| 1039 | literature-alice-in-wonderland | Alice's Adventures in Wonderland | Alice Harikalar Diyarında | Literature | A2 | 8615 | 11 |  | premium |  | 0 / 0 |  |
| 1094 | literature-anne-green-gables | Anne of Green Gables | Yeşilin Kızı Anne | Literature | A2 | 7753 | 12 |  | premium |  | 0 / 0 |  |
| 1097 | literature-secret-garden | The Secret Garden | Gizli Bahçe | Literature | A2 | 8259 | 12 |  | premium |  | 0 / 0 |  |
| 1098 | literature-wind-in-the-willows | The Wind in the Willows | Söğütlükteki Rüzgâr | Literature | A2 | 8768 | 12 |  | premium |  | 0 / 0 |  |
| 1096 | literature-wizard-of-oz | The Wonderful Wizard of Oz | Oz Büyücüsü | Literature | A2 | 7558 | 12 |  | premium |  | 0 / 0 |  |
| 1105 | literature-black-beauty | Black Beauty | Siyah İnci | Literature | B1 | 8994 | 14 |  | premium |  | 0 / 0 |  |
| 1099 | literature-christmas-carol | A Christmas Carol | Bir Noel Şarkısı | Literature | B1 | 7022 | 8 |  | premium |  | 0 / 0 |  |
| 1091 | literature-eighty-days | Around the World in Eighty Days | Seksen Günde Devriâlem | Literature | B1 | 10029 | 14 |  | premium |  | 0 / 0 |  |
| 1040 | literature-huckleberry-finn | The Adventures of Huckleberry Finn | Huckleberry Finn’in Maceraları | Literature | B1 | 12258 | 14 |  | premium |  | 0 / 0 |  |
| 1092 | literature-little-women | Little Women | Küçük Kadınlar | Literature | B1 | 10537 | 14 |  | premium |  | 0 / 0 |  |
| 1042 | literature-oliver-twist | Oliver Twist | Oliver Twist | Literature | B1 | 11155 | 14 |  | premium |  | 0 / 0 |  |
| 1095 | literature-peter-pan | Peter Pan | Peter Pan | Literature | B1 | 9116 | 12 |  | premium |  | 0 / 0 |  |
| 1030 | literature-tom-sawyer | The Adventures of Tom Sawyer | Tom Sawyer’ın Maceraları | Literature | B1 | 8835 | 14 |  | premium |  | 0 / 0 |  |
| 1090 | literature-treasure-island | Treasure Island | Define Adası | Literature | B1 | 11702 | 14 |  | premium |  | 0 / 0 |  |
| 1038 | literature-a-tale-of-two-cities | A Tale of Two Cities | İki Şehrin Hikâyesi | Literature | B2 | 14131 | 16 |  | premium |  | 0 / 0 |  |
| 1031 | literature-frankenstein | Frankenstein | Frankenstein | Literature | B2 | 10737 | 16 |  | premium |  | 0 / 0 |  |
| 1041 | literature-jane-eyre | Jane Eyre | Jane Eyre | Literature | B2 | 12975 | 14 |  | premium |  | 0 / 0 |  |
| 1044 | literature-the-time-machine | The Time Machine | Zaman Makinesi | Literature | B2 | 11333 | 14 |  | premium |  | 0 / 0 |  |
| 1093 | literature-persuasion | Persuasion | İkna | Literature | C1 | 12653 | 12 |  | premium |  | 0 / 0 |  |
| 1043 | literature-pride-and-prejudice | Pride and Prejudice | Gurur ve Önyargı | Literature | C1 | 11911 | 14 |  | premium |  | 0 / 0 |  |
| 1112 | literature-dorian-gray | The Picture of Dorian Gray | Dorian Gray’in Portresi | Literature | C2 | 9156 | 13 |  | premium |  | 0 / 0 |  |
| 1114 | literature-the-great-gatsby | The Great Gatsby | Muhteşem Gatsby | Literature | C2 | 9209 | 9 |  | premium |  | 0 / 0 |  |
| 1113 | literature-wuthering-heights | Wuthering Heights | Uğultulu Tepeler | Literature | C2 | 11216 | 14 |  | premium |  | 0 / 0 |  |
| 1045 | legends-baba-yaga | Baba Yaga | Tavuk Bacaklı Kulübe | Legends | A2 | 446 | 0 |  | günlük |  | 3 / 3 | 1.1 |
| 1046 | legends-john-henry | John Henry | Makineyle Yarışan Adam | Legends | A2 | 364 | 0 |  | premium |  | 0 / 0 |  |
| 1047 | legends-la-llorona | La Llorona | Ağlayan Kadın | Legends | B1 | 442 | 0 |  | premium |  | 0 / 0 |  |
| 1049 | legends-the-flying-dutchman | The Flying Dutchman | Uçan Hollandalı | Legends | B1 | 459 | 0 |  | premium |  | 0 / 0 |  |
| 1050 | legends-the-piper-of-hamelin | The Pied Piper of Hamelin | Fareli Köyün Kavalcısı | Legends | B1 | 475 | 0 |  | premium |  | 0 / 0 |  |
| 1051 | legends-the-selkie-wife | The Selkie Wife | Denizden Gelen Kadın | Legends | B1 | 563 | 0 |  | premium |  | 0 / 0 |  |
| 1053 | legends-urashima-taro | Urashima Tarō | Açılmaması Gereken Kutu | Legends | B1 | 527 | 0 |  | premium |  | 0 / 0 |  |
| 1048 | legends-the-bell-witch | The Bell Witch | Bell Cadısı | Legends | B2 | 577 | 0 |  | premium |  | 0 / 0 |  |
| 1052 | legends-the-wild-hunt | The Wild Hunt | Vahşi Av | Legends | B2 | 516 | 0 |  | günlük |  | 0 / 0 |  |
| 1023 | island-where-rabbits-won | The Island Where Rabbits Won | Haritadan Silinen Ada | Curiosity | A2 | 287 | 0 |  | açık |  | 47 / 33 | 3.3 |
| 1022 | colony-that-left-one-word | The Colony That Left One Word | 117 Kişi, Tek Kelime | Mystery | B1 | 473 | 0 |  | premium |  | 0 / 0 |  |
| 1021 | goldsmith-who-copied-minds | Johannes Gutenberg: The Goldsmith Who Copied Minds | Gutenberg’in Kaybettiği İcat | Famous People | B1 | 437 | 0 |  | premium |  | 0 / 0 |  |
| 1016 | night-the-sky-fell | The Night the Sky Fell | Gökyüzünün Düştüğü Gece | History | B1 | 434 | 0 |  | premium |  | 0 / 0 |  |
| 1019 | the-note-that-opened-the-berlin-wall | The Note That Opened the Berlin Wall | Duvarı Açan Not | History | B1 | 478 | 0 |  | günlük |  | 0 / 0 |  |
| 1024 | village-that-whistles | The Village That Whistles | Islıkla Konuşan Köy | Curiosity | B1 | 281 | 0 |  | günlük |  | 36 / 23 | 1.2 |
| 1018 | night-telegraph-caught-fire | The Night the Telegraph Caught Fire | Telgrafın Tutuştuğu Gece | History | B2 | 467 | 0 |  | premium |  | 0 / 0 |  |
| 1017 | sound-heard-around-the-world | The Sound Heard Around the World | Dünyanın Duyduğu Ses | History | B2 | 411 | 0 |  | premium |  | 0 / 0 |  |
| 1020 | the-man-who-said-no | The Man Who Said No | Hayır Diyen Adam | History | B2 | 489 | 0 |  | premium |  | 0 / 0 |  |
| 1115 | mystery-dracula | Dracula | Drakula | Mystery | B2 | 11008 | 14 |  | premium |  | 0 / 0 |  |
| 1083 | nature-thirty-one-mornings-v2 | Thirty-One Mornings | Her Sabah Aynı Tilki | Nature | A1 | 254 | 0 |  | açık |  | 18 / 14 | 1.2 |
| 1084 | nature-orange-sky-v2 | Why the Sky Turns Orange | Gökyüzü Neden Turuncu Olur? | Nature | B1 | 372 | 0 |  | premium |  | 0 / 0 |  |
| 1082 | nature-the-moon-v2 | The Lamp Nobody Lit | Kimsenin Yakmadığı Lamba | Nature | B1 | 404 | 0 |  | premium |  | 0 / 0 |  |
| 991 | rome-city-built-on-itself | Rome: The City Built on Top of Itself | Katman Katman Roma | Culture | B1 | 435 | 0 |  | premium |  | 0 / 0 |  |
| 992 | rome-fountain-not-a-monument | Rome: The Fountain That Is Not a Monument | Trevi Çeşmesi | Culture | B1 | 469 | 0 |  | premium |  | 0 / 0 |  |
| 990 | rome-city-the-world-built | Rome: The City the World Built | Dünyanın Kurduğu Şehir: Roma | Culture | B2 | 744 | 0 |  | premium |  | 0 / 0 |  |
| 994 | alexandria-lost-library | Alexandria: The City of the Lost Library | İskenderiye’nin Kayıp Kütüphanesi | Culture | B1 | 443 | 0 |  | premium |  | 0 / 0 |  |
| 996 | athens-city-invented-voting | Athens: The City That Voted on Everything | Halkın Hükmü: Atina | Culture | B1 | 434 | 0 |  | premium |  | 0 / 0 |  |
| 1005 | kyoto-never-bombed | Kyoto: The City on the Target List | Kyoto’nun 1945 Yazı | Culture | B1 | 446 | 0 |  | premium |  | 0 / 0 |  |
| 1007 | london-burned-and-rebuilt | London: The City That Burned and Rebuilt Itself | Küllerinden Doğan Şehir: Londra | Culture | B1 | 448 | 0 |  | premium |  | 0 / 0 |  |
| 1008 | petra-carved-from-cliff | Petra: The City Carved from a Cliff | Gül Rengi Şehir: Petra | Culture | B1 | 423 | 0 |  | premium |  | 0 / 0 |  |
| 1011 | timbuktu-books-cost-more-than-gold | Timbuktu: The Real End of the Earth | Dünyanın Öbür Ucu: Timbuktu | Culture | B1 | 460 | 0 |  | premium |  | 0 / 0 |  |
| 1012 | varanasi-city-never-stopped | Varanasi: The City That Never Stopped | Ganj Kıyısında Üç Bin Yıl | Culture | B1 | 423 | 0 |  | premium |  | 0 / 0 |  |
| 1015 | xian-army-under-the-field | Xi'an: The Army Under the Field | Tarlanın Altındaki Ordu | Culture | B1 | 441 | 0 |  | premium |  | 0 / 0 |  |
| 995 | angkor-jungle-took-back | Angkor: The City the Jungle Took Back | Ormanın Yuttuğu Şehir | Culture | B2 | 482 | 0 |  | premium |  | 0 / 0 |  |
| 997 | baghdad-books-weighed-in-gold | Baghdad: The City Behind the Word 'Algorithm' | Bağdat’tan Algoritmaya | Culture | B2 | 476 | 0 |  | premium |  | 0 / 0 |  |
| 998 | cairo-city-that-ate-a-pyramid | Cairo: The City That Ate a Pyramid | Beyaz Piramidin İzinde: Kahire | Culture | B2 | 473 | 0 |  | premium |  | 0 / 0 |  |
| 999 | cusco-built-without-cement | Cusco: The City Built Without Cement | İnkaların Yıkılmayan Duvarları | Culture | B2 | 512 | 0 |  | premium |  | 0 / 0 |  |
| 1000 | damascus-street-called-straight | Damascus: The Street Called Straight | Şam’ın İki Bin Yıllık Caddesi | Culture | B2 | 480 | 0 |  | premium |  | 0 / 0 |  |
| 1001 | florence-city-bankers-built | Florence: The City That Bankers Built | Floransa: Yirmi Dakika, Üç Dahi | Culture | B2 | 506 | 0 |  | premium |  | 0 / 0 |  |
| 1002 | great-zimbabwe-refused-to-believe | Great Zimbabwe: The City Europe Refused to Believe | Avrupa’nın İnanmadığı Şehir | Culture | B2 | 511 | 0 |  | premium |  | 0 / 0 |  |
| 1003 | istanbul-one-city-three-names | Istanbul: One City, Three Names | Tek Şehir, Üç İsim | Culture | B2 | 535 | 0 |  | premium |  | 0 / 0 |  |
| 1004 | jerusalem-city-everyone-wanted | Jerusalem: The City Everyone Wanted | Kudüs’ün Taşınamayan Hazinesi | Culture | B2 | 515 | 0 |  | premium |  | 0 / 0 |  |
| 1006 | lhasa-city-above-the-clouds | Lhasa: The City Above the Clouds | Tibet’te Nefes Almak | Culture | B2 | 471 | 0 |  | premium |  | 0 / 0 |  |
| 1009 | samarkand-prince-counted-stars | Samarkand: The Prince Who Counted the Stars | Yıldızları Sayan Hükümdar Uluğ Bey | Culture | B2 | 468 | 0 |  | premium |  | 0 / 0 |  |
| 1010 | tenochtitlan-city-on-the-lake | Tenochtitlan: The City on the Lake | Azteklerin Göldeki Beyaz Şehri | Culture | B2 | 517 | 0 |  | premium |  | 0 / 0 |  |
| 1013 | venice-standing-on-a-forest | Venice: The City Standing on a Forest | Venedik’in Altındaki Orman | Culture | B2 | 455 | 0 |  | premium |  | 0 / 0 |  |
| 1014 | vienna-where-music-was-a-job | Vienna: The City Where Music Was a Job | Viyana: Müziğin Silikon Vadisi | Culture | B2 | 446 | 0 |  | premium |  | 0 / 0 |  |
| 1109 | literature-blue-carbuncle | The Blue Carbuncle | Mavi Yakut | Literature | C1 | 2874 | 3 |  | premium |  | 0 / 0 |  |
| 1108 | literature-red-headed-league | The Red-Headed League | Kızıl Saçlılar Derneği | Literature | C1 | 3154 | 4 |  | premium |  | 0 / 0 |  |
| 1106 | literature-scandal-in-bohemia | A Scandal in Bohemia | Bohemya’da Skandal | Literature | C1 | 3422 | 4 |  | premium |  | 0 / 0 |  |
| 1107 | literature-speckled-band | The Speckled Band | Benekli Kordon | Literature | C1 | 3462 | 4 |  | premium |  | 0 / 0 |  |
| 1085 | sports-the-bench-v2 | The Bench | Finalde Yedek | Sports | A1 | 251 | 0 |  | günlük |  | 4 / 2 | 1.6 |
| 1029 | sports-sixty-kilos-suleymanoglu | Naim Süleymanoğlu: The Pocket Hercules | Cep Herkülü Naim Süleymanoğlu | Sports | B1 | 5651 | 9 |  | premium |  | 0 / 0 |  |
| 1054 | survival-133-days-alone-at-sea | 133 Days Alone at Sea | Denizde 133 Gün | Survival | B1 | 452 | 0 |  | premium |  | 0 / 0 |  |
| 1055 | survival-forty-one-days-by-the-sun | Forty-One Days by the Sun | Güneşle Kırk Bir Gün | Survival | B1 | 554 | 0 |  | premium |  | 0 / 0 |  |
| 1056 | survival-nine-days-in-the-sahara | Nine Days in the Sahara | Sahra’da Dokuz Gün | Survival | B1 | 485 | 0 |  | premium |  | 0 / 0 |  |
| 1057 | survival-sixty-nine-days-in-the-dark | Sixty-Nine Days in the Dark | Karanlıkta Altmış Dokuz Gün | Survival | B1 | 445 | 0 |  | premium |  | 0 / 0 |  |
| 1058 | survival-the-air-bubble | The Air Bubble | Batıktaki Hava Cebi | Survival | B1 | 551 | 0 |  | premium |  | 0 / 0 |  |
| 1059 | survival-the-girl-who-fell-from-the-sky | The Girl Who Fell From the Sky | Gökten Düşen Kız | Survival | B1 | 474 | 0 |  | günlük |  | 3 / 1 | 2.8 |
| 1060 | survival-the-most-successful-failure | The Most Successful Failure | En Başarılı Başarısızlık | Survival | B2 | 611 | 0 |  | premium |  | 0 / 0 |  |
| 1061 | survival-the-woman-they-hired-to-sew | The Woman They Hired to Sew | Dikiş İçin Tutulan Kadın | Survival | B2 | 619 | 0 |  | premium |  | 0 / 0 |  |
| 1062 | survival-twice-declared-dead | Twice Left for Dead | İki Kez Ölü Sayılan Dağcı | Survival | B2 | 656 | 0 |  | premium |  | 0 / 0 |  |
| 1086 | technology-electric-cars-v2 | The Car That Came Back | Geri Dönen Araba | Technology | B2 | 548 | 0 |  | premium |  | 0 / 0 |  |
| 116 | breakfast-in-new-york | Breakfast in New York | New York’ta Kahvaltı | Daily Life | A1 | 104 | 0 |  | günlük |  | 6 / 6 | 1.4 |
| 124 | first-ramadan-in-london | First Ramadan in London | Londra’da İlk Ramazan | Culture | A1 | 137 | 0 |  | günlük |  | 10 / 9 | 2.9 |
| 118 | sunday-lunch-with-grandma | Sunday Lunch with Grandma | Pazar Sofrası | Family | A1 | 89 | 0 |  | günlük |  | 5 / 5 | 5.1 |
| 140 | a-bus-ride-with-a-stranger | A Bus Ride with a Stranger | Otobüste Bir Yabancı | Inspiration | A2 | 153 | 0 |  | premium |  | 0 / 0 |  |
| 127 | ali's-first-snow | Ali's First Snow | Ali’nin İlk Kar Günü | Daily Life | A2 | 121 | 0 |  | günlük |  | 4 / 4 | 1.4 |
| 137 | no-phone-for-a-day | No Phone for a Day | Telefonsuz Bir Gün | Technology | A2 | 138 | 0 |  | premium |  | 0 / 0 |  |
| 161 | famous-people's-first-jobs | Famous People's First Jobs | Ünlülerin İlk İşleri | Famous People | B1 | 319 | 0 |  | günlük |  | 3 / 2 | 4.6 |
| 128 | grandma's-soup | Grandma's Soup | Büyükannenin Çorbası | Daily Life | B1 | 113 | 0 |  | premium |  | 0 / 0 |  |
| 154 | the-city-of-cats-–-istanbul | The City of Cats – Istanbul | Kedilerin Şehri: İstanbul | Travel | B1 | 372 | 0 |  | premium |  | 0 / 0 |  |
| 146 | the-girl-with-the-yellow-umbrella | The Girl with the Yellow Umbrella | Sarı Şemsiyeli Kız | Daily Life | B1 | 127 | 0 |  | premium |  | 0 / 0 |  |
| 148 | why-italians-love-talking | Why Italians Love Talking | İtalyanların Konuşma Aşkı | Culture | B1 | 388 | 0 |  | premium |  | 1 / 1 | 2.6 |
| 120 | why-penguins-can't-fly | Why Penguins Can't Fly | Penguen Neden Uçamaz? | Nature | B1 | 332 | 0 |  | günlük |  | 84 / 48 | 1.7 |
| 156 | a-train-to-venice | A Train to Venice | Venedik’e Giden Tren | Travel | B2 | 121 | 0 |  | premium |  | 0 / 0 |  |
| 178 | charles-babbage:-the-pioneer-of-computing | Charles Babbage: The Pioneer of Computing | Elektriksiz Bilgisayar | Famous People | B2 | 458 | 0 |  | premium |  | 0 / 0 |  |
| 176 | henry-ford:-the-man-who-changed-america | Henry Ford: The Man Who Changed America | Henry Ford’un 1914 Kışı | Famous People | B2 | 467 | 0 |  | premium |  | 0 / 0 |  |
| 175 | stephen-hawking:-the-world's-finest-mind | Stephen Hawking: Given Two Years to Live | Stephen Hawking’e Biçilen İki Yıl | Famous People | B2 | 463 | 0 |  | premium |  | 0 / 0 |  |
| 143 | the-gift-of-the-magi | The Gift of the Magi | Noel Armağanı | Literature | B2 | 105 | 0 |  | premium |  | 0 / 0 |  |
| 153 | where-are-the-harry-potter-stars-now? | Where Are the Harry Potter Stars Now? | Harry Potter Setlerinde Büyümek | Entertainment | B2 | 395 | 0 |  | premium |  | 0 / 0 |  |
| 988 | two-more-floors | Two More Floors | İki Kat Daha | Work | A2 | 326 | 0 |  | premium |  | 0 / 0 |  |
| 987 | coffee-at-four | Coffee at Four | Sabahın Dördünde Kahve | Work | B1 | 483 | 0 |  | premium |  | 0 / 0 |  |
| 986 | my-umbrella-is-better | My Umbrella Is Better | İki Tür Şemsiye | Daily Life | B1 | 437 | 0 |  | premium |  | 0 / 0 |  |
| 989 | the-last-kilometre | The Last Kilometre | Son Kilometre | Sports | B1 | 449 | 0 |  | premium |  | 0 / 0 |  |
| 985 | the-better-school | The Better School | Daha İyi Okul | Family | B2 | 595 | 0 |  | premium |  | 0 / 0 |  |
| 984 | the-light-in-9b | The Light in 9B | 9B’deki Işık | Mystery | B2 | 672 | 0 |  | günlük |  | 1 / 0 | 0.3 |
| 982 | the-wrong-floor | The Wrong Floor | Yanlış Kat | Drama | B2 | 616 | 0 |  | premium |  | 0 / 0 |  |
| 981 | a-small-debt | A Small Debt | Küçük Bir Borç | Drama | C1 | 774 | 0 |  | premium |  | 0 / 0 |  |
| 980 | eleven-months | Eleven Months | On Bir Ay | Drama | C1 | 786 | 0 |  | premium |  | 0 / 0 |  |
| 983 | night-bus | Night Bus | Gece Otobüsü | Mystery | C1 | 844 | 0 |  | premium |  | 0 / 0 |  |
| 979 | the-loan | The Loan | Faiz Yerine Kek | Drama | C1 | 796 | 0 |  | premium |  | 0 / 0 |  |
| 978 | thirty-years-of-sundays | Thirty Years of Sundays | Her Pazar, Otuz Yıl | Drama | C1 | 717 | 0 |  | premium |  | 0 / 0 |  |
| 1035 | travel-london-eye-v2 | The London Eye | Londra’nın Durmayan Dönme Dolabı | Travel | A1 | 132 | 0 |  | premium |  | 1 / 1 |  |
| 1037 | travel-eiffel-tower-tear-down | The Eiffel Tower They Wanted to Destroy | Yıkılmak İstenen Eyfel Kulesi | Travel | A2 | 174 | 0 |  | premium |  | 0 / 0 |  |
| 1080 | travel-gate-change-v2 | Gate Change | Uçuş Kapısı Değişti | Travel | A2 | 230 | 0 |  | premium |  | 0 / 0 |  |
| 1088 | travel-glacier-express-v2 | The Slowest Express in the World | En Yavaş Ekspres | Travel | A2 | 325 | 0 |  | günlük |  | 1 / 0 | 0.0 |
| 1089 | travel-paris-metro-v2 | The Train with No Driver | Sürücüsüz Tren | Travel | A2 | 321 | 0 |  | günlük |  | 0 / 0 |  |
| 1036 | travel-santorini-the-island-that-exploded | Santorini: The Island That Exploded | Uçurumun Kenarında: Santorini | Travel | A2 | 172 | 0 |  | premium |  | 0 / 0 |  |
| 1087 | travel-british-museum-v2 | The Most Famous Tax Notice in the World | Dünyanın En Ünlü Vergi Belgesi | Travel | B1 | 445 | 0 |  | premium |  | 1 / 0 |  |
| 1034 | travel-istanbul-fifteen-minutes | Istanbul: Fifteen Minutes Between Two Continents | Her Sabah İki Kıta: İstanbul | Travel | B1 | 178 | 0 |  | premium |  | 0 / 0 |  |
