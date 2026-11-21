# Akşam turu: unutulan işler, kararlar ve ekibin işleri

**Tarih:** 21 Kasım 2026, 20:30 · Tek geçiş; üyeler kurgusaldır.
**Mehmet (20:16):** "Bu işlerin hepsi hemen sırayla yapılsın." Konu: konuşulup yapılmayan ya da karara bağlanmadan kalan işler (kariyer yolu, ana sayfa yolculuk kartı, UI/UX incelemesi ve öbürleri).
**Bu söz, 12:12'deki "sürümden önce başka iş eklenmez" kuralının üstündedir.** Aşağıdaki uygulama işleri derleme 50'ye girer. Editörün sıralı görevi: `ortak/editor_gorevi_2026-11-21_aksam.md`.

## 0. Neden kaldılar (ders)
Kalan işlerin çoğu "karar Mehmet'te" diye bırakılmıştı (E1/E2, kart gövdesi, yorum ekranı). Mehmet'in kuralı açık: ürün kararını ekip verir, sonucu raporlar. **Bundan sonra iş listesinde "karar Mehmet'te" yazılmaz.** Mehmet'e yalnız canlıya yazma, sunucu ve mağaza yayını, fiyat ve silme sorulur. Ayrıca her editör görüntüsü Mehmet'e gitmeden önce Dieter ve Don'dan geçer.

## 1. UI/UX incelemesi (Dieter, Don)
İncelenenler: `ekran_2026-11-21/kariyer_pano.png`, `kariyer_buyuk_yazi_ve_esik.png`, `guncelleyen_kullanici_pano.png`.

### 1a. Kariyer sayfası: **E1 seçildi** (Mehmet 20:28 ile düzeltildi; bkz. 1a-2)
- **Neden E1:** E2'deki kemer biçimli eşik, o boyutta mıknatıs ya da nal gibi okunuyor. Kilitler kalktığı ve sıradaki rütbe halkayla öne çıktığı için ek işarete gerek yok (Dieter). Kullanıcı neye bakacağını E1'de de buluyor (Don).
- **Mehmet'in 12:06 isteği karşılanıyor:** yol rozetin kenarından çıkıyor, öbür rozetin kenarında bitiyor. Hiçbir nokta rozetin altından ya da üstünden geçmiyor (`mockup/career-readability`).
- **E1 ile birlikte düzeltilecekler:**

| # | Gözlem | Karar |
|---|---|---|
| K1 | Büyük yazıda kayıt kartı üç satıra çıkıyor, Çaylak rozetinin yarısını ve adını örtüyor | Büyük yazıda kart tek satır: simge, "İlerlemeni güvene al ›", ×. Alt satır yalnız normal yazıda. Kart hiçbir boyutta kullanıcının bulunduğu rozeti örtmez (testle kilitli) |
| K2 | Kayıt kartının × düğmesi yaklaşık 24 × 24 pt | Dokunma alanı 44 × 44 pt (görünen simge aynı kalabilir) |
| K3 | Dolum az olunca (277 XP, %11) bayrak rozetle yolun arasına sıkışıyor | Bayrak, rozet kenarına 24 pt'den yakın olamaz. Dolum ucu daha yakındaysa bayrak 24 pt'de durur; dolum çizgisi yine gerçek yerinde |
| K4 | Üst alanın altında rozeti görünmeyen bir rütbenin adı yalnız kalıyor ("Kelime Avcısı") | Ad ve rozet birlikte görünür ya da birlikte gizlenir |
| K5 | Büyük yazıda alt şerit iki satıra çıkıyor | Kabul. İki satırda kalabilir |

- **Değişmeyenler:** eşikler (20/350/1.000 sunucu değişikliğidir; sonraki sürümün işi olarak kalır), rütbe adları, rozet çizimleri.

### 1a-2. Mehmet'in düzeltmesi (20:28) ve Dieter–Don ortak çalışması
**Mehmet:** kapı olmasın. Rozetin etrafındaki doluluk dairesine gerek yok, yol zaten gösteriyor. Yolda yüzde görünsün. UI ve UX sorumluları birlikte çalışsın; gördükleri sorunları ve daha iyi fikirleri çözümüyle söylesinler.

