# Satış kanalı ve bildirim verisi

**Tarih:** 21 Kasım 2026, 01:30 · **Görev:** `ortak/editor_gorevi_2026-11-21_kanal_ve_bildirim_verisi.md` · **Hazırlayan:** editör
**Yöntem:** canlı veritabanı salt okuma (yalnız müşteri hesapları, 358; kişisel bilgi yok) ve canlıdaki sunucu kodu (`master` c8497c6) ile uygulama kodu (`feat/journey-core`). Kod ve veri değişmedi. Önceki sayılar yeniden hesaplanmadı; bu rapor 18 Kasım'dan sonrasını ve eksikleri ekler.

## Özet

1. **18 Kasım'dan sonra gerçek yeni satış, iptal ya da iade yok.** Dört satış, üçü etkin; hepsi iOS.
2. **Android'de geliş kaynağı kullanıcı başına tutuluyor ve dolu.** 137 Android müşterinin 85'i (%62) Instagram bağlantısından gelmiş: profil 53, hikâye 32. Play organik 43, bilinmeyen 9. Toplantıdaki "kaynak bilinmiyor" Android için doğru değil.
3. **iOS'ta kullanıcı başına kaynak yok ve mağaza bağlantısıyla olamaz.** Dört alıcının dördü de iOS; nereden geldikleri uygulama kayıtlarından öğrenilemez.
4. **17 Kasım sıçraması Instagram'dan:** o günkü 32 Android kaydın 23'ü Instagram etiketli. Tek bir saate yığılmıyor; 16 Kasım 23:00'te başlıyor, gün boyu sürüyor, 18 Kasım'da devam ediyor.
5. **Dokunma kaydı gönderim kaydıyla eşleşiyor; 18 Kasım raporundaki "türü taşımıyor" sözüm yanlıştı.** 32 dokunmanın 32'si eşleşti. 1.376 gönderime 32 dokunma (%2,3).
6. **"Geri dön" bildirimi ölçülebildiği kadarıyla işe yaramıyor:** 185 gönderim, 1 dokunma; 24 saat içinde uygulamayı açan 2.
7. **Ayar kaydetme hatasının nedeni bulundu:** onboarding sonunda aynı profil satırına milisaniyeler içinde iki yazma çakışıyor. Küçük bir sunucu düzeltmesi.
8. **Kelime tekrarı bildiriminin 3 günlük arası çalışmıyor:** tekrarların üçte ikisi 3 günden önce gitmiş.

## 1. Satış ve kaynak

### 1.1 Gerçek satışlar (bugün)

