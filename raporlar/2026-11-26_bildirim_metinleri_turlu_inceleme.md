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

## Son hâl: bildirimler
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

## Son hâl: deneme hatırlatması (bitişten 2 gün önce, bir kez)
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
