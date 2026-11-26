# Üç cephe: teslim paketi, kapaklar, ElevenLabs — ön analiz ve çerçeve plan

**Tarih:** 26 Kasım 2026, gece · **Hazırlayan:** ekip (Steve İşler, Kent Bekçi, Paul Ulus, Tomris Uyum, Charles Kızılağaç, Dieter Koç, Nate Gümüş, Nassim Talip). Üyeler kurgusaldır.
**İsteyen:** Mehmet (26 Kas 23:25): "İki önemli cephede savaş açmamız lazım… Downloads klasöründe büyük bir teslim paketi var; önümüzdeki hafta içinde sisteme yüklenmiş olması lazım. Okuma metinlerinin kapak resimleri yok. Bir de seslendirmede ElevenLabs'e geçiş: öncelikle yeni metinler ve ses kalitesini düşük bulduğumuz mevcut metinler. Üçü de çok büyük iş ama önümüzdeki hafta mutlaka tamamlanması gerek… Sesleri oluşturduktan sonra metin değişirse sesin yeniden üretilmesi gibi maliyet sorunları oluyor. Sağlam bir planlama yapalım; iş sırası ve prensipler; mevcut sistemin detaylı analizi; riskler, olumlu yönler; verilerle ilerleyelim."
**Bu belge ne:** birinci tur. Mehmet'in bilgisayarındaki paket ve kod **doğrudan okunarak** yazıldı. Canlı veritabanına bakılmadı; canlıdan gelmesi gereken her sayı "bilinmiyor" diye işaretli ve editöre soruldu (bölüm 8). İkinci tur (itiraz ve bağımsız göz) bu belgenin üstüne yapılacak; üç işin ayrı planları ondan sonra.

**Okunan kaynaklar**
- Paket: `~/Downloads/ARSIV/TESLIM - TAM PAKET (5 Eki 2026)/` (652 dosya, 632 md, 11 MB; `ARSIV 2` altındaki kopya aynı).
- Sunucu kodu (`DailyEnglish`): `tools/content-importer/`, `tools/cover-generator/`, `scripts/` (ses ve kapak betikleri), `Services/TtsProvider`, `Services/ElevenLabsTtsService`, `Services/GoogleCloudTtsService`, `Services/AudioManifestService`, `Services/VoiceService`, `Server/Helpers/WordTimingPolicy.cs`, `DataAccess/DbModels/SentenceAudioClip.cs`.
- Katalog: `raporlar/2026-11-17_katalog.csv` (287 etkin metin).

---
## 0. En önemli yedi bulgu
1. **Paket kayıtta yok.** Eylül klasörlerindeki 161 adresin (slug) hiçbiri 17 Kasım kataloğunda bulunmuyor. Paket 5 Ekim'den beri bekliyor.
2. **Paket bugünkü kayıt aracına uymuyor.** Kayıt aracı (`import_packages.py`) eski biçimi "birebir" okuyor (`TextLevel`, `## TRANSLATION (TR)`, dört sütunlu kelime tablosu). Eylül paketleri başka biçimde: alan adı `Level`, **Türkçe çeviri bölümü hiç yok**, kelime tablosu üç sütun, çok parçalı ve bölümlü dosyalar var. Paketin kendi rehberi de "importer testi açık iş" diyor.
3. **Paketteki Türkçe ad bizim Türkçe ad değil.** Pakette `SubtitleTR`, İngilizce alt adın çevirisi ("Dinner at Ten → Saat onda akşam yemeği"). Canlıda `SubtitleTR` kartta görünen Türkçe addır. Olduğu gibi yüklenirse kartta "The Clock Is Wrong / Saat Onda Akşam Yemeği" yazar: iki satır ayrı şey söyler. Üstelik 159 metnin yalnız 81'inde bu alan dolu. **Yaklaşık 160 metin için Türkçe ad yazılması gerekiyor** (28 karakter kuralı ve ad kurallarıyla).
4. **Paket 5 Ekim'in kurallarıyla yazıldı; o günden beri kurallar değişti.** Ad ve açıklama kuralları (25 Kas), 28 karakter sınırı, merak cümlesi, seviye denetimi (dokuz metin B1'e çekildi), özel isim listesi, bildirimlerin Türkçe adı kullanması. Paket bu kurallardan geçirilmeden yüklenirse 26 Kasım'da adlarda yaşadığımızın yüz altmış katını yaşarız.
5. **Ses altyapısı düşündüğümüzden hazır.** ElevenLabs bağlantısı kodda duruyor (eski kayıtlar için). Klipler cümle cümle saklanıyor ve cümlenin metnine bağlı: **metin değişince yalnız değişen cümle yeniden üretilir.** Kelime kelime takip, sağlayıcıdan bağımsız bir hizalama betiğiyle üretiliyor (ölçülmüş: ortalama hata 31 ms). Yani yeni sese geçmek metin takibini baştan yazdırmıyor.
6. **Ama ElevenLabs yolu bugünkü hâliyle üretime hazır değil:** model adı eski (`eleven_multilingual_v2`), komşu cümle bağlamı (robot sesin asıl ilacı) üretim kodunda yok, maliyet sabiti eski (1.000 karakter 0,30 dolar varsayıyor) ve en önemlisi **eksik klip kullanıcı metni açınca o an üretiliyor**: pahalı sağlayıcıda bu, kontrolsüz fatura demek.
7. **Kapakların yazısı hazır, resmi yok.** 162 kapak tarifi (Leonardo için, denetlenmiş, ayarlarıyla) pakette. Üretim elle: Leonardo'da tarif başına dört seçenek, birini seçmek, `<slug>.png` adıyla kaydetmek. Kapak dosyaları sunucunun kendi klasöründe duruyor (`wwwroot/images/readingtexts/`); yani **kapak eklemek sunucu yayını gerektiriyor.**