**Kesinleşen (Mehmet):**
- E2'nin kapısı ve eşik işareti yok.
- Sıradaki rozetin çevresindeki dolan halka kalkar. Sıradaki rütbe yarı renkli rozetle ve "Sıradaki: Meraklı" etiketiyle ayrışır; uzak rütbeler küçük ve soluk kalır.
- **Yolda yüzde:** dolumun ucundaki bayrak yüzdeyi taşır ("%11"). İlerlemeyi gösteren tek yer yoldur.

**Dieter ve Don'un birlikte bulduğu sorunlar ve çözümleri:**
| # | Sorun | Çözüm | Kim |
|---|---|---|---|
| D1 | Mehmet'in halka için söylediği alt şerit için de geçerli: şeritteki ince ilerleme çubuğu yolun gösterdiğini üçüncü kez gösteriyor | Şeritteki çubuk kalkar. Şeritte yalnız eylem cümlesi kalır: "Meraklı'ya yaklaşık 5 günlük okuma kaldı" (60 XP ve altında "Meraklı olmana çok az kaldı!"). Yüzde yolda, gün şeritte; ikisi aynı şeyi tekrarlamaz | Dieter |
| D2 | Yüzde etiketi rozete ya da rütbe adına binebilir (dolum %90'ı geçince uç sıradaki rozete yaklaşır; %5'in altında ise geçilen rozete) | Etiket hiçbir rozetle ve adla çakışmaz. Yolun bir yanında yer yoksa öbür yanına geçer. Bayrağın 24 pt kuralı (K3) yalnız bayrak simgesi için geçerli; yüzde, dolumun gerçek ucunu gösterir | Dieter |
| D3 | Rütbe yeni kazanılmışken yol "%0" diyor; kutlamanın hemen ardından sıfır görmek kazanımı siliyor (ses kuralı 2) | Dolum %0 iken etikette sayı yerine "Yeni yol başladı" yazar. İlk XP ile yüzdeye döner | Don |
| D4 | Yüzde küçük ve renkli yazılırsa zeminde okunmaz; büyük yazıda yolun üstünde taşar | Etiket beyaz zemin üstünde koyu yazı, en az 13 pt kalın, karşıtlık 4,5:1'in üstünde. Büyük yazıda 17 pt'de sabitlenir (yolu kapatmasın) | Dieter |
| D5 | Kullanıcı yeniden geldiğinde ne kadar ilerlediğini görmüyor; sayfa hep son hâliyle açılıyor | Sayfa açılırken dolum, son açılışından bu yana eklenen kısmı 0,6 saniyede doldurur; yüzde de birlikte sayar. Yalnız XP değiştiyse ve bir kez; "hareketi azalt" açıksa animasyon yok | Don |
| D6 | Halka kalkınca sıradaki rozet dokunulabilir mi, belli değil | Halka dokunma işaretiydi, değildi; rozet bugün dokunuluyorsa davranış aynı kalır, dokunulmuyorsa ekleme yapılmaz. **Editör koddan bakar**, raporlar | Don |
| D7 | Ekran okuyucu yolu ve yüzdeyi duyurmuyor olabilir | Yolun erişilebilirlik etiketi: "Meraklı'ya giden yolun yüzde 11'i. Yaklaşık 5 günlük okuma kaldı." Editör bugünkü etiketi koddan döker | Don |

**Bu turda yapılmayan (ikisi de kabul):** rozete dokununca rütbenin ne getirdiğini anlatan pencere. Önce rütbenin bugün bir şey açıp açmadığı koddan bakılmalı; bir şey açmıyorsa anlatacak bir şey de yok. Sonraki sürümün işi.

