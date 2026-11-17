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


---

## Düzeltme (17 Kas 15:47): ücretsiz sınır dar olmalı
**Mehmet:** 32 metin ücretsiz verilmez. Ücretsiz yolculuk 3–4 metin olur ve hâlihazırda ücretsiz olanlardan kurulur; yoksa satacak bir şey kalmaz. Yukarıdaki "her kullanıcının ilk yolculuğu ücretsiz" önerisi **geri çekildi.**

**Yeni yapı:** seviyeye göre 4 duraklık ücretsiz **başlangıç yolculuğu** (yalnız bugün ücretsiz ya da günlük açma havuzundaki metinler), bitince "sıradaki yolculuk" (New in Town / Coffee Shop / Dünya şehirleri) Premium. Son durağın cümlesi satış anıdır.

| Seviye | Başlangıç yolculuğu (kolaydan zora) | Bugünkü durum | Sonra (Premium) |
|---|---|---|---|
| A1 | First Ramadan in London (124) → Two Cups (916) → Thirty-One Mornings (1083) → The Bench (1085) | 2 her zaman açık, 2 günlük havuz | New in Town |
| A2 | Ali's First Snow (127) → The Cat Knows the Time (1070) → Baba Yaga (1045) → The Island Where Rabbits Won (1023) | 1 her zaman açık, 3 günlük havuz | Coffee Shop Stories |
| B1 | The Village That Whistles (1024) → Why Penguins Can't Fly (120) → The Note That Opened the Berlin Wall (1019) → The Girl Who Fell From the Sky (1059) | 4 günlük havuz | Dünya şehirleri |

Notlar: Rabbits içerik incelemesine göre etiketinden zor; A2 yolculuğunun sonuna kondu. Penguins B1 ilk metin olarak düşük bitiriyordu (63'te 23); B1 yolculuğunda ikinci durak.

**Açık karar – günlük açma (`IsDailyUnlock`):** bugün ücretsiz kullanıcı havuzdan günde bir metin açabiliyor. Sean: başlangıç yolculuğu bitince ücretsizin tek kalan değeri bu; kaldırılırsa sınır gerçekten dar olur. Nassim: ödemeyen kullanıcıyı uygulamada tutan tek şey olabilir; kaldırmak dönüşü düşürebilir. Mehmet'in kararı.

---

## Tur (17 Kas 15:54): günde bir ücretsiz durak, yolculuğun içinde
**Mehmet:** Günlük ücretsiz sistemi yolculuğun içinde kullanalım; ücretsiz kullanıcı sıradakinin açılması için ertesi günü bekler.

**Ekip:** Uygun. Önceki "bekleme yok" önerisi herkese yönelikti; burada bekleme ücretsiz planın açık sınırı ve Premium onu kaldırıyor. Dürüst bir takas (README madde 9): sahte geri sayım yok, sınır baştan söylenir.
- **Sean:** Satış anı her gün kendiliğinden doğar: metni bitiren, en istekli anında "Sıradaki durak yarın açılır · Premium'la şimdi devam et" görür. Yolculuk sonunda bir kez değil, her gün.
- **Don:** Ücretsiz kullanıcı için ertesi gün dönmek için gerçek bir sebep olur. Ertesi sabah "durağın açıldı" bildirimi uydurma değil, doğru bir haber.
- **Nate:** İlk gün iki metin bitirenler daha çok dönüyor (7/11, az veri). İlk günü bir metinle kesmek bunu bozabilir.
- **Nassim:** Ücretsiz kullanıcı yolculuğu yavaş da olsa bitirebilir; sınırın içerikte mi hızda mı olduğu karara bağlanmalı.

**Kararı bekleyen iki nokta:**
1. **Sınır nerede:** (a) yalnız hız: bütün yolculuklarda ücretsiz günde 1 durak, Premium sınırsız; (b) hız + içerik: ücretsiz günde 1 durak yalnız 4 duraklık başlangıç yolculuğunda, sonraki yolculuklar Premium.
2. **İlk gün:** ilk gün 2 durak açık, sonra günde 1 (Nate'in verisi için).

**Gösterim önerisi (Don, Dieter):** bitiş ekranında sıradaki durak kartı ve cümlesi; ücretsiz kullanıcıda kartın üstünde "Yarın açılır" ve tek ikincil düğme "Premium'la şimdi oku". Geri sayım yok.

---

## Mehmet'in kararı (17 Kas 15:58) ve satış hunisi önerisi
**Karar:** İlk yolculuk 3–4 parça, sırayla, günde bir açılır. Premium'da hepsi açık. Diğer serilerin başı da birkaç durak ücretsiz (günlük hakla açılır), sonrası ücretli. Ücretsiz içerik sayılı. Sıra: değer → yol → ilerlemeyi göster → ikna → satış; kibarca.

**Önerilen huni (ekip):**
| Aşama | Ne olur | Satış anı |
|---|---|---|
| 1. Başlangıç yolculuğu (gün 1–4) | 4 durak, günde 1 | Her bitişte sakin: "Yarın açılır · Premium'la şimdi oku" |
| 2. Değer anı (başlangıç bitince) | İlerleme kartı: biten durak, deftere eklenen kelime, okunan gün; yeterli veri varsa bakış oranının düşüşü | **Ana teklif:** 7 günlük ücretsiz deneme, "bütün yolculuklar açılsın" |
| 3. Seviye yolculuğu (New in Town / Coffee Shop / Şehirler) | İlk 2 durak ücretsiz, günlük hakla | **İkinci teklif:** 3. durak; dizilerde hikâyenin en merak edilen yerinde |
| 4. Ücretsiz kalan kullanıcı | Günlük hak devam eder; yeni yolculukların ilk 2 durağı | Günde en çok bir teklif |

**Ücretsiz bütçe (öneri):** başlangıç 4 + üç seviye yolculuğunun ilk 2'şer durağı = 10 metin; yeni yolculuklar eklendikçe her birinin ilk 2 durağı.

- **Sean:** Satış iki doruk anda: değeri gördüğü an (aşama 2) ve hikâyeye bağlandığı an (aşama 3). Deneme teklifi aşama 2'de.
- **Nate:** Gösterilecek ilerleme yalnız doğru olanı: durak, kelime, gün. "Daha az kelimeye bakıyorsun" en az 5 metinden sonra ve gerçekten düşüyorsa gösterilir.
- **Don:** Günde en çok bir teklif (uygulamada oturum başına bir kesinti kuralı zaten var). Her teklifte ücretsiz yol görünür: "Yarın devam et".
- **Nassim:** 2 durak, 4 durak, 10 metin tahmin. Her satış anında gösterim → satın alma ölçülür; 4 hafta sonra sınır ayarlanır.

**Mehmet'ten:** seviye yolculuklarında kaç durak ücretsiz (öneri 2) ve deneme teklifi aşama 2'de mi.
