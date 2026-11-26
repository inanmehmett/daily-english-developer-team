# Bildirim metinleri ve deneme hatırlatması: turlu inceleme (son hâl, Mehmet'in onayına)

**Tarih:** 26 Kasım 2026 · **Üç tur + bağımsız göz** (yeni çalışma modu, README). Üyeler kurgusaldır.
- **Tur 1 (taslak):** Paul, Tomris. Taslak 3 (`raporlar/2026-11-26_bildirim_ornekleri_taslak.md`) ve dokunulmamış altı bildirim için yeni taslak.
- **Tur 2 (itiraz):** Nassim, Don, Sean; ölçüt `ortak/uygulamanin_sesi.md` ve Mehmet'in 26 Kasım sözleri.
- **Bağımsız göz:** taslağın gerekçesini görmemiş ayrı oturum; 19 satırın 18'ine "düzelt", 1'ine "ele" dedi.
- **Dayanak (koddan, `fix/push-plain-voice` dalı, `NotificationDispatchService.cs`):** "3 dakika" sabit bir sayı (`TypicalStoryMinutes = 3`), gerçek süre değil · hikâyenin toplam süresi biliniyor (`EstimatedReadingTimeInMinutes`) · seri bildirimleri seçilen saatte gidiyor, yoksa 20:00 · deneme bildirimi yalnız gün adını yazıyor, bitiş saati kayıtta var (`EndDate`) · plan adı değişken · günlük hedef kullanıcının kendi seçtiği dakika.
- **Tur 3 (düzeltme):** aşağıdaki tablo.
**Durum:** editörün PR #23'ü taslak 3'ü taşıyor; **bu tabloya göre güncellenmeden birleştirilmemeli.**

## Turlarda elenenler
| Elenen | Neden | Hangi turda |
|---|---|---|
| "İyi akşamlar, {ad}" | Sabah saatini seçen kullanıcıya da gidiyor; yanlış olur | 2 ve bağımsız göz |
| "3 dakika yeter", "beş dakikalık", "4 dakika" (sabit sayılar) | Kodda sabit; yedi dakikalık hikâyeye "3 dakika" demek söz tutma kuralına aykırı. Süre yalnız hikâyenin gerçek süresinden yazılır | 2 ve bağımsız göz |
| "5 gün oldu" | "Gelmeyeli 5 gün oldu" diye de okunuyor | bağımsız göz |
| "Sorun yok, {ad}" | Bir sorun olduğunu ima ediyor; örtük suçlama | bağımsız göz |
| "10 soru, 2 dakika." | Fiilsiz, etiket gibi; robot sesi | bağımsız göz |
| "Defterindeki kelimelere birlikte bakalım mı?" | Ne olduğunu söylemiyor; "birlikte" olmayan bir şeyi vaat ediyor. Başlığı da deneme başlığına fazla benziyor | bağımsız göz |
| "Rafına yeni bir hikâye eklendi" | "Raf" kişiye özel eklenmiş gibi gösteriyor; açamayacağı hikâyeye "göz at" demek gizli satış | bağımsız göz |
| "Takıldığın / bilmediğin kelimeye dokunman yeter" | Özellik anlatan reklam cümlesi; iki bildirimde tekrar | bağımsız göz |
| "Hikâyen yarım kaldı" | Eksik dili; reddedilen "bıraktığın yerde duruyor" ailesinden | bağımsız göz |
| "Beş dakikan var mı?", "Hangi hikâyeyle başlasak?" | Soru başlık olmaz (kural 2) | 2 |
| "{ad}, bir haftadır görüşmedik", "{ad}, dün ara verdin, sorun yok" | Uzun, kesiliyor; gün sayan sitem | 2 |
| "Seni özledik" (3. günde) | Üç günde abartı; her uygulamanın kalıbı | bağımsız göz |
| "Her şey yerinde", "Hikâyelerin yerinde", "Defterindeki kelimeler de yerinde" | Sistem durum iletisi gibi; boş bilgi | bağımsız göz |
| **30. gün bildirimi ("Kapı hep açık")** | Sitem gibi okunuyor; bir ayda dördüncü "buradayız" mesajı. "Geri dön"e dokunma oranı %0,5. **Tür kaldırılır** | bağımsız göz, ekip kararı |
| Deneme: "Premium kendiliğinden başlar", "yıllık plan başlar" | Ücret alınacağını söylemiyor | 2 ve bağımsız göz |
| Deneme: "cumaya kadar", "perşembeye kadar" | iOS'ta iptal bitişten en az 24 saat önce yapılmalı; gün adı yetmez, saat gerekir | 2 ve bağımsız göz |
| Deneme: "ayarlardan" | Hangi ayar belli değil; iptal Profil'den başlıyor | 2 |
| Deneme: 175–200 karakterlik gövdeler | Kilit ekranında kesilen kısım tam iptal bilgisi | bağımsız göz |
| Deneme (yenileme kapalı): "Premium'da kalmak istersen…" | Satış cümlesi; ücret alınmayacağı da yazmıyordu | bağımsız göz |