---
## 1. Kapsam: ölçülen ve beyan edilen
| | Sayı | Kaynak | Güven |
|---|---|---|---|
| Canlıda etkin metin | 287 (438.920 kelime, yaklaşık 2,5 milyon karakter) | 17 Kas kataloğu | ölçüldü |
| Paketin beyanı: yeni içerik | 364 | `TESLIM NOTU - 16-23 Eyl.md` | beyan; "içerik" bölüm ve parçaları da sayıyor olabilir |
| Pakette `## META` bloğu (Eylül klasörleri) | 159 | bu analiz | ölçüldü |
| Pakette adres (slug) | 161–174 | bu analiz (iki ayrı sayım) | ölçüldü, fark açıklanmalı |
| Gövdesi okunabilen metin | 160 gövde, 37.270 kelime, 199.102 karakter | bu analiz | **eksik sayım:** benim ayrıştırıcım çok parçalı dosyaların hepsini yakalamıyor |
| Bölümlü yapı | 54 "BÖLÜM" + 44 "CHAPTER" başlığı | bu analiz | ölçüldü |
| Kapak tarifi | 162 | paket | beyan, dosya okundu |
| Ertelenen (gövdesi yok) | 26 metin (Kulvar A/B) | paket rehberi | beyan |
| Teliften çıkarılan | 7 kalem; Peter Pan (kimlik 1095) canlıdan silinecek | paket | beyan; **silme Mehmet'in kararı** |
| Editör kararı bekleyen | 8 madde (bölüm 8.4) | paket | beyan |
**İlk iş kesin envanter:** kaç okuma metni, kaç bölüm, kaç dizi, kaç kelime ve karakter. Bu sayı olmadan ne süre ne maliyet söylenebilir.

---
## 2. Mevcut sistem nasıl çalışıyor
### 2.1 İçerik kayıt hattı
- **Yol:** paket dosyası (.md) → `tools/content-importer/import_packages.py` → SQL betiği (`MigrationScripts`) → önce yerelde, sonra canlıda. Betik adresle korunuyor (yeniden çalıştırılabilir); metinler **etkin olmadan** girer, sezon tamamlanınca tek güncellemeyle açılır.
- **Araçlar:** `import_packages.py` (hikâye ve dizi), `import_books.py` (bölümlü kitap), `import_package_quizzes.py`, `import_book_quizzes.py`, `import_descriptions.py`, `fix_packages.py`, `update_packages.py`, `tools/check_title_tr.py` (Türkçe ad denetimi), `tools/scan_proper_nouns.py`.
- **Kategori koruması:** araç 23 kategori dışında bir şeyi reddediyor (dizi adları kategori diye sızmasın diye).
- **Güçlü yan:** tekrar çalıştırılabilir, etkin olmadan giriyor, daha önce yedi teslimde kullanılmış (`out/` altında yedi SQL).
- **Zayıf yan:** biçimi "birebir" okuyor; alan adı değişince o alanı **sessizce atlıyor**. Eylül biçimi için uyarlanmamış.
- **Çeviri:** eski pakette Türkçe çeviri paketle gelirdi. Eylül paketinde yok. Canlıda cümle çevirisi istek anında çeviri servisinden (DeepL) geliyor ve saklanıyor; kelime balonu sözlükten. 16 Kasım ölçümünde balon doğruluğu %77,6'ydı ve Premium metinlerde elle düzeltme işi (tur04) hâlâ sürüyor. **Yeni 160 metin aynı düzeltme işini doğurur.**

### 2.2 Kapak hattı
- **Alanlar:** metinde `ImageUrl` (dikey kapak, 3:4), `HeroImageUrl` (ana sayfa slaytı için yatay; yoksa dikey kapak kırpılıyor), dizide `CoverImageUrl`.
- **Metin kapağı:** Leonardo AI'da elle üretiliyor. Paketteki ortak ayar: Phoenix, Illustration, 3:4, Alchemy açık, Guidance 7, dört seçenek, aile başına sabit seed; dosya adı `<slug>.png`. Üç görsel aile var: Örnek Levhası (117 tarif), Sessiz Sahne, Koyu Mürekkep.
- **Dizi kapağı:** `tools/cover-generator` (şablondan, yazılı; 560×746). Bu yüzden dizi kartı adı kapakta varsayıyor (26 Kas bulgusu: Game Day).
- **Yayın kapısı:** `scripts/publish_when_covers_land.sh` yalnız kapağı gelmiş metinleri etkinleştiriyor; parça parça kapak teslimine uygun.
- **Dosyalar nerede:** sunucunun `wwwroot/images/readingtexts/` klasöründe; kapak eklemek kod deposuna dosya eklemek ve sunucuyu yayınlamak demek.
- **Mehmet'in bilgisayarında:** Temmuz–Kasım arası on beşten fazla kapak klasörü (en büyüğü "kapak 4", 381 dosya, 3 Eylül); 5 Kasım'da üç dosyalık bir "stil referansı" klasörü. Hangisinin canlıda olduğu, hangisinin deneme olduğu bilinmiyor.
- **Bilinmeyen:** canlıdaki 287 metnin kaçında kapak eksik ya da kırık, kaçında yatay görsel var; 162 tarifin kaçı üretildi.

