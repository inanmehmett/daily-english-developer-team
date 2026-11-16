# Kullanıcılar neden kalmıyor – canlı veritabanı okuması

**Rol:** Nate Gümüş (veri); itirazlar Nassim Talip. **Tarih:** 16 Kasım 2026, 02:40 (TR).
**Görev:** `ortak/editor_gorevi_2026-11-15_neden_kalmiyorlar.md`. Yalnız okuma; canlıda hiçbir satır değişmedi.

## En üstte beş satır

1. **Kayıp ilk günde ve ilk metnin içinde.** 166 müşterinin 107'si (%64) en fazla bir gün görüldü. Gidenlerin 151'inden 101'i okumaya başladı, 51'i bir metni bitirdi, 32'si ikinci metne geçti.
2. **Dönüşle birlikte görülen davranış ilk gün bir metni bitirmek.** İlk gün hiç okumayanların ertesi gün dönüşü 3/58, başlayıp bitirmeyenlerin 7/63, bir metin bitirenlerin 19/53, iki ve üzeri bitirenlerin 7/11.
3. **Desteklenen hipotez:** ilk metin önemli. A2 ve B1 seçenlerin çoğuna ilk metin olarak düşen "Why Penguins Can't Fly" 63 okurdan 23'ünde bitti (%37); A1'in ilk metni "Two Cups" 51 okurdan 29'unda (%57).
4. **Çürüyen hipotezler:** "Çok kelimeye bakan zorlanıp bırakıyor" tutmadı; en çok bakan dilim en çok bitiren ve en çok dönen dilim. "Ücretsiz içerik bitince gidiyorlar" da tutmadı; üç açık metnin hepsini bitiren 1 kişi var.
5. **Bilemediklerimiz:** bildirim izni oranı (alan 191 müşterinin hepsinde boş), bildirimin cihaza ulaşıp ulaşmadığı, bildirimin dönüşe etkisi (karşılaştırma grubu yok), müşterilerin kendi sözleri (hiç mesaj yok).

## Yöntem

- **Kimler:** `Users.AccountKind = 'customer'`, 191 hesap (125 iOS, 66 Android). Kayıt tarihleri 29 Ekim – 15 Kasım.
- **Kayıt anı:** `UserProfiles.CreatedAt`. `Users` tablosunda oluşturma tarihi yok.
- **Gün:** UTC+3 takvim günü. "N. gün döndü" = kayıt gününden N gün sonraki takvim gününde `UserEvents`'te hata dışında en az bir olay.
- **Kimler sayılır:** D1 için 14 Kasım ve öncesi kaydolanlar (185), D3 için 166, D7 için 126.
- **Nasıl çalıştı:** Canlıda geçici tablo açılamadığı için müşteri hesaplarının satırları (e-posta ve ad olmadan) yerel bir çalışma veritabanına kopyalandı, sorgular orada koştu. Kopya iş bitince silinecek.
- **Ölçümün alt sınır olduğu yer:** sunucunun `LastSeenAt` alanına göre kayıt gününden sonra görülen 78 kişi var; olaylara göre 62. Yani olay kaydı dönenlerin yaklaşık beşte birini kaçırıyor. Aşağıdaki dönüş oranları alt sınırdır.

## S1. Dönüş eğrisi

| | Ertesi gün (D1) | 3. gün (D3) | 7. gün (D7) | 1–7. günlerde en az bir kez |
|---|---|---|---|---|
| Hepsi | 36/185 (%19) | 17/166 (%10) | 3/126 (%2) | 45/126 (%36) |
| iOS | 29/121 (%24) | 14/105 (%13) | 3/74 (%4) | 32/74 (%43) |
| Android | 7/64 (%11) | 3/61 (%5) | 0/52 | 13/52 (%25) |

| Kayıt haftası | D1 | D3 | D7 |
|---|---|---|---|
| 26 Eki | 3/27 | 2/27 | 0/27 |
| 2 Kas | 22/99 | 12/99 | 3/99 |
| 9 Kas | 11/59 | 3/40 | henüz yok |

| Sürüm (ilk olaydaki) | D1 | D3 |
|---|---|---|
| iOS 1.0.1 (43) | 14/49 | 8/49 |
| iOS 1.0.2 (45) | 13/56 | 5/40 |
| Android 1.0.2 (45) | 1/16 (az veri) | 0/13 (az veri) |
| Android, sürüm yazılmamış | 5/46 | 2/46 |