## Tur 3 sonu: bildirimler (**geçersiz; yerine en alttaki "Duygu turu" tablosu geçti**)
{n} her yerde gerçek veriden gelir; bilinmiyorsa cümlenin o parçası yazılmaz. {Türkçe ad} hikâyenin Türkçe adı. Adı olan bildirim yalnız kullanıcının o gün açabildiği hikâye için gider.
| Kod | Tür | Başlık | Gövde |
|---|---|---|---|
| N1 | Dün okudu, bugün okumadı | Hikâyen hazır | Bugünün hikâyesi: {Türkçe ad}, {n} dakikalık. Hemen oku. · hikâye bilinmiyorsa: Bugünün hikâyesi açıldı. Hemen oku. · yarım hikâyesi varsa: {Türkçe ad}: kaldığın yerden devam et. |
| N2 | Serisi 3 gün ve üstü, bugün okumadı | Harika gidiyorsun | {n} gündür her gün okuyorsun. Bugünün hikâyesi hazır. |
| N3 | Seri dün kırıldı, bugün okursa geri geliyor | İyi haber | {n} günlük serin geri gelebilir. Bugün bir hikâye bitirmen yeter. |
| N4 | Günün quizi | Günün quizi hazır | Bugün {n} soru var. İstersen bir dene. |
| N5 | Kelime tekrarı | Tekrar günü | Defterinde tekrar günü gelen {n} kelime var. Kısa bir göz at. · 15'ten çoksa sayısız: Defterindeki kelimelerin tekrar günü geldi. Kısa bir göz at. |
| N6 | Yeni hikâye eklendi | Yeni hikâye | Yeni bir hikâye eklendi: {Türkçe ad}. Hemen oku. |
| N7 | Hiç okumamış, 1. gün | İlk hikâyen hazır | {ad}, seviyene göre bir hikâye seçtik: {Türkçe ad}. Hemen oku. |
| N8 | 1. gün, başlamış ama bitirmemiş | Güzel başladın | {Türkçe ad}: kaldığın yerden devam et. |
| N9 | Hiç okumamış, 3. gün | Kısa bir hikâye | Seviyene göre kısa bir hikâye var: {Türkçe ad}. İstersen bugün başla. |
| N10 | Hiç okumamış, 7. gün | Merhaba, {ad} | Sana uygun kısa hikâyeler hazır. İstersen birine göz at. |
| N11 | Günlük hatırlatma (saat seçmiş) | {ad}, okuma vakti | Seçtiğin saat geldi. Bugünün hikâyesi hazır. |
| N12 | 3 gündür gelmiyor | Merhaba, {ad} | Sıradaki hikâyen: {Türkçe ad}, {n} dakikalık. İstersen göz at. |
| N13 | 7 gündür gelmiyor | Hikâyen hazır | {Türkçe ad} seni bekliyor. Ne zaman istersen. |
| N14 | 14 gündür gelmiyor | Acelesi yok | {Türkçe ad} hazır, {n} dakikalık bir hikâye. Ne zaman istersen oku. |
| – | 30 gündür gelmiyor | **kaldırıldı** | – |
Kapalı kalan türler: "günün ücretsiz metni açıldı" ve "yeni rütbe" 12 Kasım'dan beri gönderilmiyor; açmak gönderim düzenini değiştirir, 1.0.4 ölçümünden sonra ayrı karar. "İyi haber / Günün ücretsiz metni açıldı. Hemen oku." (Mehmet'in örneği) o tür açılırsa aynen kullanılır; N1'in gövdesi de aynı cümleden.