### 2.3 Ses ve metin takibi hattı
- **Sağlayıcı:** üretimde Google (Chirp 3 HD). Kadroda 24 ses, üç tür (Hikâye, Belgesel, Dizi); varsayılan "Charon". Konuşma hızı 0,94.
- **ElevenLabs:** kodda kayıtlı, "yalnız eski kayıtları çözümlemek için"; varsayılan olarak seçilmiyor. İstek ayarı: `eleven_multilingual_v2`, stability 0,40, style 0,30.
- **Klip yapısı:** her cümle ayrı ses dosyası (kullanıcı istediği cümleden başlatabilsin diye). Kayıt anahtarı: metin, cümle sırası, ses. Dosya adı cümle metninin özetinden (hash) türüyor.
- **Metin değişince:** özet değişir, o cümle için klip bulunamaz, **yalnız o cümle yeniden üretilir.** Cümle eklenip çıkarılınca sıra kayar ama klipler metinden eşleştirilip yeni sıraya taşınıyor.
- **Üretim anı:** kullanıcı metni açınca eksik cümleler o an üretiliyor (`generateMissing`). Yönetim panelinde bu kapatılabiliyor ("kazara ElevenLabs faturası tetiklenmesin diye" notuyla).
- **Kelime kelime takip:** iki yol var. (a) Sağlayıcıdan damga: 24 sesin yalnız 5'inde mümkün ve karakter sayısını 4,5 kat şişiriyor; **kapalı**. (b) Hizalama betiği (`scripts/align-word-timings.py`): üretilmiş sesin kendisinden çıkarıyor, sağlayıcıdan bağımsız, ücretsiz; 404 kelimede ölçülmüş, ortalama hata 31 ms. **Varsayılan bu.** Zamanlama metne değil klibe bağlı saklanıyor; ses değişince zamanlama da yenileniyor.
- **Yerelden canlıya:** `scripts/sync-audio-clips-to-prod.py` yerelde üretilmiş klip kayıtlarını canlıya adres üzerinden taşıyor (ses dosyaları ortak depoda, R2). Yani **toplu üretim yerelde yapılıp canlıya taşınabiliyor**; bu yol denenmiş.
- **Robot ses sorunu, ölçülmüş neden:** her cümle ayrı istekle seslendirildiği için model komşu cümleleri görmüyor. `scripts/context-audition.py` iki çözümü dinletmek için yazılmış: ElevenLabs'te `previous_text / next_text`, Google'da komşularla birlikte seslendirip kesmek. Üretim kodunda ikisi de yok.
- **Maliyet kaydı:** her ücretli çağrı `ExternalApiCost` tablosuna yazılıyor; ama ElevenLabs birim fiyatı kodda 1.000 karakter 0,30 dolar (eski).
- **Geçmişten ders (koddaki not, 12 Eylül):** 17.441 klip satırında özet ile dosya adı uyuşmuyordu; klipler boşuna yeniden üretiliyordu. Sağlayıcıların özet şeması farklı (ElevenLabs ve Google ayrı hesaplıyor). **Sağlayıcı değişiminde en olası gizli maliyet kaynağı bu.**

---
## 3. Üç iş birbirine nasıl bağlı
| Bağ | Sonuç |
|---|---|
| Ses, cümlenin metnine bağlı | **Metin donmadan ses üretilmez.** Donmuş metinde bir cümle değişirse yalnız o cümle yeniden üretilir; ama cümle bölme kuralı ya da noktalama toplu değişirse bütün metin yeniden üretilir |
| Kapak dosya adı = adres (slug) | Adres kayıttan önce kesinleşir ve bir daha değişmez. Kapak, metnin gövdesine bağlı değil; **metin donmasını beklemeden başlayabilir** |
| Türkçe ad kartta, bildirimde ve yolculukta görünüyor | Türkçe adlar yüklemeden önce yazılır; 28 karakter kuralı baştan uygulanır |
| Metinler etkin olmadan giriyor | Yükleme ile yayın ayrı adımlar. Hedef "önümüzdeki hafta sisteme yüklenmiş" ise yükleme yapılır; **yayın, kapağı ve sesi tamamlanan metinler için dalga dalga** |
| Kapak sunucu klasöründe | Her kapak dalgası bir sunucu yayını |
| Kelime takibi klibe bağlı | Ses üretildikten sonra hizalama betiği çalışır; ses yenilenirse o klibin hizalaması da yenilenir (ücretsiz) |
| Yeni metin = yeni kelimeler | Kelime balonu doğruluğu ve çeviri düzeltmesi her yeni metinle büyüyen ayrı bir iş |