Okuma: Apple'ın sayısıyla (D1 yaklaşık %10, D7 yaklaşık %5) D7 uyuşuyor (iOS 3/74), D1 uyuşmuyor (iOS %24). Apple yalnız veri paylaşımına izin verenleri ve kendi gün tanımını sayıyor; iki kaynak aynı şeyi ölçmüyor. Android iOS'un yarısı kadar dönüyor. Android olaylarının 46 müşteride sürüm alanı boş; Android'i sürüme göre ayıramıyoruz. **Hipotez.**

Görülen gün sayısı (12 Kasım ve öncesi kaydolan 166 müşteri): 0 gün 19, 1 gün 88, 2 gün 32, 3–5 gün 22, 6 ve üzeri 5.

## S2. İlk 24 saat ve dönüş

| İlk 24 saatte | D1 | 1–7. günlerde dönen |
|---|---|---|
| Hiç okumadı | 3/58 (%5) | 8/45 (%18) |
| Başladı, bitirmedi | 7/63 (%11) | 10/38 (%26) |
| 1 metin bitirdi | 19/53 (%36) | 22/36 (%61) |
| 2 ve üzeri bitirdi | 7/11 (%64, az veri) | 5/7 (az veri) |

Okumaya başlayanlar içinde (127 kişi), yapan ve yapmayanın D1'i:

| Davranış | Yaptı | Yapmadı |
|---|---|---|
| Cümle çevirdi | 17/31 (%55) | 16/96 (%17) |
| Deftere kelime ekledi | 16/49 (%33) | 17/78 (%22) |
| Metin quizi yaptı | 14/41 (%34) | 19/86 (%22) |
| Cümle dinledi | 27/103 (%26) | 6/24 (%25) |

