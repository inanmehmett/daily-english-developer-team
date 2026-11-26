# Editör raporu: bildirim metinleri, onaylı son hâl (copy_v4)

**Tarih:** 26 Kasım 2026 · **Görev:** `ortak/editor_gorevi_2026-11-26_bildirim_metinleri.md`
**Durum: canlıda (26 Kas 23:20).** Mehmet: "Birleştir ve yayınla." [Sunucu #24](https://github.com/inanmehmett/DailyEnglish/pull/24) GitHub testi geçtikten sonra birleştirildi; dağıtım başarılı, API cevap veriyor, yayından sonraki günlükte hata yok. Bildirimler 23:00'ten sonra gitmediği için ilk `copy_v4` gönderimleri **27 Kasım 09:05'ten itibaren** beklenir; canlıda henüz gözlenmedi.

**Bu akşam taslak 3 ile gidenler (`copy_v3`, 17:30–23:00, müşteriler):** 59 gönderim, 1 dokunma (kelime tekrarı). Geri dön 21, seri başlat 11, seri 6, ilk okuma 6, kelime tekrarı 6, günün quizi 5, günlük hatırlatma 4. Bir gönderim hatası kayıtlı. Tek akşam; karşılaştırma için az.

## Önce bilinmesi gereken: PR #23 zaten yayında
Görev "PR #23'ün bugünkü hâlini birleştirme" diyor. PR #23, Mehmet'in "hepsini sen yap" sözüyle **17:30'da birleştirildi ve yayına girdi**; görev dosyası 17:45'te yazıldı. Bu yüzden:
- Canlıda şu an taslak 3 metinleri gidiyor (`copy_v3`): "İyi akşamlar", "5 gün oldu", "Seni özledik" ve öbürleri. Bu akşam 20:00–21:00 arasındaki gönderimler bu metinlerle gidecek.
- #23 güncellenemez (birleşmiş). Bu görev **yeni bir PR** olarak `master`'ın üstüne yazıldı ve taslak 3'ün yerine geçer.
- Karar Mehmet'te: yeni PR bu akşamki gönderimden önce yayına alınsın mı, yoksa bir akşam taslak 3 ile mi gidilsin.

## 1. Doğrulama tablosu (koddan ve canlı veriden)
| Satır | Soru | Cevap | Sonuç |
|---|---|---|---|
| E3 | Kırılan seri bir hikâye bitirince geri geliyor mu; ücretsiz ve Premium'da aynı mı? | Evet. Onarım, okur bir hikâyeyi ya da bölümü bitirdiğinde sunucuda kendiliğinden yapılıyor (kırılmadan sonraki 48 saat içinde). Premium'da her zaman; ücretsizde 30 günde bir. Bildirim zaten yalnız hakkı açık olana gidiyor | Tutuyor, uygulandı |
| E4 | {n} gerçek soru sayısı mı? | Günün quizi her zaman 10 soru (sabit set boyutu). Eski kod okurun önceki turundaki sayıyı yazıyordu; artık setin kendi boyutu yazılıyor | Tutuyor, uygulandı |
| E7, E9 | Adı geçen hikâye seviyenin başlangıç yolculuğunun ilk hikâyesi mi; seviyesi bilinmeyende? | Evet: okurun seviyesinin başlangıç yolculuğundaki ilk bitirmediği durak. Seviye profilde hiç boş kalmıyor (varsayılan A1); B2 ve üstüne B1 yolculuğu atanıyor. Canlıda üç başlangıç yolculuğunun bütün durakları ücretsiz açılabilen metinler ve hepsinin Türkçe adı var | Tutuyor, uygulandı |
| E8 | Uygulama kaldığı yerden açıyor mu? | Evet, kapak sayfasından "oku"ya basınca okuyucu son okunan yeri yüklüyor. **Sınır:** yer telefonda saklanıyor; uygulamayı silip kuran ya da başka telefona geçen okurda baştan açılır | Tutuyor, uygulandı |
| E10 | 7. günden sonra hiç okumamışa başka tür gidiyor mu? | Gidebiliyordu: ilgi alanına yeni metin gelirse "yeni içerik" bildirimi. Kural 2 için ayrı bir kapı yazıldı (aşağıda) | Kapı ile tutuyor, uygulandı |
| E13 | "Son 7 günde eklenen, seviyeye uyan metin sayısı" hesaplanabiliyor mu? | Evet (metnin eklenme tarihi ve seviyesi kayıtta). Canlıda son 7 günde eklenen metin yok; bugün herkes E13b alır | Tutuyor, uygulandı |
| D1–D4 | "Profil'den iptal" çalışıyor mu? | **Kısmen.** Android'de her sürümde çalışıyor (iptali sunucu Google'da yapıyor). iOS'ta uygulama okuru App Store'un abonelik sayfasına ancak 1.0.4'ten itibaren götürüyor; iOS 1.0.2'de sunucu "aboneliğin App Store'dan yönetiliyor" cevabını dönüyor; eski uygulamanın bunu ekranda nasıl gösterdiğine bakılmadı | Aşağıdaki sapmayla uygulandı |
| D1–D4 | Mağaza bitiş anı saatle kayıtta mı? | Evet (ör. 1 Aralık 16:40) | Tutuyor |
| D1–D4 | {fiyat} sunucuda var mı? | **Hayır.** Fiyat mağazadan geliyor, sunucuda güvenilir bir kaynağı yok | Yedek hâl: "ücretli yıllık plan" |