---
## 4. Riskler
| No | Risk | Etki | Olasılık | Önlem |
|---|---|---|---|---|
| R1 | Kayıt aracı Eylül biçimindeki alanları sessizce atlar; metinler eksik alanla girer | yüksek | yüksek | Araç uyarlanır; her alan için "okundu / boş" raporu; önce üç dosyalık deneme, sonra tam yükleme. Yalnız yerelde |
| R2 | 160 Türkçe ad ve açıklama kurallardan geçmeden yüklenir | yüksek | yüksek | Adlar ve açıklamalar yüklemeden önce turlu incelemeden geçer; `check_title_tr.py` 28 karakteri denetler |
| R3 | Ses üretildikten sonra metin düzeltmesi gelir | orta (para) | yüksek | "Metin dondu" kapısı: seviye, olgu, yazım, ad, cümle bölme denetimi bitmeden o metnin sesi üretilmez. Sonradan düzeltme tek tek cümle bazında |
| R4 | Sağlayıcı değişiminde özet uyuşmazlığı: klipler bulunamaz, yeniden üretilir | yüksek (para) | orta | Toplu üretimden önce 20 cümlelik deneme: üret, kaydet, yeniden iste, **ikinci istekte sıfır üretim** olmalı |
| R5 | Kullanıcı metni açınca ElevenLabs o an üretir; fatura denetimsiz | yüksek | yüksek (bugünkü kodla) | ElevenLabs sesli metinlerde anlık üretim kapalı; yalnız toplu, yerelde, bütçe sınırıyla. Eksik klipte Google'a ya da sessiz cümle vurgusuna düşülür |
| R6 | Bir hafta üç işin tamamına yetmez | yüksek | yüksek | Dalga: ilk hafta **yükleme tam, kapak ve ses öncelikli küme**; kalan dalgalarla. "Tamam" tanımı Mehmet'le netleştirilir (bölüm 9) |
| R7 | Kapak üretimi elle ve tek kişide (Mehmet) | orta | yüksek | 162 tarif öncelik sırasına dizilir; günlük hedef; seçim ölçütü yazılı (Dieter); mümkünse Leonardo'nun programlı arayüzü ya da tarayıcıyla yarı otomatik üretim araştırılır |
| R8 | Kapak tutarsızlığı: üç aile, eski kapaklarla yan yana | orta | orta | Stil referansı klasörü ve "Kapak Görsel Sistemi v2" tek ölçüt; her dalgada rafta yan yana görüntü denetimi |
| R9 | ElevenLabs fiyatı ve planı bilinmiyor; kodda eski sabit | orta | kesin | Resmî fiyat sayfasından doğrulanır; toplam karakter × fiyat = tavan; plan seçimi Mehmet'in |
| R10 | Ses kalitesi kulağa bırakılır, ölçülmez | orta | orta | Dinleme örneklemi: seviye ve tür başına sabit sayıda cümle; Mehmet'in "düşük kalite" dediği metinlerin listesi yazılı alınır |
| R11 | Hizalama betiğinin dayandığı kütüphane işlevi kaldırılacak (koddaki bakım notu) | düşük | orta | Sürüm sabitlenir; bu hafta engel değil |
| R12 | Kelime takibi yeni seste kayar (sabit sapma sağlayıcıya göre değişir) | orta | orta | Yeni ses için sapma ölçülür (betik zaten kaynak başına düzeltiyor); 1.0.4'te bir metinle gözle doğrulama |
| R13 | 160 yeni metin kelime balonu hatalarını çoğaltır | orta | yüksek | Yükleme ile birlikte özel isim taraması; çeviri düzeltme işi yeni metinler için sıraya alınır; ücretsiz ve başlangıç metinleri önce |
| R14 | Seviyeler: paket kendi ölçümüyle etiketlemiş; biz dokuz metni yeniden etiketlemiştik | orta | orta | Charles örneklemle denetler (seviye başına); yanlış etiket yayından önce düzeltilir |
| R15 | Telif: paket 7 kalemi çıkarmış; çıkarılanların canlıdaki karşılığı silinmeli | yüksek | düşük | Silme listesi Mehmet'e; canlıda telifli metin kalıp kalmadığı sayılır |
| R16 | Üç iş 1.0.4 ölçümünü ve açık işleri (bildirimler, adlar, arayüz düzeltmesi) boğar | orta | yüksek | Editörün kuyruğu üç cepheye göre yeniden sıralanır; durdurulan işler açıkça yazılır |
| R17 | Yayın dalgası ücretsiz/Premium dengesini ve yolculukları bozar | orta | orta | Her yeni metnin erişimi (ücretsiz, günlük, Premium) ve yolculuktaki yeri yüklemeden önce tabloda; Sean ve Paul |