### 1b. Ana sayfa yolculuk kartı ve güncelleyen kullanıcı
| # | Gözlem | Kim | Karar |
|---|---|---|---|
| G1 | Yolculuk sayfasına yalnız küçük "Yolculuğunu gör ›" bağlantısı ve ince çizgi götürüyor; kapağa, ada ya da süreye dokunmak hiçbir şey yapmıyor (Mehmet, 00:25) | Don | **Editörün önerisi kabul:** kartın düğme dışındaki bütün gövdesi yolculuk sayfasını açar. Turuncu düğme olduğu gibi sıradaki hikâyenin kapağına gider. Görünüm değişmez. Olay: `journey_page_shown`, kaynak `home_card_body` |
| G2 | Günlük hak kullanılmışken ana sayfa kartındaki tek düğme "Premium'la şimdi oku". Yolculuk sayfasında ücretsiz yol var ("Yarın hatırlat", S1), ana sayfada yok | Don | Kural aynı: teklif olan her ekranda ücretsiz yol aynı görünürlükte. Kartta Premium düğmesinin altına yolculuk sayfasındakiyle aynı beyaz "Yarın hatırlat" düğmesi gelir. Kart uzar; kabul |
| G3 | Altı hikâye okumuş kullanıcının kartı "Senin yolculuğun · 0/12" diyor; çizginin 12 dilimi de boş. Sıfırdan başlamış gibi duruyor, 12 de uzak bir sayı (ses kuralı 3) | Dieter, Paul | Hiç hikâye okunmamış bir yolculukta sayı yazılmaz; başlık "Senin yolculuğun · {yolculuğun adı}" olur ("Kafe Hikâyeleri"). İlk hikâyeden sonra "1/12" gelir. Başlangıç yolculuğunda (n/4) değişiklik yok |
| G4 | Güncellemeden sonraki ilk açılışta "Yeni hikâye gelince haber verelim mi?" penceresi ana sayfayı örtüyor | Don | Kabul: bir kez çıkıyor, teklif değil |
| G5 | İkinci yolculukta "İlk hikâyeni aç" | – | Düzeltildi (`d2228a73`) |

### 1c. Ana sayfanın sadeleşmesi
Sadık kullanıcılar raporunun asıl bulgusu: giden altı kişinin dördü son ziyaretinde uygulamayı açtı ve **ana sayfadan hiçbir metne girmeden** çıktı. K1–K7 kararlarında ana sayfa için madde yoktu; bu bir eksikti.
**Karar:** editör, kariyer taslağındaki yöntemle (ayrı dal, gerçek ekran, aynı kullanıcı durumu) ana sayfanın iki sade hâlini çizer. **A:** kişi kartı ile yolculuk kartı tek kartta (rütbe satırı kartın üstünde tek satır). **B:** ilk ekranda yalnız yolculuk kartı ve sıradaki hikâye; kişi kartı ve öbür kartlar altta. Hangi kartların bugün var olduğu önce koddan dökülür (ilk hafta sayacı dahil). Ekip veriyle seçer. Derleme 50'ye girmez; seçim yayından sonraki ilk düzeltme sürümüne.

### 1d. Yorum ekranı (T3)
Ekip 19 Kasım'da uygun bulmuştu; iş Mehmet'in "olur"unu beklerken kaldı. **Karar: derleme 50'ye girer.** Şart: SE 3'te ilk yorumun tamamı ve "Devam" kaydırmadan görünür; yorumlar kelimesi kelimesine ve takma adlı, kaynağı yazılı ("App Store yorumu · 5★" / "Google Play yorumu · 5★").

## 2. "Geri dön" bildirim metinleri (Paul)
Veri: 185 gönderim, 1 dokunma (`2026-11-21_kanal_ve_bildirim_verisi.md` 2.1). Bugünkü metinler genel ("Her şey bıraktığın gibi") ve "çay molası" gibi aynı imgeyi tekrarlıyor. Yeni metinler **somut bir sonraki adımı** söylüyor: sıradaki hikâyenin adı ve süresi (K2 notu). Başlıklar 40 karakteri geçmez; "{ad}, …" kuralı bugünkü gibi.