## 2. Uygulananlar
Bütün satırlar (E1–E14, E13b, D1–D4) tablodaki metinle, kelimesi kelimesine uygulandı; her satır ayrı testle kilitli. Ayrıca:
- **Kural 1, açılabilen hikâye:** bir hikâye yalnız okur onu bugün açabiliyorsa adıyla anılıyor. Ölçüt uygulamadaki kuralın aynısı: Premium her şeyi; ücretsiz okur her zaman açık metinleri, daha önce açtıklarını, bugünün hakkı duruyorsa havuzdaki bir metni ya da yolculuğundaki sıradaki ücretsiz durağı açabilir. Denetim hiçbir şey yazmıyor (yolculuk atamıyor, hak harcamıyor).
- **Kural 2, "son hatırlatmamız":** E10 ya da E14 giden okura, uygulamayı yeniden açana kadar yalnız deneme hatırlatması gidiyor. "Açma" = uygulamadan gelen herhangi bir olay, oturum yenileme ya da okuma. Süre sınırı yok.
- **Kural 3, ad:** yer tutucu, rakam ya da "@" içeren ve 10 harften uzun adlar adsız başlık ve adsız gövde alıyor (sınır 12'ydi).
- **Kural 4, E11:** üç gövde sırayla dönüyor (a → b → c), üst üste aynısı gitmiyor; "çayını al" haftada en çok iki kez ve yerel 07–22 arasında.
- **Kural 5, dokununca:** adı geçen hikâyenin kapak sayfası (E1, E6, E7–E14); E4 quiz, E5 kelime sekmesi (değişmedi).
- **Geri dön, 30. gün** kaldırıldı.
- **Ölçüm:** kayıtta sürüm ve metnin anahtarı birlikte: `copy_v4:E12`, `copy_v4:E11a`, `copy_v4:D3`. Yalnız E11 değil, bütün türler anahtarlı; tür başına dokunma oranı doğrudan sayılır.

## 3. Onaylı metinden sapmalar ve uygulanmayanlar
| Konu | Ne yapıldı | Neden |
|---|---|---|
| D1, D2: "Profil'den iptal edebilirsin" | Android'de ve iOS 1.0.4 ve üstünde aynen. iOS'ta eski sürümde (ya da sürümü bilinmeyende) "Profil'den" sözü düşüyor: "…kadar iptal edebilirsin." | Sözün tutulmadığı yerde verilmemesi için. Canlıda etkin iOS müşterilerinin dörtte üçü hâlâ 1.0.2'de |
| D1–D4: dokununca Profil'deki üyelik kartı | **Uygulanmadı.** Dokunuş ana sayfayı açıyor (bugünkü gibi) | Hedefi uygulama belirliyor; sunucudan değiştirilemiyor. Uygulama değişikliği gerekir (derleme 51) |
| D1, D2: {fiyat} | "sonra ücretli {plan} başlar" | Görevdeki yedek hâl; fiyat sunucuda yok |
| E6: "bugün eklendi" | Yalnız okurun yerel gününde eklenmiş metin için gidiyor (önceki pencere 2 gündü) | "Bugün" sözü doğru olsun diye |
| E7, E9–E14, E11: açılabilen hikâye yoksa | **Bildirim o gün gitmiyor** | Bu satırların hikâyesiz hâli verilmedi (yalnız E1'in var). Ekip hikâyesiz metin verirse eklenir |
| E8: hangi gün | Yarım hikâyesi olan hiç-bitirmemiş okura 1., 3. ve 7. günün üçünde de E8 | Görev gün belirtmiyor; yarım hikâyesi varken "ilk hikâyen" demek yanlış olurdu |
| E11 (b) | Hikâyenin süresi bilinmiyorsa bu gövde atlanır; hiçbir gövde uymuyorsa o gün hatırlatma gitmez | Sürenin uydurulmaması için (canlıda 287 metnin 281'inde süre var) |
| E13 | "İlki" o hafta ilk eklenen metin; okur onu bugün açamıyorsa E13b gider | Kural 1 |
| {gün} ve {son gün} | Yalın gün adı: "Denemen cuma bitiyor", "perşembe 14.00'e kadar" | Ekibin inceleme raporundaki örnekler böyle |

**Hacim etkisi (ölçülmedi, dürüst tahmin):** hikâyesi bilinmeyen okura E11, E12–E14 ve ilk okuma bildirimleri artık gitmiyor. Yolculuğu atanmamış okur (1.0.2 kullanıcıları) için seviyesinin başlangıç yolculuğundaki ilk bitirmediği hikâye kullanıldığı için çoğu okurun hikâyesi var; hikâyesiz kalanlar başlangıç yolculuğunu bitirmiş 1.0.2 kullanıcıları ve sıradaki durağı Premium'da olan ücretsiz okurlar. Gerçek sayı yayından sonraki ilk gün kayıttan okunur.

## 4. Doğruluğu ayrıca kontrol edilen sözler
- **"Dün okudun", "{n} gündür okuyorsun, bir gün bile atlamadın":** seri, okurun yerel günü bitince saatlik bakım işiyle kırılıyor; akşam bildirimi gittiğinde sayı kesintisiz gün sayısıdır.
- **D3, D4 "senden ücret alınmayacak":** denemede yenilemesi kapalı kayıtta mağaza ücret almaz. **"Sonra da her gün bir hikâye ücretsiz":** ücretsiz okurun günlük açma hakkı 1.
- **E3 "bugün geri alabilirsin":** bildirim yalnız kırılma gününde ve hakkı açık olana gidiyor.

## 5. Test
- Yeni: `PushTextTests` (tablonun her satırı, saat eki, gövde dönüşümü, iptal sözünün koşulu), `NotificationDispatchOpenableStoryTests` (açılabilen hikâye kuralı, E6, E8, E13, E13b), deneme hatırlatmasının beş durumu, "son hatırlatmamız" kapısının üç durumu.
- Tam takım: **1870 geçti, 0 kaldı, 3 atlandı.**

## 6. Mehmet'ten beklenen
1. **Birleştirme ve yayın kararı** (yeni PR). Birleşince yayına girer; betik ya da veri değişikliği yok.
2. Bu akşamki gönderim (20:00–21:00) taslak 3 metinleriyle gidecek; yeni PR'ı ondan önce yayına almak istersen söylemen yeter.

## 7. Ekibe
- Hikâyesiz hâller: E7, E9, E10, E11, E12, E13b, E14 için metin (ya da "gitmesin" kararı).
- D1–D4'te dokununca Profil: derleme 51'e ihtiyaç tanımı.
- iOS 1.0.2'de "Profil'den" sözünün düşmesi uygun mu.