---
## 5. Olumlu yönler
- İçerik hazır ve denetlenmiş: yazım, doğallık, olgu, telif, kapak tarifi denetimleri paketin içinde belgeli. Yeni metinlerde `DescriptionTR`, `DescriptionEN`, `SubtitleEN`, `NextHook` alanları çoğunda dolu (81–83 metin).
- Kayıt aracı, yayın kapısı betiği, klip taşıma betiği, hizalama betiği var ve kullanılmış.
- Cümle bazlı klip tasarımı, Mehmet'in korktuğu şeyi (metin değişince bütün sesin yeniden üretilmesi) büyük ölçüde zaten önlüyor.
- ElevenLabs'in komşu cümle bağlamı, "robot" şikâyetinin ölçülmüş nedenine doğrudan cevap; dinleme betiği hazır.
- Kütüphane bir buçuk katından fazlasına çıkar. Ücretsiz havuzdaki zayıf, eski metinlerin (25 Kas analizi) yerine konacak güçlü metin çıkar; A1–A2 başlangıç yolculuğunun ilk hikâyesi sorunu buradan çözülebilir.
- Paket ülke kataloglarıyla geliyor (Türkiye 16, Japonya 13, İspanya 12, Meksika 12, Hindistan 11, Hollanda 10, İtalya 9): Instagram tarafı için hazır malzeme.

---
## 6. Prensipler (öneri; Mehmet'in onayına)
1. **Önce envanter, sonra iş.** Sayı olmadan süre ve para söylenmez.
2. **Önce yerelde, sonra canlıda.** Canlıya her yazma yedekli, geri alınabilir ve Mehmet'in sözüyle.
3. **Metin donmadan ses üretilmez.** Donma kapısı: seviye, olgu, yazım, cümle bölme, ad ve açıklama denetimi tamam. Kapıdan geçen metnin gövdesi ancak hata için ve cümle bazında değişir.
4. **Adres (slug) kayıttan önce kesinleşir, sonra değişmez.** Kapak, ses ve bağlantılar ona bağlı.
5. **Yükleme ile yayın ayrıdır.** Her metin etkin olmadan girer; yayın yalnız metni donmuş, kapağı gelmiş ve (ses kararı verildiyse) sesi tam olan metin için.
6. **Dalga dalga.** Önce okurların en çok gördüğü yer: ücretsiz havuz, başlangıç yolculukları, ana sayfa slaytı. Sonra Premium rafları.
7. **Pahalı sağlayıcıda anlık üretim yok.** ElevenLabs yalnız toplu, yerelde, yazılı bütçe tavanıyla; her dalga öncesi tahmin, sonrası gerçekleşen.
8. **Toplu işten önce küçük deneme.** Üç dosyalık yükleme, yirmi cümlelik ses, on kapaklık raf görüntüsü. Deneme geçmeden toplu iş başlamaz.
9. **Kullanıcının göreceği her şey turdan geçer.** Türkçe adlar, açıklamalar, merak cümleleri: taslak, itiraz, bağımsız göz. Ad önerisinin yanında karakter sayısı.
10. **Geri dönüş yolu açık.** Google sesleri silinmez; yeni ses metin metin açılır ve tek ayarla eskiye dönülebilir. Eski kapaklar ve adlar yedekte.
11. **Ölçmeden iyi denmez.** Ses için dinleme örneklemi ve dinleme oranı; kapak için rafta yan yana görüntü; yükleme için alan alan doluluk raporu.
12. **Tek kuyruk.** Editörün işi `ortak/editor_kuyrugu.md`'den akar; üç cephe orada sıralı, durdurulanlar yazılı.

---
## 7. İş sırası (çerçeve; kesin takvim envanterden sonra)
**Aşama 0, envanter ve denemeler (1–2 gün):** kesin sayım · kayıt aracının Eylül biçimine uyarlanması ve üç dosyalık deneme · canlıda kapak ve ses doluluğu · ElevenLabs fiyat, plan, ses adayları · 20 cümlelik uçtan uca ses denemesi (üret, kaydet, yeniden iste, hizala, uygulamada dinle) · Mehmet'in üç kararı (bölüm 9).
**Aşama 1, metni dondurma (içerik; yüklemeyle koşut):** Türkçe adlar (yaklaşık 160, turlu) · açıklamaların 25 Kasım kurallarına göre denetimi · seviye örneklemi (Charles) · erişim ve yolculuk tablosu (Sean, Paul) · editör kararı bekleyen 8 madde · özel isim taraması.
**Aşama 2, yükleme:** yerelde tam yükleme ve alan raporu → canlıda etkin olmadan. Bu adım "sisteme yüklenmiş" hedefini karşılar.
**Aşama 3, kapak (Aşama 1 ile koşut başlar):** 162 tarif öncelik sırasına dizilir · birinci dalga (ücretsiz ve vitrin) · seçim ve raf görüntüsü denetimi · sunucu yayını · kalan dalgalar.
**Aşama 4, ses:** ses adaylarının dinletilmesi ve seçim · üretim kodunun hazırlanması (model, komşu cümle bağlamı, anlık üretimin kapatılması, özet denemesi, maliyet sabiti) · birinci dalga: donmuş yeni metinler · ikinci dalga: Mehmet'in "düşük kalite" dediği mevcut metinler · hizalama · canlıya taşıma · 1.0.4'te doğrulama.
**Aşama 5, yayın dalgaları:** metni donmuş + kapağı gelmiş + sesi tam olan metinler etkinleştirilir; her dalgadan sonra ölçüm.