Okuma: en keskin ayrım "bir metni bitirdi mi". Cümle çevirisi kullananlar belirgin biçimde daha çok dönüyor; dinleme ayırt etmiyor (zaten 127 kişinin 103'ü dinlemiş). Günün quizine giriş müşteri sürümlerinde kaydedilmiyor; ölçülemedi. **Hipotez; bağıntı, neden değil.**

## S3. İlk metin

| İlk açılan metin | Seviye | Kelime | Okur | Bitiren | D1 | 50 kelimede bakış |
|---|---|---|---|---|---|---|
| Why Penguins Can't Fly | B1 | 332 | 63 | 23 (%37) | 14/63 | 2,8 |
| Two Cups | A1 | 217 | 51 | 29 (%57) | 15/50 | 3,0 |
| The Island Where Rabbits Won | A2 | 287 | 13 (az veri) | 7 | 2/10 | 5,5 |
| The Village That Whistles | B1 | 281 | 6 (az veri) | 3 | 1/5 | 1,3 |

Kimin önüne hangisi düşüyor: A1 seçen 39 kişi "Two Cups" ile, A2 seçen 35 kişi ve B1 seçen 20 kişi "Why Penguins Can't Fly" ile başlamış. A2 seçenlerden 8'i "Rabbits" ile başlamış.

Okuma: Paul Ulus'un "Rabbits etiketinden zor" hipotezini bakış sayısı destekliyor (50 kelimede 5,5; diğerlerinin iki katı), bitirme oranı desteklemiyor; 13 okurla hüküm verilmez. Asıl büyük grup "Penguins": A2 seçen okura B1 etiketli, 332 kelimelik bir metin düşüyor ve üçte ikisi bitirmiyor. Bitirmeyenlerin metindeki ortanca etkin süresi 1,3 dakika. **Hipotez.**

## S4. Kelimeye bakma yoğunluğu (ilk metin)

Müşteri sürümlerinde kelime bakışı metin kimliği taşımıyor; bakışlar ilk metnin açılışı ile bir sonraki metnin açılışı arasındaki zamana göre atandı.

| 50 kelimede bakış | Okur | Bitiren | D1 |
|---|---|---|---|
| Hiç | 20 | 8 (%40) | 6/20 |
| 0–1 | 33 | 11 (%33) | 5/31 |
| 1–3 | 32 | 14 (%44) | 5/32 |
| 3 üzeri | 53 | 31 (%58) | 18/50 (%36) |

Okuma: çok bakan bırakmıyor; tersine en çok bitiren ve dönen dilim. Bakmak zorluğun değil ilginin işareti gibi duruyor. **Hipotez.**

## S5. Nerede bıraktılar

12 Kasım ve öncesi kaydolup son üç gündür (13–15 Kasım) görünmeyen 151 müşteri (166'nın %91'i).

Ulaştıkları en ileri nokta: onboarding'i bitiren 147, okumaya başlayan 101, bir metni bitiren 51, quiz yapan 33, ikinci bir metne başlayan 32.

| Son oturumdaki son olay | Kişi |
|---|---|
| Okuma sürüyor (`reading_active`) | 30 |
| Hiç olay yok | 19 |
| Uygulamayı açtı, başka olay yok | 16 |
| Premium şeridi ya da kilitli içerik kaydı | 20 |
| Kelimeye baktı | 11 |
| Cümle dinledi | 10 |
| Sıradaki okuma önerisi gösterildi | 9 |
| Metni bitirdi | 9 |

Oturum sayısı: 0 oturum 19, 1 oturum 23, 2 oturum 57, 3–5 oturum 37, 6 ve üzeri 15.

Okuma: en büyük grup metnin ortasında kalanlar (okuma, bakış, dinleme, çeviri: 53 kişi, %35). 16 kişi uygulamayı yeniden açıp hiçbir şey yapmadan çıkmış. 20 kişinin son kaydı bir Premium teması. **Hipotez.**

## S6. Ücretsiz içerik sınırı

- Kilitsiz üç metin var (Two Cups, Thirty-One Mornings, The Island Where Rabbits Won). Üçünü de bitiren 1 müşteri, ikisini bitiren 4, birini bitiren 41.
- Günlük açılan metni en az bir kez açan 35 müşteri; 29'u yalnız bir kez.
- Kilide çarpma sınıra varmadan oluyor: 48 müşteri kilitli bir kitabın ön izlemesini açmış, 36 müşteri kilitli bir dizi bölümüne 192 kez dokunmuş.
- İlk metnini bitiren 72 müşterinin 40'ı sonraki 30 dakikada bir kilide ya da paywall'a çarpmış. Bunların D1'i 17/38; çarpmayanların 10/32.
- **Kodla doğrulanan bulgu:** bitiş ekranındaki "sıradaki okuma" kartı kilitli kitabı önermiyor ama dizilerde kilit denetimi yok (`book_list_view_model.dart`, `nextReadingSuggestion`). 41 müşteriye dizi önerilmiş (çoğu "New in Town" ve "Game Day"); bu dizilerin ücretsiz bölümü yok. 41 kişinin 21'i beş dakika içinde kilide çarpmış.

Okuma: kimse ücretsiz içeriği tüketip gitmiyor. Kilide çarpanlar daha az dönmüyor; ama bu grup zaten metin bitirmiş, ilgili okurlar. Öneri kartının ücretsiz okuru kilitli diziye götürmesi tasarımın kendi sözüyle çelişiyor (kod yorumu: "öneri kartı bir davet, ödeme teklifine giden kapı değil"). **Bulgu; karar Don Normal ve Sean Büyüt'te.**

## S7. Bildirim

- **İzin oranı bilinmiyor.** `OsNotificationPermission` 191 müşterinin hepsinde boş; alanı dolduran sürüm müşterilerin elinde değil. Bildirim adresi (token) olan: iOS 122/125, Android 51/66. Token izin demek değildir.
- **Ulaşma bilinmiyor.** `ReceivedAt` 803 gönderimin hepsinde boş; Android'de ulaşmayı ölçen sürüm de henüz yayında değil.
- 177 müşteriye 803 bildirim gitti. Günde birden fazla alan 2 kişi-gün var.

| Tür | Gönderim | 2 saat içinde uygulamada | Bildirime dokunan |
|---|---|---|---|
| Günlük açılan metin | 154 | 3 | 1 |
| Günün quizi | 146 | 10 | 2 |
| Kelime tekrarı | 126 | 3 | 0 |
| Seri başlat | 116 | 5 | 2 |
| İlk okumaya çağrı | 109 | 1 | 1 |
| Geri dön | 96 | 1 | 0 |
| Seri hatırlatma | 24 | 6 | 4 |
| Günlük hatırlatma | 21 | 3 | 0 |
| Toplam | 803 | 33 (%4) | 10 (%1,2) |

- İlk bildirimini aldıktan sonra uygulamaya bir kez bile dönen: 50/177.
- İlk 3 günde bildirim alan ve token'ı olanlarda D3: 13/122; token'ı olup bildirim almayanlarda 3/29. Gruplar rastgele ayrılmadı; fark okunmaz.
- Ertesi gün dönen 37 kişinin o gün yaptıkları: 30'u okudu, 12'si quiz yaptı, 9'u günlük metni açtı, 2'si bildirimden geldi.
- Hatırlatma saati seçen 48/191 (42'si 20:00).
- Gönderim saatleri kullanıcının kendi saatine göre 09–22 arasında; 62 gönderim 22:00–22:59'da. Sunucudaki sınır 09–23 (`CampaignTriggerService`), ekip kuralı (README madde 9) 09–21 diyor.
- Yeni metinler (`copy_v2`, 12 Kasım'dan beri): 235 gönderim; ayrı okumak için sayı az.

Okuma: bildirim şu an dönüş getirmiyor ya da getirdiğini göremiyoruz. Hangisi olduğunu izin ve ulaşma alanları dolmadan ayıramayız. **Bilinmiyor.**

## S8. Erken Premium teması

İlk 30 dakikada: şerit de paywall da görmeyen 9 kişi (D1 2/9), yalnız şerit gören 128 (D1 20/128), ikisini de gören 48 (D1 14/48).

Okuma: şeridi görmeyen grup 9 kişi; karşılaştırma yapılamaz. Paywall görenlerin daha çok dönmesi, paywall'un ancak içerikte gezen okura çıkmasından. **Okunamıyor.**

## S9. Kalanlar

Kayıttan 7 gün ve sonrasında en az bir kez görülen 13 müşteri (126'da %10): 7 iOS, 6 Android.

- Yalnız 2'si sık kullanıcı (10 ve 8 etkin gün). İkisi de "Two Cups" ile başlamış, ilk gün bitirmiş, quiz yapmış, dinlemiş.
- Kalan 11'i 7–14 günlük sürede 2–6 gün görülmüş; 3'ü hiç okumaya başlamamış.
- Android'deki 6 kişinin 5'i Instagram bağlantısından gelmiş.
- İlk metin: 5 "Two Cups", 5 "Penguins", 3'ünde okuma yok.

Okuma: "kalan" dediğimiz grubun çoğu ara sıra uğrayanlar. Düzenli okur 2 kişi; onlardan genelleme yapılmaz. **Az veri.**

## S10. Kullanıcıların kendi sözleri

`UserFeedbacks`'te müşteri hesabından gelen mesaj yok. Tablodaki üç mesajın hepsi geliştirici ve testçi hesaplarından. Mağaza yorumları bu sorguya dahil değil.

## S11. Geliş kaynağı

| Kaynak | Müşteri | D1 |
|---|---|---|
| iOS App Store (kaynak ayrımı yok) | 124 | 29/121 (%24) |
| Android, Play'de organik | 25 | 1/24 |
| Android, Instagram profil bağlantısı | 25 | 5/24 |
| Android, Instagram hikâye | 11 | 1/11 (az veri) |
| Android, kaynak boş | 4 | 0/4 (az veri) |

Okuma: Android'de Play'den kendiliğinden gelenler neredeyse hiç dönmüyor; Instagram profilinden gelenler iOS düzeyine yakın. **Hipotez (24'er kişi).**

Seçilen seviyeye göre D1: A1 13/72, A2 13/66, B1 7/35. Fark yok.

## İtirazlar (Nassim Talip)

1. **Hayatta kalan yanlılığı.** "Bitiren dönüyor" cümlesi nedeni göstermez. Bitiren kişi zaten hevesli olabilir; metni bitirtmek aynı kişiyi geri getirmeyebilir.
2. **Küçük sayılar.** Tabloların çoğunda hücreler 10–60 kişi. D7'de 3 kişi var; bir kişi oranı üçte bir oynatır.
3. **Ölçüm eksik sayıyor.** Olay kaydı dönenlerin yaklaşık beşte birini kaçırıyor; 19 müşterinin hiç olayı yok. Android'de bu kayıp daha büyük olabilir; "Android daha az dönüyor" kısmen ölçüm farkı olabilir.
4. **Test hesabı sızıntısı.** `AccountKind` elle ve kuralla atanıyor. Müşteri sayılan hesapların arasında tanıdık ve ekip cihazı olabilir; özellikle en sık kullanan 2 kişi için bu kontrol edilmedi.
5. **S4'teki atama yaklaşık.** Bakışlar metne zaman aralığıyla bağlandı; aynı oturumda iki metin açan okurda kayma olur.
6. **Bildirim tablosu neden-sonuç değil.** "2 saat içinde uygulamada" olanların bir kısmı bildirim olmasa da gelecekti; 20:00 zaten okuma saati.
7. **18 günlük veri.** Hepsi lansman haftalarının kitlesi. Sonraki kitle farklı davranabilir.

## Ek: sorgular

Canlıdan yalnız müşteri satırları şu tablolardan okundu: `Users`, `UserProfiles`, `UserEvents`, `PushNotificationLogs`, `FreeTextUnlocks`, `PaywallAnalyticsEvents`, `ReadingProgresses`, `UserVocabularies`, `UserFeedbacks`, `ReadingTexts`, `Subscriptions`, `Series`. Bağlantı `default_transaction_read_only = on` ile açıldı. Sorgular yerel kopyada tek tek koşturuldu; depoya betik olarak kaydedilmedi. Tekrarlamak isteyen aynı tanımlarla (yukarıdaki "Yöntem") yeniden yazmalı.