| Gün | Başlık | Gövde | Sıradaki hikâye bilinmiyorsa |
|---|---|---|---|
| 3 | {hikâye} seni bekliyor | Kaldığın yerden, {dk} dakikalık bir hikâye. | Başlık: "Kısa bir hikâye okuyalım mı?" · Gövde: "Seviyene göre {dk} dakikalık hikâyeler var." |
| 7 | Bir haftadır görüşmedik | Sıradaki hikâyen hazır: {hikâye}. Defterindeki kelimeler de yerinde. | Gövde: "Seviyene göre yeni bir hikâye seçtik. Beş dakika yeter." |
| 14 | Yolculuğun yerinde duruyor | {hikâye}, {dk} dakika. Ne zaman istersen oradan devam. | Başlık: "Hikâyelerin yerinde duruyor" |
| 30 | Kapı hep açık | Kaldığın yerdeyiz. {hikâye} seni bekliyor. | Gövde: "Kaldığın yerdeyiz. Kısa bir hikâyeyle başlayabilirsin." |

- {hikâye}: sunucunun o kullanıcı için sıradaki dediği metin (yolculuğun sıradaki durağı; yarım bir kitap varsa o kitap). Başlık 40 karakteri geçiyorsa "Sıradaki hikâyen seni bekliyor" yazılır.
- Dokunulunca uygulama ana sayfaya değil **o hikâyenin kapak sayfasına** açılır (1.0.4'te; 1.0.2'de ana sayfaya). Editör bunu kodda doğrular, yoksa ekler.
- Ses kuralları: suçlama yok, sayı yok, geri sayım yok. "Seni özledik" gibi duygu sömürüsü de yok.

## 3. Günün quizi: yeniden tasarım kararları (Charles, Don, Dieter, Paul, Nate)
Veri (`2026-11-21_seviye_quiz_guncelleme_verisi.md` bölüm 3) sabahki varsayımlardan birini çürüttü:

| # | Sabahki öneri | Veri | Karar |
|---|---|---|---|
| Q1 | Quiz seviyeye göre olsun | Skor seviyeye göre değişmiyor: A1'de ortalama 7,6, B2'de 7,3; 173 turda 5'in altı yalnız 4 kez | **Yapılmaz.** Herkese aynı sorular kalır, "Herkesle aynı sorular" cümlesi de kalır. Yarım bırakılan turlar ölçülünce (Q7) yeniden bakılır |
| Q2 | Çeldiriciler kötü | Şıkları uygulama üretiyor; en az uzunluk ve tür denetimi yok. İki harfli karşılıklar (an, el, ev, iş, ağ…) şık olunca anlamsız görünüyor. Sunucu "doğru karşılık bu metinle başlıyor mu" diye de kabul ediyor | Şık en az 3 harf. Çeldirici doğru cevapla aynı türden (sıfata sıfat, isme isim); türü bilinmeyen kelime çeldirici olmaz. Kısa karşılıklı kelime soru olabilir, çeldirici olamaz. Sunucuda "ile başlıyor" kabulü kalkar, tam eşleşme. Gösterilen şıklar olaya yazılır |
| Q3 | Sonuç ekranı dev "3/10" ile açılıyor | – | Ses kuralı 2. Başlık skor değil: 8 ve üstü "{d}/10, harika gidiyorsun." · 5–7 "{d} kelimeyi bildin, {y} yeni kelimeyle tanıştın." · 4 ve altı "{y} yeni kelimeyle tanıştın, yarın yine buradayız." "Kaçırdıkların" başlığı "Yeni tanıştıkların" olur |
| Q4 | Ana düğme "Yeniden başla" | – | Yanlış varsa ana düğme "Yeni kelimeleri deftere ekle", yoksa "Sıradaki hikâye". "Yeniden başla" ikincil metin bağlantısı olur. **Önce koda bakılır:** toplu ekleme yoksa ana düğme "Sıradaki hikâye" olur, satırlardaki var olan "ekle" kalır. Defter sınırına çarpan ücretsiz kullanıcı bugünkü sınır metnini görür |
| Q5 | 3/10'dan hemen sonra "Haftalık Şampiyon" | Rozet hafta sonunda değil, o an önde olana veriliyor; pazartesi 227 XP ile de alınmış, aynı hafta iki kişi almış | Rozet hafta kapanınca (pazar 23:59, Türkiye saati) haftanın en yüksek XP'li tek kişisine verilir. Şart: o hafta en az 10 katılımcı ve en az 300 XP. Metin ancak o zaman doğru olur (ses kuralı 8) |
| Q6 | Quiz sekmesinde "#49" anlamsız, halkalar açıklamasız, orta boş | – | Numara kalkar. Halkaların üstüne "Bu hafta" yazılır; çözülen günde dolu halka. Boşluk daralır |
| Q7 | Giriş ölçülmüyor | – | Olaylar: `daily_quiz_started`, `daily_quiz_completed` (skor, süre), `daily_quiz_abandoned` (kaçıncı soruda). Var olan olaylar önce koddan dökülür, olmayan eklenir |