**Bir haftada gerçekçi olan (ekibin dürüst tahmini; envanterden sonra kesinleşir):** yüklemenin tamamı (etkin olmadan) mümkün. Kapakların tamamı, günde 30–40 kapak seçilirse mümkün; bu Mehmet'in elindeki emeğe bağlı. Sesin tamamı teknik olarak bir iki günde üretilir, ama **metni donmamış metnin sesi üretilmez**; darboğaz ses değil, 160 metnin ad, açıklama ve seviye denetimidir. Bu yüzden ilk hafta için öneri: yükleme tam; kapak ve ses, birinci dalga (öncelikli küme) için tam; kalan iki–üç dalga ikinci haftaya.

---
## 8. Bilinmeyenler ve editörden istenenler
### 8.1 Envanter (paket)
Eylül klasörlerindeki her kayıt birimi için tablo: adres, ad, seviye, tür, ülke, dizi/bölüm, kelime ve karakter sayısı, hangi alanlar dolu (Türkçe ad, iki açıklama, İngilizce alt ad, merak cümlesi, kelime tablosu, quiz, kapak tarifi), ücretsiz/başlangıç işareti. Toplamlar: okuma metni, bölüm, dizi. "364" ile "159" arasındaki fark neyi sayıyor? Gövdesi olmayan 26 metin hangileri? 5 Ekim'den sonra pakette değişen dosya var mı; `Okuma Parçaları` klasöründeki iki teslim paketin içindekiyle aynı mı?
### 8.2 Canlı durum
- Paketin adreslerinden canlıda (etkin ya da değil) kayıtlı olan var mı?
- Kapak: 287 etkin metnin kaçında `ImageUrl` boş ya da dosyası yok; kaçında yatay görsel var; dizilerde kapak. 162 tarifin kaçının dosyası Mehmet'in klasörlerinde ya da depoda hazır?
- Ses: klip sayısı ve karakter toplamı, sağlayıcı ve ses bazında; kaç etkin metnin sesi tam, kaçı kısmi, kaçı hiç yok; kelime zamanlaması olan klip oranı; eski ElevenLabs klipleri hangi metinlerde.
- Dinleme: kaç müşteri sesi kullanıyor, metin başına dinleme; ses kullananla kullanmayanın tutunması (az veri notuyla).
- Maliyet: `ExternalApiCost` tablosundan son 90 günde sağlayıcı bazında harcama ve karakter; Google'da ücretsiz kotanın neresindeyiz.
### 8.3 Kod
- Kayıt aracının Eylül biçimiyle farkları, alan alan; uyarlama için gereken iş.
- ElevenLabs yolu: komşu cümle bağlamı, model seçimi, anlık üretimi ses bazında kapatma, özet şeması; `HasNativeWordTimings` ElevenLabs için ne döndürüyor ve gerçekten kullanılıyor mu.
- Uygulama (1.0.4): ses değişince istemcide ayar gerekiyor mu (kaynak başına sapma düzeltmesi, ses seçimi ekranı, önbellek)?
- Kapakları sunucu klasörü yerine ortak depoya (R2) taşımak ne kadar iş? (Her kapak dalgası için sunucu yayını gerekmesin.)
### 8.4 Paketin "editör kararı bekleyen" maddeleri
Emerson ve Thoreau kırpması · *The Bet* iki rafta · Jekyll & Hyde 3/9 · "Why Italians Love Talking" başlığı (ulusal karakter; 26 Kas'ta Türkçesi "İtalyanlar Neden Konuşkan?" yapıldı) · Hindistan "Lunch" metninde cinsiyet rolü · 11 Ağustos'un dört klasiği kayıtta yok · başlık standardı · Owens metninde bir aktarım. Bunların içerik olanlarını ekip karara bağlar; silme ve telif Mehmet'e çıkar.

---
## 9. Mehmet'ten gereken üç karar
1. **"Önümüzdeki hafta tamamlanmış" ne demek?** (a) Hepsi sisteme yüklü ama yayında değil; (b) hepsi yayında; (c) öncelikli küme yayında, kalan yüklü. Ekip (c)'yi öneriyor.
2. **ElevenLabs bütçesi ve hesabı.** Aylık tavan ne; hesap ve plan var mı? Resmî olmayan bir kaynağa göre 1.000 karakter 0,04–0,08 dolar aralığında (model ailesine göre); bu doğruysa yeni paket onlarca dolar, bütün katalog birkaç yüz dolar mertebesinde. **Resmî fiyat doğrulanmadan bu sayıya güvenilmez.**
3. **"Ses kalitesi düşük" dediğiniz mevcut metinler hangileri?** Liste ya da ölçüt (belirli sesler, belirli seviye, belirli diziler).
Ayrıca: kapak üretiminde günde ne kadar zaman ayırabileceğiniz (Leonardo'da seçim elle).

---
## 10. Sonraki adım
İkinci tur: bu belge itiraz turundan ve bağımsız gözden geçer. Ardından üç ayrı plan: `plan_teslim_paketi`, `plan_kapaklar`, `plan_elevenlabs`; her biri kapsam, adımlar, kapılar, sorumlular, ölçüm ve geri dönüş yoluyla. Editörün envanteri gelmeden takvime gün yazılmaz.

**Kaynak (fiyat, resmî değil):** [Wireflow: ElevenLabs API pricing](https://www.wireflow.ai/blog/elevenlabs-api-pricing) (17 Kasım 2026 tarihli üçüncü taraf yazı).

---
# İkinci tur: bağımsız gözün itirazları ve belgede değişenler (27 Kas 00:30)
Bağımsız göz (planı görmüş, gerekçeyi görmemiş ayrı oturum) belgeyi çürütmeye çalıştı. Kabul edilen itirazlar aşağıda; bu bölüm yukarıdaki bölümlerle çeliştiği yerde **bu bölüm geçerlidir.**

## A. Belgenin zayıf çıkan beş yeri
| No | İtiraz | Karar |
|---|---|---|
| 1 | **Envanter mutabık değil.** 159, 160, 161–174 ve 364 yan yana duruyor. Gerçek sayı 364'e yakınsa ad işi, karakter, maliyet ve kapak sayısı iki katını aşar; bölüm 7 ve 9 geçersiz olur | Kabul. **Mutabık kayıt birimi sayısı gelmeden takvim, maliyet ve "bir haftada şu olur" cümlesi kurulmaz.** Bölüm 7'deki tahmin bu sayıya kadar askıda |
| 2 | **"Yalnız değişen cümle yeniden üretilir" komşu cümle bağlamı açılınca tam doğru değil.** Klip komşularına da bağlanır: tek cümle yenilenirse ton kopabilir, kopmasın denirse üç cümle yenilenir. ElevenLabs çıktısı aynı girdiyle aynı sesi veriyor mu, bilinmiyor | Kabul. Denemeye **tek cümle yenileme testi** eklendi: bağlam açıkken bir cümle değiştirilir, önce tek, sonra komşularıyla üretilir, fark dinlenir. Maliyet kuralı bu testten sonra yazılır |
| 3 | **Yükleme hem "tamamı mümkün" hem darboğaza bağlı gösterilmiş.** Adlar ön koşulsa yükleme de 160 adın arkasında kalır | Kabul. **Yükleme adlardan ayrılır:** metinler etkin olmadan, Türkçe ad alanı boş olarak girer; adlar sonradan güncellenir (`update_packages.py`) ve **yayın kapısında** denetlenir |
| 4 | **Çeviri kapıların dışında kalmış.** Pakette Türkçe çeviri yok, balon doğruluğu %77,6; yayın koşulu yalnız metin, kapak, ses. Bu hâliyle 160 metin ham çeviriyle yayına girer | Kabul. Yayın kapısına dördüncü koşul: **çeviri ve kelime balonu denetimi** (en azından özel isimler ve en sık bakılan kelimeler). Kapsamı Tomris ve editör belirler; çeviri düzeltme işinin (tur04) yeni metinlerdeki maliyeti envanterle birlikte hesaplanır |
| 5 | **Aşama 0 "1–2 gün" iyimser; "ses bir iki günde üretilir" hiçbir ölçüme dayanmıyor.** Hepsi tek editörde; bir gün tıkanırsa üç cephe durur | Kabul. İki cümle de geri alındı. Hız sınırı ve plan kotası bilinmeden üretim süresi söylenmez |

## B. Belgede olmayan, eklenen riskler
| No | Risk | Önlem / kim |
|---|---|---|
| R18 | **Ticari lisans:** ElevenLabs ve Leonardo'da ticari kullanım hakkı plana bağlı olabilir; mağazaların yapay zekâ içeriği beyanı | Satın almadan önce iki hizmetin lisans koşulu ve mağaza beyanı okunur (Sean, editör); karar Mehmet'in |
| R19 | **Aynı metinde iki ses:** eksik klipte Google'a düşmek, tek metinde iki ayrı ses demek | Önlem değişti: ElevenLabs sesli metin **ancak bütün cümleleri üretilmişse** o sese geçer; yarım metin eski sesinde kalır. Karışık ses yok |
| R20 | **Yarım kalan okurlar:** dizinin ortasında ses değişir; silinen metinde (Peter Pan) ilerleme, favori, kelime kayıtları | Ses bir dizinin tamamı için birlikte değişir. Silinecek metne bağlı kayıtlar sayılır; silme yerine yayından kaldırma seçeneği Mehmet'e |
| R21 | **Eski sürümler ve önbellek:** kelime takibi sapma düzeltmesi istemcideyse eski sürümde vurgu kayar; cihazda eski klip kalabilir | Editör koddan cevaplar; gerekirse yeni ses yalnız 1.0.4 ve üstüne |
| R22 | **Quiz ve kelime bütünlüğü:** üç sütunlu kelime tablosunda eksik sütun (seviye) ne oluyor; quizi olmayan metin yolculuğu ve rozetleri nasıl etkiliyor | Envanterde alan alan; kayıt aracı uyarlanırken karar |
| R23 | **Raf ve bildirim davranışı:** 160 metin birden açılırsa "yeni" rafı, günlük metin seçimi, "yeni hikâye geldi" bildirimi | Dalga büyüklüğü sınırlanır; bildirim yeni içerik için 7 gün arayla gidiyor, doğrulanır |
| R24 | **Kalıcı gider ve gelir:** çok az abone varken ücretsiz okura pahalı ses; her yeni metin için süren gider; çift klip depolaması | Tavan tek seferlik değil **aylık** hesaplanır; ElevenLabs sesinin ücretsiz metinlerde mi Premium'da mı açılacağı ayrı ürün kararı (Sean, Nate) |
| R25 | **Geri alma yeni metinlerde işlemez; ölçüm karışır:** yeni metnin Google sesi yok; ses, kapak ve içerik aynı hafta açılırsa hangisinin etkili olduğu ayrıştırılamaz | Yeni metinler için yedek ses kararı (Google ile de üretmek ücretsiz kotada mümkün mü); dalgalar arasında en az birkaç gün ve dalga başına ölçüm |
| R26 | **Tek kişiye bağımlılık:** editör ve Mehmet | İşler birbirini beklemeyecek biçimde sıralanır (D bölümü) |

## C. "Metin dondu" kapısı: genişletilmiş hâli
Kapı yalnız denetim listesi değil, **teknik kilit** olacak.
1. Kapıdan **önce**: seviye, olgu, yazım, cümle bölme, özel isim ve telaffuz denemesi, çeviri ve balon denetimi, paketin bekleyen karar maddeleri (8.4).
2. Donma anında metnin özeti kaydedilir. Donmuş metnin İngilizce gövdesine yazma **tek betikten** geçer; betik önce kaç cümlenin sesinin yenileneceğini ve tahmini maliyeti gösterir.
3. Kapıdan sonra Türkçe taraf (ad, açıklama, çeviri) serbestçe değişir; ses etkilenmez.
4. İngilizce düzeltmeler tek tek değil, **haftalık tek pencerede** toplanır.
5. Cümle bölücünün ve metin normalleştirmenin (tırnak, tire, "Mr.") sürümü sabitlenir; değişmeden önce "kaç özet değişir" kuru çalıştırması yapılır, eşik aşılırsa durur.
6. Sonradan seviye yanlış çıkarsa metin değil **etiket** değişir.
7. Cümle başına yeniden üretim deneme sınırı ve metin başına sayaç; aşılırsa alarm.

## D. Düzeltilmiş sıra: ilk üç gün
Belgedeki sıradan üç yerde ayrılıyor: ses denemesi **mevcut metinlerle** başlar (onlar zaten donmuş; yeni metinler en geç donacak olanlar) · yükleme adlardan ayrılır · Mehmet'in kulağı ve eli **birinci gün** devreye girer (ses adayı ve kapak en uzun bekleyen işler).
- **Gün 1:** mutabık envanter ve kesin adresler · lisans, resmî fiyat, hız sınırı · canlıda ElevenLabs için anlık üretimin kapalı olduğunun doğrulanması · Mehmet'e ses adayı dinletisi (mevcut bir metinden aynı paragraf, üç dört ses) · öncelikli kümenin kapak üretimi başlar.
- **Gün 2:** kayıt aracının uyarlanması ve üç dosyalık deneme · seçilen sesle, komşu bağlam açıkken 20 cümlelik uçtan uca deneme ve tek cümle yenileme testi · çeviri yolu kararı.
- **Gün 3:** yerelde tam yükleme ve alan raporu · mevcut metinlerde ilk ElevenLabs dalgası · Türkçe adların birinci turu.

## E. Mehmet'ten gerekenler: düzeltilmiş liste
Bölüm 9'un yerine geçer.
1. **"Tamamlanmış" tanımı.** Ekibin (c) önerisi (öncelikli küme yayında, kalan yüklü) Mehmet'in "mutlaka tamamlanması gerek" sözünü **tam karşılamıyor**; bunu açıkça söylüyoruz. Hepsinin yayında olması isteniyorsa neyin feda edileceği (ad ve çeviri denetimi mi, dalga arası ölçüm mü) envanterden sonra sayılarla sunulacak.
2. **Günde kapak için ayırabileceğiniz süre.** Takvimi en çok bu belirliyor; kapak seçimi elle ve sizde.
3. **Ses seçiminde kulak onayı.** Dinletiyi ekip hazırlar; seçim sizin.
4. **ElevenLabs ve Leonardo için plan satın alma.** Ekip resmî fiyat, kesin karakter sayısı ve lisans koşuluyla tek seferlik ve aylık tavanı getirir; siz onaylarsınız. (Önceki soru erkendi: bütçe, resmî olmayan fiyatla sorulmaz.)
5. **Canlıya yazma pencereleri.** Yükleme, kapak yayını ve klip taşıma için.
6. **Silme:** Peter Pan (kimlik 1095) ve teliften çıkarılan kalemler; bağlı kayıtlar sayıldıktan sonra.
"Ses kalitesi düşük metinler" sorusu size yük bindiriyordu; **aday listeyi ekip çıkaracak** (ses ve metin bazında, dinleme verisiyle), siz onaylayacaksınız. Elinizde hazır bir liste varsa yine de işimizi hızlandırır.