## Tur 3 sonu: deneme hatırlatması (**gövdeler en altta güncellendi**)
Başlık (Mehmet'in kararı): **"{ad}, küçük bir hatırlatma"**. {gün} ve {saat} mağazanın bildirdiği bitiş anından hesaplanır; iptal için son an bitişten 24 saat öncesidir. Fiyat yazılmaz (mağazaya ve ülkeye göre değişiyor).
| Kod | Durum | Gövde | Karakter |
|---|---|---|---|
| D1 | Yenileme açık, okumuş | {n} hikâye okudun, eline sağlık. Denemen cuma bitiyor; sonra ücretli yıllık plan başlar. İstemezsen perşembe 14.00'e kadar Profil'den iptal edebilirsin. | ~151 |
| D2 | Yenileme açık, okumamış | Denemen cuma bitiyor; sonra ücretli yıllık plan başlar. İstemezsen perşembe 14.00'e kadar Profil'den iptal edebilirsin. O zamana kadar bütün hikâyeler açık. | ~158 |
| D3 | Yenileme kapalı, okumuş (**yeni tür**) | Denemende {n} hikâye okudun, eline sağlık. Premium denemen cuma bitiyor, ücret alınmayacak. Sonrasında günde bir hikâyeyi ücretsiz okumaya devam edersin. | ~152 |
| D4 | Yenileme kapalı, okumamış (**yeni tür**) | Bütün hikâyeler cumaya kadar sana açık. Premium denemen cuma bitiyor, ücret alınmayacak; sonrasında günde bir hikâye ücretsiz. | ~125 |

## Çözülmeyen itiraz (Mehmet'e)
**Deneme başlığı uzun adlarda kesiliyor.** "Mehmet, küçük bir hatırlatma" 28 karakter; Mehmet'in kendi ekran görüntüsünde başlık 24. karakterde kesilmişti ("Mehmet, dün okudun, bugü…"). Aynı ekranda bu başlık "Mehmet, küçük bir hatırl…" görünür. İki çözüm: (a) ad sonda: "Küçük bir hatırlatma, Mehmet" (kesilirse yalnız ad kesilir), (b) başlık adsız "Küçük bir hatırlatma", ad gövdenin başında. Ekibin önerisi (a).

## Editöre (PR #23'ün güncellenmesi)
1. Metinler bu tablodaki gibi; kayıt sürümü `copy_v4`.
2. `TypicalStoryMinutes` hiçbir metinde kullanılmaz; süre bilinmiyorsa süresiz cümle.
3. Adı geçen hikâye yalnız kullanıcının o gün açabildiği hikâyeyse; değilse adsız cümle.
4. Deneme: bitiş anından 24 saat önceki gün ve saat hesaplanır (yerel saat, saat başına aşağı yuvarlanır); yenilemesi kapalı deneme kullanıcısı için yeni tür (D3, D4).
5. 30. gün "geri dön" kaldırılır.
6. Doğrula ve raporla: N3'te seri gerçekten bugün okuyunca geri geliyor mu ve hangi kullanıcıda (ücretsiz/Premium); N4'te {n} gerçek soru sayısı mı; N7'de "seçtik" dediğimiz hikâye başlangıç yolculuğunun ilk hikâyesi mi; "Profil'den iptal" yolu iki mağazada da çalışıyor mu.
7. Birleştirme ve yayın Mehmet'in sözüyle.


---
# Duygu turu (tur 4 ve 5; 26 Kas 17:31, Mehmet: "Duygu uyandırıyor mu? Psikoloji ekibi inceledi mi?" → "Ekle ve yap")
- **Yeni üye:** BJ Sis, davranış ve duygu (`uyeler/bj_sis_davranis.md`; dayanak BJ Fogg'un davranış modeli: istek, güç yetirme, işaret; alışkanlığı duygu kurar).
- **Tur 4 (duygu taslağı):** BJ, Paul, Tomris. Her bildirim için hedef his yazıldı, başlıklar hisse göre yeniden kuruldu.
- **Bağımsız göz 2:** tek soru: "Bunu kilit ekranında gören ne hisseder, sonra ne yapar?" 16 satırı 0–3 arası puanladı. Üçü 3 ya da ona yakın (deneme, kırılan seri, kendi kelimelerin), beşi 0–1.
- **Tur 5 (düzeltme):** aşağıdaki tablo.

## Bağımsız gözün ana bulgusu
> Set sıcaklığı sıfatla ("güzel", "harika") ve çekingenlikle ("istersen", "acelesi yok") kurmaya çalışıyor. Oysa duygu, kişiye özgü doğru bir bilgiden doğar.
BJ'nin ilkesiyle aynı yere çıkıyor: his, kullanıcının gerçekten yaptığı ya da gerçekten olan bir şeyin söylenmesinden gelir; övgü kelimesinden gelmez.

## Tur 4–5'te elenenler
| Elenen | Uyanan gerçek his | Neden |
|---|---|---|
| "Dün güzel okudun" | öğretmenden yıldız | "Güzel okumak" Türkçede sesli okumaya söylenir; uygulama okumanın güzel olduğunu bilemez |
| "Harika gidiyorsun" | yok | Her uygulamanın söylediği övgü; asıl haber olan sayı gövdeye gömülmüştü |
| "Oyun vakti" | çocuksuluk | Anaokulu zili; yetişkine söylenmez |
| "Güzel başladın" | iğnelenme | Kulak kendiliğinden "…ama bitirmedin" diye tamamlıyor |
| "Kısacık bir hikâye" | yok | Raf etiketi; hikâye 8 dakikaysa yalan |
| "Ne zaman istersen" (7. gün), "Acelesi yok" (14. gün) | "o zaman niye yazdın?" | Telefonu titretip "bir şey yapmana gerek yok" demek kendiyle çelişiyor; üç kez "baskı yok" demek ısrar etmiyormuş gibi ısrar etmek |
| "Aklımıza geldin" | arkadaş taklidi | Üç gün gelmeyen herkese otomatik gidiyor; kimsenin aklına kimse gelmedi. Söz tutma kuralına aykırı |
| "Yerin hazır" | tuhaflık | Neyin yeri belli değil |
| "… seni bekliyor" | örtük suçluluk | Hikâye bekliyor, sen gelmiyorsun |
| "eline sağlık" (okuma için) | eğreti | El emeğine söylenir, okumaya değil |
| "hazır" (sekiz yerde), "istersen" (beş yerde) | kibar garson | Tekrar; birkaç hafta sonra ses arkadaş değil, masaya sürekli gelen garson oluyor |

## Son hâl (tur 5)
Her satırda his, kullanıcıya özgü doğru bir bilgiye yaslanıyor. {n} ve {fiyat} gerçek veriden; bilinmiyorsa o parça yazılmaz.
| Kod | Durum | Başlık | Gövde | His ve dayandığı gerçek |
|---|---|---|---|---|
| E1 | Dün okudu, bugün okumadı | Bugünkü hikâye geldi | Dün okudun, bugünkü de burada: {Türkçe ad}, {n} dakikalık. | Süreklilik; dün okuduğu doğru |
| E2 | 3+ gündür her gün okuyor | {n} gündür okuyorsun | Bir gün bile atlamadın. Bugünkü hikâye geldi. | Gurur; sayı başlıkta |
| E3 | Seri dün kırıldı | İyi haber | {n} günlük okuma serini bugün geri alabilirsin. Bir hikâye bitirmen yeter. | Rahatlama; gerçek kayıp, gerçek çare |
| E4 | Günün quizi | Günün quizi | {n} kısa soru geldi. Canın isterse bir dene. | Hafif oyun; iddiasız |
| E5 | Kelime tekrarı | Senin kelimelerin | Defterine eklediğin {n} kelimeyi tekrar etme günü. Bir göz at. | Sahiplik; kelimeleri kendisi ekledi |
| E6 | Yeni hikâye eklendi | Yeni hikâye geldi | {Türkçe ad} bugün eklendi, {n} dakikalık. Hemen oku. | Yenilik |
| E7 | Hiç okumamış, 1. gün | Hoş geldin, {ad} | İlk hikâyeni seviyene göre seçtik: {Türkçe ad}. {n} dakika sürer, bir bak. | Karşılanmak; seviyesini kendisi belirtti |
| E8 | Başlamış, bitirmemiş | Yerini tuttuk | {Türkçe ad} hikâyesinde kaldığın yer işaretli. Açınca oradan devam edersin. | Düşünülmüş olmak; uygulama gerçekten yeri saklıyor |
| E9 | Hiç okumamış, 3. gün | İlk hikâyen hazır | {Türkçe ad}, {n} dakikalık ve senin seviyende. Bugün bir bak. | "Yapabilirim"; süre ve seviye gerçek |
| E10 | Hiç okumamış, 7. gün | Son hatırlatmamız | İlk hikâyen {Türkçe ad}, {n} dakikalık. Bundan sonra yazmayacağız; canın isteyince aç. | Saygı; **gerçekten son olmalı** |
| E11 | Seçtiği saatte hatırlatma | Okuma vakti | Dönüşümlü: "Çayını al {ad}, bugünün hikâyesi geldi: {Türkçe ad}." (haftada en çok iki kez) · "Bugünkü hikâye {n} dakikalık: {Türkçe ad}." · "{ad}, seçtiğin saat. Bugünkü hikâye: {Türkçe ad}." | Ritüel; saati kendisi seçti |
| E12 | 3 gündür gelmiyor | Selam {ad} | Sıradaki hikâyen {Türkçe ad}, {n} dakikalık. Müsait olunca uğra. | Sade selam; taklit yok |
| E13 | 7 gündür gelmiyor | Yeni hikâyeler var | Bu hafta {n} hikâye eklendi. İlki {Türkçe ad}. · o hafta eklenen yoksa: başlık "Merhaba {ad}", gövde "{Türkçe ad} hazır, {n} dakikalık. Müsait olunca uğra." | Haber; yalnız gerçekten eklendiyse |
| E14 | 14 gündür gelmiyor | Son hatırlatmamız | Bundan sonra seni dürtmeyeceğiz. {Türkçe ad} hazır, {n} dakikalık; canın isteyince buradayız. | Saygı; **sonrasında gerçekten susulur** |
| D1 | Deneme, yenileme açık, okumuş | {ad}, küçük bir hatırlatma | {n} hikâye okudun. Denemen cuma bitiyor, sonra yıllık plan ({fiyat}) başlar. İstemezsen perşembe 14.00'e kadar Profil'den iptal edebilirsin. | Güven |
| D2 | Deneme, yenileme açık, okumamış | aynı | Denemen cuma bitiyor, sonra yıllık plan ({fiyat}) başlar. İstemezsen perşembe 14.00'e kadar Profil'den iptal edebilirsin. O zamana kadar bütün hikâyeler açık. | Güven |
| D3 | Deneme, yenileme kapalı, okumuş | aynı | Denemende {n} hikâye okudun. Denemen cuma bitiyor, senden ücret alınmayacak. Sonra da her gün bir hikâye ücretsiz. | Rahatlama |
| D4 | Deneme, yenileme kapalı, okumamış | aynı | Denemen cuma bitiyor, senden ücret alınmayacak. O güne kadar bütün hikâyeler açık; sonra da her gün bir hikâye ücretsiz. | Rahatlama |

## Ekip kararları (ürün)
1. **Gelmeyen kullanıcıya "geri dön" dizisi üç bildirim:** 3., 7. ve 14. gün. 14. gün "son hatırlatmamız" der ve o kullanıcıya dönene kadar hiçbir bildirim gitmez. 30. gün kaldırıldı.
2. **Hiç okumamış kullanıcıya üç bildirim:** 1., 3., 7. gün; 7. gün son olduğunu söyler ve sonrasında susulur.
3. **Yenilemesi kapalı deneme kullanıcısına hatırlatma** (D3, D4) yeni tür olarak eklenir.
4. **Günlük hatırlatmada dönüşümlü gövde** (E11); gönderim kaydına hangi gövdenin gittiği yazılır.

## Mehmet'e çıkan iki konu
1. **Deneme başlığı kesiliyor** (iki bağımsız göz de söyledi): "Mehmet, küçük bir hatırlatma" 28 karakter, ekranda "Mehmet, küçük bir hatırl…". Öneri: başlık "Küçük bir hatırlatma", ad gövdenin başında ("Mehmet, 5 hikâye okudun. …").
2. **Hikâyenin konusu tek düz cümleyle söylenebilir** ("bir çaycıyla müşterisi hakkında, 4 dakikalık"). Bağımsız göze göre okumaya dair bildirimlerde eksik olan "neden bu hikâye" cevabı. Bu, reddedilen merak cümlesi değil, düz konu bilgisi; ama hikâye başına bir cümle yazmayı gerektirir ve Mehmet'in 26 Kasım sabahki tepkisi nedeniyle **eklenmedi**; karar Mehmet'in.

## Editöre (PR #23; önceki "Editöre" bölümünün yerine)
1. Metinler "Son hâl (tur 5)" tablosundaki gibi; kayıt sürümü `copy_v4`.
2. Sabit `TypicalStoryMinutes` hiçbir metinde kullanılmaz.
3. Adı geçen hikâye yalnız kullanıcının o gün açabildiği hikâyeyse; değilse bildirim o gün gitmez.
4. "Son hatırlatmamız" diyen iki bildirimden (E10, E14) sonra o kullanıcıya, uygulamayı yeniden açana kadar **hiçbir tür gitmez** (deneme bitiş uyarısı hariç). Bu sağlanamıyorsa o iki metin kullanılmaz; raporla.
5. E13'te "bu hafta eklenen hikâye sayısı" son 7 günde eklenen ve kullanıcının seviyesine uyan metinlerden; sıfırsa yedek metin.
6. E11'de üç gövde dönüşümlü; "çay" gövdesi haftada en çok iki kez ve 07–22 arasında.
7. {ad}: yer tutucu, rakam ya da 10 harften uzunsa adsız başlık ("Hoş geldin", "Selam", "Merhaba").
8. Deneme: iptal için son an bitişten 24 saat öncesi, yerel saatle, saat başına aşağı yuvarlanır. {fiyat} sunucuda biliniyorsa yazılır, bilinmiyorsa "ücretli yıllık plan".
9. Doğrula ve raporla: E3 (seri bugün okuyunca geri geliyor mu, kimde), E7 ("seviyene göre seçtik" doğru mu), E8 (uygulama kaldığı yerden açıyor mu), "Profil'den iptal" yolu iki mağazada, 7. günden sonra hiç okumamış kullanıcıya başka bildirim gidiyor mu.
10. Birleştirme ve yayın Mehmet'in sözüyle.
