# Üç cephe, aşama 0: envanter ve mevcut durum (editör)

**Tarih:** 28 Kasım 2026 · **Hazırlayan:** editör · **Kuyruk:** 10 · **Yöntem:** yalnız okuma. Paket dosyaları tek tek ayrıştırıldı; canlı veritabanına salt okuma sorguları atıldı; kod okundu. Kod yazılmadı, yükleme yapılmadı, ses ya da kapak üretilmedi, para harcatan çağrı yapılmadı.
**Tablo:** `raporlar/veri_2026-11-27/paket_envanteri_editor.csv` (159 satır, metin başına alanlar).
**Cevaplanan:** ön analizin 8.1–8.4 bölümleri ve kuyruktaki ek sorular. Ön analizde yanlış ya da eksik bulduklarım "Düzeltmeler" bölümünde.

## Sonuç
1. **Yükleme, kayıt aracı uyarlanmadan yapılamaz; yapılırsa veri sessizce bozulur.** Bugünkü araçla Eylül paketi şu kayıplarla girer: 44 metin hiç okunmaz, bütün metinler A1 olarak girer, 80 metnin kelime tablosu düşer, 185 Doğru/Yanlış sorusunun cevabı ters kaydedilir, 52 boşluk doldurma sorusunun cevabı boş kalır, 515 soru metnine editör etiketi karışır. Ayrıntı: 8.3.
2. **Canlıda ses tamam:** 287 etkin metnin 287'si tam seslendirilmiş, kısmi ya da sessiz metin yok. 30.476 klip, 2,25 milyon karakter, 39,9 saat; kliplerin tamamına yakını kelime zamanlamalı (5 klip hariç).
3. **ElevenLabs bugün canlıda yalnız 2 metinde** (161 Famous People's First Jobs, 120 Why Penguins Can't Fly). Ön analizdeki "ElevenLabs klipleri" sayısı Google'ın eski Studio ve Neural2 seslerini de kapsıyordu; onlar 17 metin, ElevenLabs değil.
4. **ElevenLabs yolu bugünkü hâliyle sese geçişi yapamaz:** önbellek araması aynı sıradaki **herhangi bir sesin** klibini döndürüyor. Google sesli bir metni ElevenLabs'e atamak hiçbir şey üretmez, yine Google sesi çalar. Komşu cümle bağlamı, tohum (seed) ve maliyet kaydı yok.
5. **Okurun açtığı metinde anlık üretim kapalı, bütün sesler için.** İstemcinin manifest isteği salt okuma; üretim yalnız yönetici ucundan ve geliştirici makinesindeki komuttan.
6. **Ses maliyeti hiç kaydedilmiyor.** Maliyet tablosunda son 90 günde yalnız DeepL var (1,29 $). Google TTS ve ElevenLabs çağrıları kayıt yazmıyor; bütçe takibi bugün ölçülemez.
7. **Kapak:** canlıdaki 287 metnin ve 12 dizinin hepsinde kapak var, dosyaları yerinde; yatay görsel 23 metinde. **Paketin 159 adresinden hiçbirinin kapak dosyası yok** (depo, İndirilenler, Masaüstü ve Resimler'de arandı).
8. **Paketten canlıda kayıtlı adres yok** (0/159). Ama 2 ad canlıdaki metinlerle çakışıyor: "The Wrong Key" (830) ve "The Second Page" (958).

## 8.1 Paket envanteri
Eylül klasörlerindeki (16–23 Eylül) her `## META` bloğu ayrıştırıldı. Ekibin 27 Kasım sayımıyla karşılaştırma:

| | Editör | Ekip (27 Kas) | Not |
|---|---|---|---|
| Okuma metni | **159** | 159 | Aynı |
| Kayıt bloğu | 165 | — | Fark: "It Wasn't Always Like This" ayrı klasörde ikinci kez var (6 blok); 5'i aynı adres, 1'i farklı (`in-italy-the-fork-was-rude` / `italy-called-the-fork-rude`) |
| Kelime | **92.140** | ~107.400 | Benim sayım yalnız gövde (ara başlıklar ve sayılar hariç). Ekibin sayısı daha geniş tanımlı olmalı. Ses maliyeti için karakter sayısı esas alınmalı |
| Karakter (gövde) | **505.000** | ~610.000 | Ses için yaklaşık üst sınır; seslendirilen metin bundan biraz az |
| Seviye | A1 42 + 8 boş, A2 47, B1 33, B2 11, C1 18 | A1 50 | 8 boş seviye mini kitapların 2.–5. bölümleri |
| Bölümlü kitap | 4 kitap, 44 bölüm | aynı | Gövde `## BÖLÜM n —` başlıklarında |
| Türkçe ad (`SubtitleTR`) dolu | 81 | 81 | İngilizce alt adın çevirisi, kart adı değil |
| Açıklama TR / EN dolu | 81 / 81 | 81 | 78 metinde yok |
| Merak cümlesi dolu | 74 | 74 (85 eksik) | Aynı |
| Quiz | 159/159 | var | Biçim sorunları 8.3'te |
| Türkçe çeviri | **0/159** | yok | Aynı |
| Kelime tablosu | **80 üç sütun, 79 dört sütun** | "neredeyse tamamı üç" | **Düzeltme:** yarısı dört sütunlu |
| Kategori | 4 "Cities" (sistemde yok), 8 boş | aynı | Canlıda 24 etkin kategori var, 23 değil ("Work" dahil) |
| Kapak dosyası | **0/159** | 151 tarif var | Tarif var, dosya yok |

Gövdesi olmayan 26 metin (Kulvar A/B klasikleri) bu sayımın dışında; ekibin listesi geçerli. 5 Ekim'den sonra değişen dosyaya bakılmadı.

## 8.2 Canlı durum
**Paket adresleri:** 0/159 kayıtlı (etkin ya da değil); dizi adreslerinde de 0. Ad çakışması 2 (yukarıda): yüklemeden önce birinin adı değişmeli, yoksa rafta aynı adlı iki kart görünür.

**Kapak**
| | Sayı |
|---|---|
| Etkin metin, kapak yolu dolu | 287/287 |
| Dosyası sunucu klasöründe var | 287/287 |
| Yatay görsel (ana sayfa slaytı) | 23 |
| Etkin dizi, kapaklı | 12/12 |
| Sunucu klasöründe dosya | 1.109 dosya, 106 MB (çoğu kullanılmayan eski sürüm) |

**Ses**
| | Sayı |
|---|---|
| Klip | 30.476 (2,25 milyon karakter, 39,9 saat) |
| Tam seslendirilmiş etkin metin | **287/287** (sunucunun kendi denetim komutuyla, cümle bölücüden geçerek) |
| Kelime zamanlamalı klip | 30.471 (%99,98) |
| Google Chirp 3 HD | 27.117 klip, 15 ses; en çok Charon (11.674 klip, 135 metin) |
| Google Studio ve Neural2 (eski Google sesleri) | 3.313 klip, 17 metin |
| ElevenLabs | 46 klip, 2 metin (161: George, 120: Daniel) |
| Ses ataması olmayan etkin metin | 85 (kliplerinin sesine düşüyor, sorun değil) |
| Depolama (tahmin) | ~575 MB (32 kb/sn MP3 × 39,9 saat; R2'den liste alınmadı, Santorini'nin 19 dosyasından ölçülen oranla) |

**Dinleme (müşteri hesapları, 11 Kasım'dan bu yana; testçi ve geliştirici hariç)**
| | Sayı |
|---|---|
| Okuyan müşteri | 277 |
| Sesi en az bir kez kullanan | 209 (%75) |
| Okuma oturumu / sesli oturum | 2.051 / 547 (%27) |
| Ses süresi / okuma süresi | 10,2 saat / 56,5 saat |
| 2+ gün okuyan: sesi kullananlarda | 96/209 (%46) |
| 2+ gün okuyan: kullanmayanlarda | 12/68 (%18) |
Son iki satır ilişki, neden değil: istekli okur hem sesi açıyor hem geri geliyor. Tek dönem, tek ölçüm; **hipotez**.

**Maliyet (son 90 gün, `ExternalApiCosts`)**
| Sağlayıcı | Çağrı | Birim | Tutar |
|---|---|---|---|
| DeepL | 1.726 | 51.499 karakter | 1,29 $ |
| Google TTS | **kayıt yok** | — | — |
| ElevenLabs | **kayıt yok** | — | — |
Google'ın ücretsiz kotasının neresinde olduğumuz buradan bilinemiyor; Google Cloud faturasından bakılmalı (Mehmet'in hesabı). Resmî fiyat: Chirp 3 HD için ayda ilk 1 milyon karakter ücretsiz, sonrası milyon karakter başına 30 $.

**Peter Pan (1095):** canlıda **etkin**. 12 bölüm, 13 quiz, 589 klip. Okur 1, oturum 2, günlük etkinlik kaydı 1. Kayıtlı kelime, kitaplık, ilerleme, yolculuk durağı ve günlük hak kaydı 0. Yani yayından kaldırmak (`IsActive` = hayır) kimsenin kaydını bozmaz. Silme bölümleri, quizleri ve klipleri de götürür; geri alınamaz. Karar Mehmet'in.

## 8.3 Kod
### Kayıt aracı (`tools/content-importer/import_packages.py`) ve Eylül biçimi
| Fark | Bugünkü davranış | Etki |
|---|---|---|
| Seviye alanı `Level` (araç `TextLevel` arıyor) | Bulamayınca **A1** yazıyor | 159 metnin hepsi A1 girer |
| Çok kayıtlı dosya `# HİKÂYE n ·` ile ayrılıyor (araç `## n ·` bekliyor) | Dosya başına yalnız ilk metin | 26 dosyadaki **44 metin okunmaz** |
| Doğru/Yanlış cevabı `- B) False ✓` ile işaretli (araç `**Cevap:**` arıyor) | Bulamayınca cevap **True** | 212 sorunun **185'i ters** kaydedilir |
| Boşluk doldurma şıklı ve `✓` ile işaretli | Cevap satırı bulunamıyor, tek boş şık | 52 soru bozuk girer |
| Soru başlığının sonunda `*(hatırlama)*`, `*(çıkarım)*` | Yalnız baştaki etiket siliniyor | 515 soruda etiket okura görünür |
| Kelime tablosu üç sütun (seviye yok) | 4 hücreden az satır atlanıyor | 80 metnin kelime tablosu **tamamen düşer** |
| Bölümlü kitaplar `## BÖLÜM n —` | `import_books.py` bu biçimi tanıyor ("Kulvar D") | Uygun; denemeyle doğrulanmalı |
| `SubtitleTR`, `DescriptionTR/EN`, `NextHook` | `import_packages.py` okumuyor; `update_packages.py` ve `import_descriptions.py` ayrı | Yükleme adlardan ayrı yapılabilir (ön analizin ikinci tur kararıyla uyumlu) |
| "Cities" kategorisi | Reddediyor | 4 metin |
| Etkinlik | `IsActive` = hayır ile giriyor | Uygun |
**Gereken iş:** yukarıdaki altı ayrıştırma düzeltmesi, her alan için "okundu / boş" raporu, üç dosyalık yerel deneme (biri çok kayıtlı, biri bölümlü). Tahmin: bir oturum. Testsiz yapılmamalı; quiz cevap anahtarı hatası okura "yanlış bildin" olarak döner.

### ElevenLabs yolu (`Services/ElevenLabsTtsService/ElevenLabsTtsService.cs`)
| Konu | Bugün |
|---|---|
| Model | `eleven_multilingual_v2` (hâlâ listede; yeni nesil modeller var) |
| Ayar | stability 0,40, similarity 0,80, style 0,30, speaker boost |
| Komşu cümle bağlamı (`previous_text` / `next_text`) | **Yok** |
| Tohum (seed) | **Yok.** ElevenLabs'e göre tohum yalnız "en iyi çaba"; aynı girdi aynı sesi garanti etmiyor |
| Önbellek araması | (metin, sıra, ses) ile; **cümle metnini denetlemiyor**, bulamazsa **aynı sıradaki herhangi bir sesin** klibini döndürüyor. Sonuç: Google klibi olan metinde ElevenLabs hiç üretilmez; metin değişince eski klip yeni cümleye servis edilebilir |
| Dosya adı (özet) şeması | `ComputeSentenceHash(metin, EN, EN, ses)`; Google'ınkinden farklı ama kendi içinde tutarlı. Ses değişince bütün klipler zaten yeniden üretilir; gizli maliyet riski şema değil yukarıdaki önbellek araması |
| Kelime zamanlaması | `HasNativeWordTimings` ElevenLabs için "evet" döndürüyor ama zaman damgalı uç çağrılmıyor; zamanlama hizalama betiğinden gelir (ücretsiz, sağlayıcıdan bağımsız) |
| Maliyet kaydı | **Yok** (sabit kodda 1.000 karakter 0,30 $, kullanılmıyor) |
| Anlık üretim | Okur tarafında kapalı (istemci manifesti salt okuma). Test uçları (`api/test/tts`) yalnız DEBUG derlemesinde var, canlıda yok |
| Canlıda anahtar | `ELEVENLABS_API_KEY` tanımlı |
**Geçişten önce gereken kod işi:** önbellek aramasını Google yolundaki gibi metinle doğrulamak, ses bazında "yalnız toplu üretim" kuralı, komşu cümle bağlamı, maliyet kaydı, model seçimi. Tek cümle yenileme testi (ön analiz ikinci tur, A2) bu düzeltmelerden sonra anlamlı.

### Uygulama (1.0.4)
- **Kelime takibi sapma düzeltmesi istemcide**, kaynak adına göre (`lib/features/reader/utils/word_timings.dart:35`): sağlayıcı işareti +138 ms, hizalama 0 ms. 17 Ağustos'tan beri her sürümde var. Yeni ses hizalama betiğiyle zamanlanırsa istemcide değişiklik gerekmez; eski sürümler de doğru vurgular.
- **Cihazdaki klip önbelleği:** adres üzerinden (100 MB, en eski silinir). Ses ya da metin değişince adres değiştiği için eski klip kalmaz.
- **Ses seçimi ekranı:** okura açık bir ses seçimi yok; ses metne (ya da diziye) atanıyor.

### Kapakları ortak depoya (R2) taşımak
Ses zaten R2'de (`audio.getdailyenglish.com`). Uygulama mutlak adresi olduğu gibi kullanıyor, göreli yolu sunucu adresine ekliyor (`lib/main.dart:1762`). Yani kapakları R2'ye yükleyip `ImageUrl`'i mutlak adrese çevirmek **uygulama güncellemesi istemez**. İş: yükleme betiği (ses için olan depo istemcisi hazır), adres güncelleme betiği (yedekli), sunucu klasörünü bir süre yerinde tutmak. Tahmin: yarım oturum. Kazanç: her kapak dalgası için sunucu yayını gerekmez.

### Cümle bölücü
Sunucuda `Server/Helpers/SentenceUtils.cs` (`SplitIntoSentences`, `PrepareForSpeech`), istemcide aynı kuralı uygulayan `SentenceSegmenter`. Sürüm numarası yok; sabitlemenin yolu bir "altın" test kümesi: kataloğun bugünkü bölümleri kaydedilir, bölücü değişirse kaç cümlenin kaydığı test olarak raporlanır. Bugün böyle bir test yok.

### Yeni içerik bildirimi ve "yeni" rafı
- Bildirim, **oluşturulma tarihi** son 2 gün içinde olan etkin metinlerden, okurun ilgi alanı kategorisine uyanı seçiyor; kişi başına 7 günde bir, günde en çok bir bildirim. Metinler etkin olmadan girip **2 günden sonra** açılırsa bildirim hiç gitmez, çünkü tarih açılış değil kayıt anı. 160 metin aynı gün açılırsa her okura yine yalnız bir bildirim gider.
- Uygulamada "yeni" adlı bir raf yok. Raflar seviye ve ilgi alanıyla sıralanıyor.

### Quiz ve kelime bütünlüğü (R22)
- Canlıda quizi olmayan etkin metin **0**. Pakette 159/159 quiz var; risk biçimde (yukarıda).
- Üç sütunlu kelime tablosu bugünkü araçla düşüyor. Dört hücreye tamamlanırsa seviye sütunu boş kalır ve A1 (1) yazılır.

## 8.4 Paketin "editör kararı bekleyen" maddeleri
İçerik kararları (Emerson ve Thoreau kırpması, *The Bet* iki rafta, Jekyll & Hyde 3/9, başlık standardı, Owens aktarımı, Hindistan "Lunch") ekibin; editörün söyleyeceği teknik bir şey yok. "11 Ağustos'un dört klasiği kayıtta yok": canlıda bu adlarla kayıt aranmadı, adları belli olunca bakılır. Telif ve silme Mehmet'in: Peter Pan için sayım yukarıda.

## Resmî kaynaklardan (ek sorular)
| Soru | Cevap | Kaynak |
|---|---|---|
| ElevenLabs fiyatı | API'de 1.000 karakter 0,08 $ (v2 Multilingual, v3, v4) ya da 0,04 $ (Flash/Turbo). Abonelik: Creator 22 $/121 bin kredi, Pro 99 $/600 bin, Scale 299 $/1,8 milyon. Sayfanın bir sürümünde daha düşük, indirimli görünen fiyatlar var; satın almadan önce canlı sayfadan bakılmalı | [Fiyat](https://elevenlabs.io/pricing/api), [v3 maliyeti](https://help.elevenlabs.io/hc/en-us/articles/35869113958801-How-much-does-it-cost-to-generate-using-Eleven-v3) |
| Paketin ses maliyeti (tahmin) | ~505 bin karakter: 0,08 $ ile ~40 $, 0,04 $ ile ~20 $. Bugünkü bütün katalog (2,25 milyon): ~180 $ ya da ~90 $ | hesap |
| Hız sınırı (eşzamanlı istek) | Flash/Turbo dışı modellerde Creator 5, Pro 10, Scale 15; Flash/Turbo'da iki katı. Aşınca sıraya alıyor, sonra 429 | [Eşzamanlılık](https://elevenlabs.io/docs/help-center/technical/how-many-text-to-speech-requests-can-i-make-and-can-i-increase-it) |
| Ticari lisans | Ücretsiz planda ticari kullanım yok, atıf zorunlu. Ticari hak ücretli abonelikle | [Yardım merkezi](https://elevenlabs.io/docs/help-center/legal/can-i-publish-the-content-i-generate-on-the-platform) |
| Aynı girdi aynı ses mi | Hayır, garanti değil; tohumla "en iyi çaba". Komşu cümle bağlamı birleştirilen parçalarda sürekliliği artırmak için | [API başvurusu](https://elevenlabs.io/docs/api-reference/text-to-speech/convert) |
| Google Chirp 3 HD | Ayda ilk 1 milyon karakter ücretsiz, sonrası milyon başına 30 $ | [Google fiyat](https://cloud.google.com/text-to-speech/pricing) |

## Düzeltmeler (ön analize ve paket envanterine)
1. "ElevenLabs klipleri olan metinler": ElevenLabs yalnız 2 metinde. Studio ve Neural2 sesli 17 metin Google'ın eski sesleri.
2. "Klipler metinden eşleştirilip yeni sıraya taşınıyor": Google yolunda doğru (Santorini'de bugün sınandı, 6 klip taşındı). **ElevenLabs yolunda değil** (önbellek araması metne bakmıyor).
3. "Yönetim panelinde anlık üretim kapatılabiliyor": bugün anlık üretim istemci için hiç yok; üretim yalnız yönetici ucu ve yerel komut.
4. "Kelime tablosu neredeyse tamamı üç sütun": 80 üç, 79 dört sütun.
5. "23 kategori": canlıda 24 etkin kategori.
6. "Maliyet kaydı her ücretli çağrıda": yalnız DeepL'de.
7. Kelime sayısı 107.400 değil, gövde sayımıyla 92.140; karakter 505 bin. Fark yöntemde; maliyet için karakter esas alınmalı.

## Mehmet'ten beklenen
1. Kayıt aracının uyarlanması (8.3'teki altı düzeltme + üç dosyalık yerel deneme): kod işi, onayınla başlar.
2. ElevenLabs'e geçmeden önce önbellek araması ve maliyet kaydı düzeltmesi: kod işi, onayınla.
3. Peter Pan: yayından kaldırma mı, silme mi (kaldırmak kimsenin kaydını bozmuyor).
4. Google Cloud faturasında bu ayın TTS karakter kullanımı (ücretsiz kotanın neresindeyiz); editör göremiyor.