## 4. Seviye denetimi (Paul, Charles) – ilk tur
Dosya: `veri_2026-11-21/A1_A2_seviye_denetimi.csv` (84 metin: kelime, cümle başına kelime, yan cümle, sıklık dışı kelime oranları, nadir kelime örnekleri). Betikle ölçüldü, sonra okunarak bakıldı.

**Ölçüm hakkında dürüst not:** sıklık listesiyle hesaplanan "nadir kelime oranı" bu metinlerde işe yaramıyor. Web metinlerinden çıkan liste "coffee, kitchen, grandmother" gibi gündelik kelimeleri nadir sayıyor; kullanıcının dokunma oranıyla ilişkisi ters çıktı (8 metin, r = −0,53). Kelime zorluğu için insan okuması gerekiyor. Cümle uzunluğu güvenilir.

**Bulgular:**
1. **A1 sağlam görünüyor.** 24 metnin hepsinde ortalama cümle 9 kelimenin altında (ortanca 6,2; hedef ~8). Uzunluk 89–475 kelime.
2. **"A2 metinleri ortalama 1.150 kelime" sözü yanıltıcıydı.** 69.091 kelimenin 46.546'sı 6 klasik uyarlamadan geliyor. Kalan 54 metnin ortalaması yaklaşık 420 kelime, A2 ortancası 405.
3. **Altı klasik uyarlama A2 etiketli ama A2 değil:** The Wonderful Wizard of Oz, The Wind in the Willows, The Secret Garden, The Jungle Book, Alice's Adventures in Wonderland, Anne of Green Gables. Her biri 5.600–8.750 kelime. Ortalama cümle 12,5–16,8 kelime (Anne 12,5; Alice 14,3; Secret Garden 15,6; Jungle Book 15,8; Willows 16,7; Oz 16,8). A2 hedefi ~10. Oz'da 451 cümlenin 128'i 20 kelimeyi aşıyor; "and … and …" ile bağlanmış 80–94 kelimelik cümleler var. Kelimeler sade, cümleler değil. Henüz hiçbir müşteri açmamış; zarar yok, ama A2 kullanıcısına önerilirse ilk sayfada bırakılır. **Karar:** etiket B1 olur. Cümle bölme (A2'ye indirme) sonraki içerik işi; o zaman etiket yeniden bakılır.
4. **Üç kısa A2 metni de B1 düzeyinde:** The Country That Eats Breakfast Twice (ortalama 17,2), The Train with No Driver (15,7; günlük havuzda), The See-Through Umbrella (14,9). Cümleler 27–34 kelimeye çıkıyor, tire ve yan cümleyle. **Karar:** etiket B1 olur.
5. **A2'nin ücretsiz başlangıç hikâyesi The Island Where Rabbits Won en zor A2 başlangıcı:** ortalama cümle 13 (A2 hedefi ~10), beş edilgen yapı (was removed, was chosen, were told…), yan cümleler. Dokunma oranı en yüksek bu metinde (100 kelimede 11,7). 93 kişi başladı; A2 kullanıcısının ilk hikâyesi bu. Bitirme %77 olduğu için bırakılmıyor, ama "zor geldi" e-postasıyla örtüşüyor. **Karar:** aynı hikâye, aynı bilgiler, A2 cümleleriyle yeniden yazıldı (aşağıda; 286 kelime, ortalama cümle ~8, edilgen yok). Yerine konur; çevirisi ve sözlük eşleşmesi editör betiğiyle yenilenir. Ölçüm: yeni metnin bitirme ve dokunma oranı eskisiyle karşılaştırılır.
6. **Kalan iş (Paul, Charles):** A2'de cümle ortalaması 12'yi geçen iki kısa metin daha (A Bus Ride with a Stranger 12,8; The Eiffel Tower They Wanted to Destroy 12,1) okunup karara bağlanacak. En çok okunan 8 metnin kelime denetimi okuyarak yapılacak.

