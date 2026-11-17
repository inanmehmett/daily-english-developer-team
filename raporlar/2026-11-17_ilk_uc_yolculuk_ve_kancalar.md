# İlk üç yolculuk: kararlar, durak sırası ve "sıradaki" cümleleri

**Tarih:** 17 Kasım 2026 · Tek geçiş; üyeler kurgusaldır.
**Kaynak:** durak listesi canlı katalogdan (`raporlar/2026-11-17_katalog.csv`); cümleler metinlerin içe aktarma betiklerindeki gövde ve özetlerden (`DailyEnglish/MigrationScripts/AddNewInTownSeries.sql`, `AddCoffeeShopStories.sql`, `AddCitiesAndCuriosityShelf_2026_08_01.sql`, `AddRomeDocumentaries_2026_08_01.sql`). Canlıdaki gövdelerle birebir aynı olduğu doğrulanmadı.

## Mehmet'in kararları (17 Kas 15:39)
- Üç yolculuk uygun: A1 New in Town, A2 Coffee Shop Stories, B1 Dünya şehirleri.
- Bir yolculuk baştan sona ücretsiz; diğerleri ücretli.
- "Sıradaki" cümlelerini Claude yazar.
- Metin bitince yolculuk ekranı açılıp sıradaki durak orada gösterilsin. Beklemek mi, hemen sıradaki mi: tartışılacak.

## Tartışma ve ekip önerisi
**1. Kullanıcı seçecek mi?** Hayır. Onboarding seviyesi yolculuğu atar; değiştirmek ayarlarda mümkün ama öne çıkmaz (Don, Steve).

**2. Hangi yolculuk ücretsiz?** Yolculuklar seviyeye göre atandığı için "tek ücretsiz yolculuk" herkese aynı olamaz: A1 okura B1 şehirleri ağır, B1 okura New in Town fazla kolay. Öneri: **her kullanıcının ilk yolculuğu baştan sona ücretsiz; sonraki yolculuklar Premium.** Bu üç yolculuğun 32 metni ücretsiz olur (bugün 3 her zaman açık + günlük açma). Sean: Premium'un vaadi somutlaşır ("sıradaki yolculuk"); okur önce değeri yaşar. Nassim: ücretsiz yolculuğu bitirip giden olacak; ama 10 durağı bitiren kullanıcı bugünkünden çok daha fazla değer görmüş olur, ölçülür.
A1 için sorun: New in Town'dan sonra A1'de bütün bir yolculuk yok; A1 okurun ikinci yolculuğu Coffee Shop (A2) olur.

**3. Beklemek mi, hemen sıradaki mi?** Öneri: **hemen sıradaki, bekleme yok.**
- Veri (`2026-11-16_neden_kalmiyorlar.md`): ilk gün iki ve üzeri metin bitirenlerin ertesi gün dönüşü 7/11 (az veri), bir metin bitirenlerin 19/53. İstekli okuru durdurmak için gerekçe yok.
- Yapay bekletme bir kısıt; README madde 9 (sahte kısıt yok).
- Ritmi bekletme değil bildirim kurar: okur durursa ertesi gün "sıradaki durak" hatırlatılır.
- Cümleler bu yüzden "yarın" değil, ne zaman okunursa okunsun geçerli olacak biçimde yazıldı.
- Nassim: hızlı okuyan 10 durağı bir günde bitirip yolculuğun sonuna çabuk varır. Bu, Premium teklifinin doğru anı olabilir; ölçülecek.

**4. Metin bitince ne görünür?** Mehmet'in isteği: yolculuk ekranı açılsın. Don ve Dieter'in önerisi: ayrı bir ekran açmak yerine **bitiş ekranı yolculuk ekranına dönüşsün**: harita ilerlemesi (3/10 → 4/10, mevcut harita animasyonu), altında sıradaki durağın kartı ve cümlesi, tek düğme "Sıradaki durağa geç". Tam yolculuk haritası bu karttan açılır. Bir ekran az, aynı etki. Metin sonu quiz'inin bu akıştaki yeri Don'un tasarımında netleşecek.

**5. Cümle dili:** şimdilik Türkçe. Paul: ileride okurun seviyesinde kısa İngilizce cümleye çevrilebilir (ek okuma). Mehmet'in kararı.

## Durak sırası ve "sıradaki" cümleleri (`NextHook`)
Cümle, o durak bitince sıradaki durağı tanıtır.

### A1 · New in Town (10 durak, dizi sırası)
| # | Durak (id) | Bitince görünen "sıradaki" cümlesi |
|---|---|---|
| 1 | Box Number Twelve (829) | Maya ekmek almaya çıkıyor. Kapı arkasından kapanıyor ve elindeki anahtar yanlış anahtar. |
| 2 | The Wrong Key (830) | Köşedeki küçük dükkânda sessiz bir adam var. Bugün dört kelime söylüyor. Ertesi gün beş. |
| 3 | Milk and Bread (831) | Gri kedi yine kapıda. Maya "Sen benim kedim değilsin" diyor. Kedi hâlâ aynı fikirde değil. |
| 4 | The Cat at the Door (832) | Maya ilk kez şehir merkezine gidiyor. Sokakta iki tane 7 numaralı otobüs var; yalnız biri merkeze gidiyor. |
| 5 | Bus Number 7 (833) | Holde altı posta kutusu var, beşinde isim yazıyor. Maya'nın elinde küçük beyaz bir kart ve bir kalem. |
| 6 | A Name on the Mailbox (834) | Yağmur başladığında Maya evden uzakta ve montsuz. Sonra büyük siyah bir şemsiye geliyor. Ve tabii ki Ben. |
| 7 | Rain and an Umbrella (835) | Her sabah duvarın arkasından eski şarkılar gelirdi. Pazartesi sessiz. Salı da sessiz. |
| 8 | The Neighbour's Radio (836) | Altı hafta önce pazar yeri yalnızca gürültüydü. Bugün o gürültünün isimleri var. |
| 9 | Saturday Market (837) | Soğuk bir pazar akşamı. Bu gece kapalı iki şey açılıyor: bir kapı ve üstünde tek kelime yazan eski bir kutu. |
| 10 | Home (838) | Maya'nın hikâyesi burada bitiyor. Sıradaki yolculuğunda bir kafenin her sabah 8:15'te gelen müdavimi seni bekliyor. |