| | Tarih | Platform | Plan | Deneme | Bugün |
|---|---|---|---|---|---|
| A | 2 Kas | iOS | Yıllık | evet | etkin (9 Kas'ta ücretliye döndü), yenileme açık |
| B | 3 Kas | iOS | Aylık | hayır | etkin, yenileme açık (sonraki 3 Ara) |
| C | 7 Kas | iOS | Yıllık | evet | denemeyi 14 Kas'ta kapattı, süresi doldu |
| D | 13 Kas | iOS | Aylık | hayır | etkin, yenileme açık (sonraki 13 Ara) |

- 18 Kasım'dan sonra: yeni gerçek satış yok, iptal yok, iade yok.
- Tabloda müşteri türüyle görünen beşinci abonelik (19 Kas, Android, yıllık) Mehmet'in kendi denemesi; satış sayılmadı.
- Satın almaya basıp tamamlamayan: 18 Kasım'da 11'di, bugün **18** (iOS 11, Android 7). 19 Kasım'dan beri 7 kişi bastı. Neden tamamlamadıkları hâlâ bilinmiyor.

### 1.2 Sunucu kullanıcı başına ne tutuyor

`Users` tablosunda üç alan; uygulama bunları istek başlığıyla bildiriyor. Yönlendiren bilgisinde ilk değer saklanır, sonradan değişmez.

| Alan | Ne | Dolu olan |
|---|---|---|
| `SignupPlatform` | ios / android | 358/358 |
| `InstallSource` | hangi mağazadan kuruldu (appstore, playstore, testflight…) | 357/358 |
| `InstallReferrer` | Play'in verdiği yönlendiren bilgisi (yalnız Android) | 137/137 Android; ilk müşteriden (29 Ekim) beri |

`InstallSourceReport` yönetim panelindeki bir rapor; `InstallReferrer`'ı kanal ve kampanyaya ayırıyor. Ayrı bir tablo değil.

**Android müşteriler, kaynağa göre (137):**

| Kaynak | Kişi | En az 1 hikâye bitiren | Ertesi gün dönen | Paywall gören | Satın almaya basan |
|---|---|---|---|---|---|
| Instagram · profil bağlantısı | 53 | 23 (%43) | 11/50 (%22) | 23 | 2 |
| Play organik (arama, göz atma) | 43 | 13 (%30) | 3/41 (%7) | 12 | 1 |
| Instagram · hikâye bağlantısı | 32 | 22 (%69) | 11/30 (%37) | 13 | 2 |
| Bilinmiyor (Play etiket vermemiş) | 9 | 4 | 1/8 | 4 | 3 |
| *iOS (kaynak yok), karşılaştırma için* | *221* | *128 (%58)* | *52/208 (%25)* | *91* | *15* |

- Instagram'dan gelen, mağazada kendisi bulandan daha çok okuyor ve dönüyor; hikâye bağlantısından gelen en iyisi. Gruplar küçük (30–50 kişi); yön gösterir, kesin değildir.
- **Alıcılarda ne yazıyor:** dördü de iOS; `InstallSource` "appstore", yönlendiren alanı boş. Android'de gerçek alıcı yok.
- **Basıp tamamlamayanlarda:** iOS 11 (kaynak yok); Android 7: Instagram profil 2, Instagram hikâye 2, organik 1, bilinmiyor 2.

### 1.3 iOS'ta kaynak okunabilir mi

- **Play:** yönlendiren bilgisi uygulamaya ulaşıyor ve bugün okunuyor. Instagram bağlantıları zaten etiketli (`utm_campaign=bio`, `story`). Yeni bağlantı türleri (reels açıklaması gibi) kendi etiketiyle verilirse ek iş gerekmez.
- **App Store:** kampanya bağlantısının etiketi uygulamaya ulaşmaz; yalnız App Store Connect'in kaynak raporunda toplu görünür. Yani iOS'ta "bu kullanıcı hangi bağlantıdan geldi" bilgisi mağaza bağlantısıyla elde edilemez. Bağlantıları etiketlemek kod işi değil; sonuç Mehmet'in App Store Connect oturumundan okunur.
- iOS'ta kullanıcı başına kaynak isteniyorsa iki yol var: onboarding'e soru (ekip istemiyor) ya da üçüncü taraf bir ölçüm hizmeti (orta-büyük iş, gizlilik beyanı değişir). Önermiyorum; Android'deki oran iOS için de makul bir tahmin verir.

### 1.4 17 Kasım'daki 76 kayıt

| Gün | Kayıt | iOS | Android | Android'de Instagram | Android'de organik |
|---|---|---|---|---|---|
| 10–15 Kas (günlük ortalama) | 9 | 7 | 2 | 1 | 0 |
| 16 Kas | 21 | 15 | 6 | 3 | 3 |
| **17 Kas** | **76** | **44** | **32** | **23** (profil 14, hikâye 9) | 7 |
| 18 Kas | 30 | 15 | 15 | 13 (profil 10, hikâye 3) | 2 |
| 19 Kas | 19 | 9 | 10 | 5 | 3 |
| 20 Kas | 19 | 11 | 8 | 5 | 2 |

**Saat saat (17 Kas, Türkiye saati):** 00–04: 10 · 08–11: 11 · 12: 6 · 13: 7 · 14: 7 · 15–16: 6 · 17: 5 · 18: 5 · 19: 5 · 20: 1 · 21: 4 · 22: 6 · 23: 3. Artış 16 Kasım 23:00'te başlıyor (o saatte 4 kayıt).

- Tek bir saate yığılma yok; öğlen 12–14 arası hafif tepe. 24 saatte biten bir hikâye paylaşımından çok, gün boyu izlenen bir gönderiye (reels) benziyor. Hangi paylaşım olduğunu Instagram tarafındaki saatle karşılaştırmak gerekir: **16 Kasım akşamı 22:00–23:00 civarında ya da 17 Kasım sabahı ne paylaşıldı?**
- Android'de o günün %72'si Instagram etiketli. iOS'taki 44 kayıt için kanıt yok; aynı gün aynı oranda arttığı için aynı kaynaktan olması beklenir.
- **Seviye seçimi:** A1 25 · A2 40 · B1 7 · B2 ve üstü 4. Önceki haftaya göre (A1 29 · A2 29 · B1 13 · üstü 1) A2 ağırlıklı.
- **İlk gün:** onboarding'i bitiren 72/76 · okumaya başlayan 63 · bir hikâye bitiren 41 (%54) · ertesi gün dönen 22 (%29). Önceki hafta (74 kişi): 70 · 60 · 38 (%51) · 16 (%22). Sıçramayla gelenler önceki haftadan kötü değil, biraz iyi.

## 2. Bildirim

### 2.1 Türe göre (bugüne kadar: 317 müşteriye 1.376 gönderim)

| Tür (kayıttaki ad) | Bugüne kadar | Kişi | Son 7 gün | 19 Kas'tan beri | Dokunma | 24 saat içinde uygulamayı açan* |
|---|---|---|---|---|---|---|
| Kelime tekrarı (`VocabReview`) | 261 | 79 | 167 | 66 | 3 | 25/224 |
| Günün quizi (`DailyQuiz`) | 250 | 71 | 138 | 58 | 9 | 37/225 |
| Seri başlat (`StreakStart`) | 209 | 152 | 108 | 42 | 8 | 41/188 |
| İlk okumaya çağrı (`Activation`) | 186 | 98 | 94 | 41 | 3 | 11/162 |
| Geri dön (`WinBack`) | 185 | 114 | 118 | 49 | 1 | **2/155** |
| Günlük açılan metin (`DailyUnlock`) | 154 | 68 | 0 | 0 | 1 | 15/154 |
| Günlük hatırlatma (`DailyReminder`) | 90 | 71 | 80 | 42 | 2 | 10/73 |
| Seri hatırlatma (`Streak`) | 30 | 11 | 7 | 6 | 5 | 13/26 |
| Seri telafisi, tanıtım, deneme bitiyor | 11 | 9 | 1 | 0 | 0 | 3/11 |
| **Toplam** | **1.376** | **317** | **713** (277 kişi) | **304** | **32** (18 kişi) | **157/1.218** |

\* Yalnız 24 saati dolmuş gönderimler. Bildirimin etkisi demek değildir; o gün zaten açacak olanı da sayar.

- Günlük açılan metin 12 Kasım'da kapatıldı; tanıtım da. Kodda artık gönderilmiyorlar.
- Ulaşma kaydı (`ReceivedAt`) 1.376 gönderimin 4'ünde dolu; müşteriler hâlâ eski sürümde.

### 2.2 Her türün bugünkü metni, koşulu ve saati

Metinler 12 Kasım'da yeniden yazıldı (kayıtta `copy_v2`; 928 gönderim bu metinlerle). Tek sürüm var, A/B yok. Başlıkta ad kullanılabiliyorsa "{ad}, …" biçimi gider (ad 2–12 harf, başlık 40 karakteri geçmiyorsa).

| Tür | Başlık | Gövde | Kime | Ne zaman |
|---|---|---|---|---|
| Seri hatırlatma | {n} gündür her gün okuyorsun | Bu akşam bir bölüm daha okursan {n+1}. gün olur. · yarım kitap varsa: Bu akşam bir bölüm daha? {kitap} bıraktığın yerde duruyor. | Serisi 3 gün ve üstü, bugün okumamış | Akşam: seçtiği saat, yoksa 19–21 |
| Seri başlat | Dün okudun, bugün de olsun mu? | {kitap}, {n}. bölüm bıraktığın yerde. · kitap yoksa: Bir bölüm bitirmen yeter. | Serisi 1–2 gün, bugün okumamış | Akşam |
| Seri telafisi | Dün ara verdin, sorun yok | {n} günlük serin duruyor. Bugün bir hikâye ya da bölüm bitirirsen geri gelir. | 3 gün ve üstü serisi son 48 saatte kırılmış; kırılma başına bir kez | 09–23 arası ilk fırsat |
| İlk okumaya çağrı, 1. gün | İlk hikâyen: {hikâye} · ya da: İlk hikâyen hazır | Senin seviyende bir hikâye. Takıldığın kelimeye dokunman yeter. | Kayıttan beri hiç etkinliği yok; kaydın 1., 3. ve 7. günü | Kişisel saat |
| İlk okumaya çağrı, 3. gün | Beş dakikan var mı? | Seviyene göre kısa hikâyeler var. Bilmediğin kelimeye dokun, sözlüğe gerek yok. | aynı | Kişisel saat |
| İlk okumaya çağrı, 7. gün | Hangi hikâyeyle başlasak? | Seviyene göre hikâyeler var. Birini seç, ilk bölümü oku. | aynı | Kişisel saat |
| Deneme bitiyor | Ücretsiz denemen {gün adı} günü bitiyor | Sonrasında {plan} olarak devam eder. İstemezsen iptal edebilirsin; sürpriz yok. | Denemede, yenileme açık, bitişe 2 gün | Kişisel saat |
| Kelime tekrarı | {kelime} ne demekti? · ya da: Kelimelerinin tekrar günü | Bugün {n} kelimenin tekrar günü. Unutmadan bir tur at, birkaç dakika sürer. | Günü gelmiş en az 5 kelime, bugün tekrar yapmamış; 3 gün ara (bkz. 2.3) | Kişisel saat |
| Günün quizi | Günün Quizi hazır · dün oynadıysa: Dünkü kelimeler yerine oturdu mu? | {n} kelime, iki dakika. Herkesle aynı sorular. | Son 7 günde en az bir kez oynamış, bugün oynamamış | Kişisel saat |
| Yeni içerik | Yeni hikâye: {ad} · ya da: Seviyene yeni hikâye geldi | {seviye} seviyesinde, yeni eklendi. İlgi alanına göre seçtik. | Son 2 günde eklenen, seviyesine ve ilgi alanına uyan metin; 7 gün ara | Kişisel saat (bugüne kadar hiç gitmemiş) |
| Geri dön, 3. gün | {n}. bölümde kalmıştın · ya da: Kısa bir hikâye? | {kitap} bıraktığın yerde duruyor. · ya da: Seviyene göre kısa hikâyeler var. Bir çay molasına sığar. | Son etkinlikten tam 3, 7, 14 ve 30 gün sonra (her biri bir kez) | Kişisel saat |
| Geri dön, 7. gün | Bir haftadır görüşmedik | Kelimelerin, bölümlerin hepsi yerinde. Bir hikâyeyle kaldığın yerden dönersin. | aynı | Kişisel saat |
| Geri dön, 14. ve 30. gün | Her şey bıraktığın gibi | Kelimelerin ve seviyen yerinde. Bir bölüm yeter, kaldığın yerden. | aynı | Kişisel saat |
| Günlük hatırlatma | Okuma vakti | {kitap} bıraktığın yerde duruyor. · ya da: Bugünkü hedefin {n} dakika; bir bölüm yeter. | Hatırlatma saati seçmiş, son etkinliği 1–2 gün önce | Seçtiği saat |

**Ortak kurallar (kod):**
- Saatte bir çalışır (her saatin 5. dakikası). **Kişi başına yerel günde en çok 1 bildirim.**
- Yerel saat 09:00–22:59 dışında gönderilmez.
- "Kişisel saat": kullanıcının seçtiği hatırlatma saati; yoksa son 14 günde en çok etkin olduğu saat; o da yoksa 20:00. Hepsinde bir saat tolerans.
- Öncelik sırası: seri hatırlatma, seri başlat, seri telafisi, ilk okumaya çağrı, deneme bitiyor, kelime tekrarı, günün quizi, yeni içerik, geri dön, günlük hatırlatma.
- Kullanıcı bildirimleri uygulamadan kapattıysa ya da telefon izni "hayır" olarak biliniyorsa gönderilmez; izin bilinmiyorsa gönderilir.

### 2.3 Kişi başına sıklık

| | Ortanca | %90 | En çok |
|---|---|---|---|
| Bir günde (bildirim alan kişi-gün) | 1 | 1 | **1** |
| Bir haftada | 2 | 5 | 7 |
| Son 7 günde (277 kişi) | 2 | 5 | 7 (5 ve üstü alan 34 kişi) |
| Bugüne kadar toplam (317 kişi) | 3 | 10 | 18 |

- Günde 1 sınırı tutuyor; hiçbir müşteri aynı gün iki bildirim almamış.
- Üst üste her gün bildirim alan: 72 kişi en az 5 gün, en uzun dizi 17 gün.

**Aynı türün aynı kişiye tekrarı:**

| Tür | Kişi | 1 kez | 2 | 3 | 4 ve üstü | En çok | İki gönderim arası (ortanca) |
|---|---|---|---|---|---|---|---|
| Seri başlat | 152 | 108 | 32 | 11 | 1 | 4 | 1 gün |
| Geri dön | 114 | 61 | 35 | 18 | 0 | 3 | 4 gün |
| İlk okumaya çağrı | 98 | 36 | 36 | 26 | 0 | 3 | 2 gün |
| Kelime tekrarı | 79 | 21 | 15 | 9 | 34 | 9 | 2 gün |
| Günün quizi | 71 | 12 | 19 | 12 | 28 | 10 | 1 gün |
| Günlük hatırlatma | 71 | 55 | 14 | 1 | 1 | 4 | 1 gün |

- "Geri dön" ve "ilk okumaya çağrı" tasarım gereği en çok 3 kez gider (şimdilik; geri dönün dördüncüsü 30. günde). Her gönderimin metni farklı; Tony'nin "aynı cümleyle üç kez" kaygısı metin için geçerli değil, sayı için geçerli.
- **Kelime tekrarının 3 günlük arası çalışmıyor.** 182 tekrarın 122'si 3 günden önce gitmiş. Neden: sunucu "son gönderilen tür kelime tekrarıysa 3 gün bekle" diye bakıyor; araya başka bir tür (çoğunlukla günün quizi) girince sayaç sıfırlanıyor.
- Günün quizinde ara yok: oynamayı bırakan kişiye 7 gün boyunca her gün gidebiliyor.

### 2.4 Gönderim saatleri (kullanıcının yerel saati)

| Saat | 09 | 10–11 | 12 | 13–18 | 19 | 20 | 21 | 22 |
|---|---|---|---|---|---|---|---|---|
| Gönderim | 191 | 20 | 134 | 137 | 273 | 350 | 141 | 130 |

- 09:00'dan önce giden yok. **22:05'te giden 130 (%9), 21:05'te giden 141.** Kod sınırı 22:59; "09–21" isteniyorsa sınır tek sabit.
- 22'de gidenler, seçtiği ya da öğrenilmiş saati 21–22 olan kullanıcılar; türleri karışık (quiz, kelime tekrarı, ilk okumaya çağrı, geri dön, seri başlat).
- Saat farkı 1.376 gönderimin 1.194'ünde Türkiye (boş olanlar da Türkiye sayılıyor); kalanı yurt dışı (Avrupa, Körfez, Amerika).

### 2.5 Dokunma gönderimle eşleşiyor mu

**Evet.** Sunucu her bildirimin içine kayıt kimliğini koyuyor; uygulama dokunulunca `push_opened` olayında bu kimliği ve türü gönderiyor (derleme 42'den beri). 32 dokunmanın 32'si bir gönderim kaydıyla birebir eşleşti. Türe göre dokunma 2.1'deki tabloda. Yönetim panelindeki bildirim etkisi raporu da bu eşleşmeyi kullanıyor.

18 Kasım raporunda "dokunma kaydı türü taşımıyor; türe göre açılma bilinmiyor" yazmıştım. **Yanlıştı;** olayın içeriğine bakmadan yazmışım.

Kaydın görmediği dokunmalar:
- Uygulama açıkken gelen bildirim ekranda şerit olarak gösterilir; ona dokunma kaydedilmez.
- Telefonun kendi kurduğu bildirimler ("Yarın hatırlat" dahil) sunucu kaydında yoktur.
- Olaylar toplu gönderilir; uygulama hemen kapatılırsa dokunma kaybolabilir.

### 2.6 Adresi olup bildirim almayan; geçersiz adres

| | iOS | Android |
|---|---|---|
| Müşteri | 221 | 137 |
| Bildirim adresi var | 216 (%98) | 110 (%80) |
| Adresi var, hiç bildirim almamış | 17 | 9 |
| Daha önce bildirim almış, bugün adresi yok | 1 | 16 |

- Adresi olup hiç bildirim almayan 26 kişinin 18'i son 24 saatte kaydoldu (ilk bildirim en erken ertesi gün gider). Kalan 8 kişi hiçbir türün koşuluna girmemiş.
- **Gönderim hatası sayısı: bilinmiyor.** Başarısız gönderim veritabanına yazılmıyor; yalnız sunucu günlüğüne düşüyor. Google "bu adres artık kayıtlı değil" derse sunucu adresi siliyor. "Bugün adresi yok" satırı bunun dolaylı izi: Android 16, iOS 1. Büyük olasılıkla uygulamayı silenler; çıkış yapanlar da aynı görünür.

### 2.7 Bildirim tercihini kaydetme hatası

- **Güncel sayı:** 7 müşteride 7 kez (18 Kasım'da 6). Aynı uca 1.168 başarılı istek var.
- **Ne zaman:** yedisinde de onboarding'in bittiği an. Uygulama birkaç yüz milisaniye içinde aynı profil satırına art arda yazıyor: tercihler, görünen ad, bildirim adresi, bildirim tercihi. Hata veren istek, bir önceki yazmadan 3–15 ms sonra başlamış.
- **Neden:** profil satırında "başkası değiştirdiyse yazma" koruması var (`UpdatedAt`). Bildirim tercihi satırı okuyup yazana kadar öbür istek satırı değiştirmiş oluyor; kayıt reddediliyor ve bu uçta yakalanmadığı için 500 dönüyor. Hata metni kayıtlı değil; teşhis kod ve zamanlamadan.
- **Kullanıcı ne görüyor:** hiçbir şey; uygulama bu hatayı yutuyor. Sonraki bildirim tercihi isteği 25–260 ms sonra başarılı. Ama başarısız isteğin taşıdığı ayar (onboarding'de seçilen hatırlatma saati ya da izin bilgisi olabilir) o an kaydedilmemiş olabilir; hangisi olduğu görülemiyor.
- **Düzeltme:** küçük. Bu uçta satırı okuyup yazmak yerine tek adımda güncellemek ya da çakışmada bir kez yeniden denemek; 5–15 satır, sunucu yayını gerekir. Bildirim adresi kaydındaki 4 hata (4 kişi) büyük olasılıkla aynı çakışma.

### 2.8 Bildirimden sonra kapatan ya da dönmeyen

- **Bildirimleri uygulamadan kapatan müşteri: 0.**
- **Telefon izni:** yalnız 8 Android müşteride biliniyor (yeni sürümde olanlar): 6 "hayır", 2 "evet". Bildirimden sonra mı kapattıkları ölçülemiyor; alan durumu tutuyor, değişimi değil.
- **Bildirim aldıktan sonra uygulamayı bir daha hiç açmayan:** ilk bildirimi 3 günden eski 207 müşterinin 136'sı (%66). Bu bildirimin sonucu değil; bildirimlerin çoğu zaten bırakmış kişiye gidiyor.
- Adresi sonradan silinen 17 kişi (2.6) uygulamayı silmiş olabilir; bildirimle ilişkisi kurulamıyor.

### 2.9 Derleme 49 ile gelenler nereye düşecek

| Ne | Nerede | Not |
|---|---|---|
| Telefon bildirim izni | `UserProfiles.OsNotificationPermission` (evet/hayır/boş) ve `OsNotificationPermissionAt` | Oturum açılınca ve uygulama öne gelince, değer değiştiyse gönderilir. "Henüz sorulmadı" boş kalır |
| Ulaşma | `PushNotificationLogs.ReceivedAt` | Android'de uygulama kapalıyken de yazılır. **iOS'ta yalnız uygulama açıkken;** iOS ulaşma oranı hep düşük görünecek |
| "Yarın hatırlat"a dokunma | `UserEvents`, tür `user_action`, içerikte `action = remind_tomorrow_tapped` | Yolculuk sayfasından gelirse `source = journey_page`; bitiş ekranından gelirse kaynak alanı yok |
| "Yarın hatırlat" sonucu | aynı, `action = remind_tomorrow_result`, `granted = true/false` | "false" izin reddini de, 15 sn içinde yanıt gelmemesini de kapsar |
| Hatırlatmanın kendisi | sunucuda **yok** | Telefonun kurduğu yerel bildirim (ertesi gün seçili saatte, yoksa 19:00). Gönderildiği ve dokunulduğu ölçülemez; dolaylı ölçü ertesi günkü açılış |

## Kodda görülen, görev dışı iki davranış

- **Öncelik pencereyi eziyor.** Sunucu önce kişinin en öncelikli bildirimini seçiyor, saatine sonra bakıyor. Serisi riskte olan kullanıcı öğlen saatinde kelime tekrarı ya da quiz bildirimi alamıyor; akşamı bekliyor. Bilinçli olabilir; yazılı bir karar görmedim.
- **Başarısız gönderim iz bırakmıyor** (2.6). Ulaşma ve hata oranını tartışmak için veritabanında bir sayı yok.

## Bilinmeyenler

- iOS'ta kullanıcı başına kaynak; dört alıcının geldiği yer.
- 17 Kasım'da hangi paylaşımın etkili olduğu (Instagram tarafındaki saatle karşılaştırılmalı).
- Gönderim hatası sayısı; bildirimin telefona ulaşma oranı; izin oranı (1.0.4'ten sonra, iOS'ta sınırlı).
- Satın almaya basıp tamamlamayan 18 kişinin nedeni.