### The Island Where Rabbits Won – A2 yazımı (Paul)
Başlıklar ve hikâye aynı; bilgi çıkarılmadı. "Bilinmeyen hayvanlar öldürüldü" bilgisi yumuşatılmadan sade söylendi.

> A small island in the south of Japan has about nine hundred rabbits. Almost no people live there. Every day, ferries bring visitors. The rabbits run to them, because visitors bring food. The island's name is Ōkunoshima. People also call it Rabbit Island. But for many years, it was not on any map.
>
> **The Secret Island**
> In 1929, the army built a secret factory on the island. The factory made poison gas. The army chose this island because it was small and quiet. It was also far from big cities. The workers could not talk about their work. Maps showed only sea in this place. The factory made gas until the end of the Second World War. Many workers got very sick from it.
>
> **After the War**
> After the war, the factory closed. But the buildings are still there. Their grey walls stand empty today. Trees grow through the old windows. There is a small museum on the island. Visitors can learn the true story there. Where did the rabbits come from? Nobody knows for sure. Some people say children brought eight rabbits to the island in 1971. Other people say the rabbits came from the factory. But an old worker said no. He said the factory killed all its animals at the end.
>
> **Rules for Rabbit Island**
> The rabbits have no enemies on the island, so every year there are more. Now the island has rules for visitors. Do not pick up the rabbits. Do not run after them. Do not give them bread or vegetables, because these make them sick. Dogs and cats cannot go on the ferry. Once, the island was a secret because of a weapon. Today, people come here because of an animal.

## 5. Seviye testleri (Charles)
- **"Seviyeni yeniden ölç" ana sayfa kartından başlatılınca seviyeyi düşürebiliyor.** Sunucuda "yalnız yükseltir" kuralı var ama uygulama işareti göndermiyor (veri raporu 2.1). Bu bir hata. **Karar:** derleme 50'de uygulama işareti gönderir.
- **"Seviyeni belgele" gizli kalır** (derleme 50, T19). Gizli kaldığı sürede: ısınma soruları kolaydan zora sıralanır. Kullanıcının seviyesi A1–A2 ise ısınmadaki B2 sorusu yerine bir A1 sorusu gelir. 176 sorunun tamamını editör döker, Charles ve Paul okur. Satır ancak bundan sonra açılır.
- **Açık soru (olgu, karar değil; editöre soruldu, S1):** Mehmet'in gördüğü "zor boşluk doldurma" hangi testteydi? "Seviyeni belgele"de boşluk doldurma yok; boşluk doldurma "Seviyeni yeniden ölç"te var. Yeniden ölçme testindeyse gizlenen satır yanlış satır olabilir. Ekran görüntüsü varsa iyi olur. Yoksa editör iki testin ilk ekranlarını SE 3'te çeker; ekip görüntüden karar verir.

## 6. Durum tablosu (bu turun sonunda)
| İş | Durum |
|---|---|
| Kariyer E1 + K1–K4 | Karar verildi → editör, derleme 50 |
| Ana sayfa kartı G1–G3 | Karar verildi → editör, derleme 50 |
| Ana sayfa sadeleşmesi | Karar: iki taslak → editör (derleme 50'ye girmez) |
| Yorum ekranı (T3) | Karar verildi → editör, derleme 50 |
| UI/UX incelemesi | Bu raporda yapıldı |
| "Geri dön" metinleri | Yazıldı → editör, sunucu PR |
| Günün quizi Q1–Q7 | Karar verildi; Q1 kapandı → editör (uygulama derleme 50, sunucu PR) |
| Seviye denetimi | İlk tur bitti; etiketler ve Ada metni → editör betiği (canlıya yazma) |
| Seviye testleri | Hata düzeltmesi derleme 50; 176 soru dökümü → editör |