### A2 · Coffee Shop Stories (12 durak, dizi sırası)
| # | Durak (id) | "Sıradaki" |
|---|---|---|
| 1 | The Empty Chair (817) | Howard masasına geri dönüyor ama nerede olduğunu söylemiyor. Emma'nın aklında tek bir soru var. |
| 2 | Black, One Sugar (818) | Duvardaki eski fotoğraf yere düşüyor. Howard kafenin ilk gününü hatırlıyor, ama her şeyi anlatmıyor. |
| 3 | The First Customer (819) | Saat 7:50 ve mutfağın ışığı kapalı. Yirmi yılda ilk kez Rosa yok. |
| 4 | The Closed Sign (820) | Her salı Howard elinde küçük beyaz çiçeklerle geliyor. Onları hiç suya koymuyor. |
| 5 | Flowers on Tuesday (821) | Bütün sabah yağmur yağıyor. İki turist duvardaki fotoğrafı soruyor ve Howard kimsenin beklemediği üç kelimeyle cevap veriyor. |
| 6 | The Woman in the Photo (822) | Rosa'nın telefonu tezgâhta ters duruyor. Bugün üç kez titriyor ve Rosa ona dokunmuyor. |
| 7 | Rosa's Phone (823) | Howard ilk kez kapanış saatinde geliyor. Masaya eski gözlük kutusunu koyuyor ve açıyor. |
| 8 | The Letter (824) | Sakin, güneşli bir sabah. Emma'nın cebinden eski bir anahtar düşüyor ve Howard'ın ayakkabısının yanında duruyor. |
| 9 | Small Talk (825) | Mavi fincan yirmi yıldır rafta. Bir perşembe sabahı, sekizi beş geçe, Emma'nın elinden kayıyor. |
| 10 | The Broken Mug (826) | Emma bütün gece söyleyeceklerini hazırladı. Ama bu sabah konuşan Howard. |
| 11 | Before Emma (827) | Pazar günü Emma bir gemi boyuyor. Gemi yamuk çıkıyor. |
| 12 | Eight Fifteen (828) | Kafenin hikâyesi burada kapanıyor. Sıradaki yolculuğunda dünyanın en eski şehirlerine gidiyoruz. |

### B1 · Dünya şehirleri (10 durak, önerilen sıra)
Sıra: tanıdık Roma ile açılış, sonra zamanda ve coğrafyada gezinti; kapanış "sabahlarını koruyan şehir" Varanasi.
| # | Durak (id) | "Sıradaki" |
|---|---|---|
| 1 | Rome: The City Built on Top of Itself (991) | Her yıl Trevi Çeşmesi'ne milyonlarca bozuk para atılıyor. Çoğu insan çeşmenin aslında ne olduğunu bilmiyor. |
| 2 | Rome: The Fountain That Is Not a Monument (992) | Demokrasi, tiyatro, felsefe: hepsi tek bir şehirde doğdu. O şehir her şeyi oylamaya koydu, en büyük adamını bile. |
| 3 | Athens (996) | Bir kral boş bir sahile bakıp bir şehir hayal etti. Sonra o şehir dünyadaki bütün kitapları toplamaya çalıştı. |
| 4 | Alexandria (994) | Kayaların arasında bir kilometrelik dar bir yarık. Sonunda kırk metrelik bir tapınak var ve neredeyse hiçbir şey inşa edilmemiş. |
| 5 | Petra (1008) | 1666'da Londra dört gün yandı. Resmî ölü sayısı altıydı ve yangın çok daha büyük bir sorunu sessizce çözdü. |
| 6 | London (1007) | İngilizcede "Timbuktu" dünyanın öbür ucu demek. Gerçek şehir altınını beklenmedik bir şeye harcadı. |
| 7 | Timbuktu (1011) | 1945'te Kyoto bir hedef listesinin en üstündeydi. Bugün ayaktaysa bunu Washington'daki bir adama borçlu. |
| 8 | Kyoto (1005) | 1974'te kuyu kazan çiftçiler topraktan bir insan başı çıkardı. Kilden yapılmıştı ve altında sekiz bin asker bekliyordu. |
| 9 | Xi'an (1015) | Antik şehirlerin çoğu bugün harabe. Biri hariç: üç bin yıldır bir gün bile boşalmadı. |
| 10 | Varanasi (1012) | B1 şehirlerini bitirdin. Yolculuğun devamında 15 şehir daha var; Roma'nın üçüncü parçası da orada. |

## Uygulamaya geçiş (karar Mehmet'in)
- Cümleler canlıda `ReadingTexts.NextHook` alanına yazılacak (bugün 287 metnin hepsinde boş). Bu canlıya yazma işi; Mehmet'in izni ve editörün yedekli betiğiyle yapılır.
- Yolculuk tanımı (hangi metin hangi sırada) kodda ya da yeni bir tabloda tutulacak; editörün tasarım kararı.
- B1 son durağındaki "15 şehir daha" B2 grubunun canlıdaki sayısına (14 şehir + 1 Roma) göre yazıldı.
