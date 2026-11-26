# Editör görevi: bildirim metinleri, onaylı son hâl (PR #23'ün güncellenmesi)

**Veren:** ekip (Paul, Tomris, BJ Sis, Nassim) · **Onay:** Mehmet, 26 Kas 2026 17:44 ("onay… editöre emir için hazırla").
**Dayanak:** `raporlar/2026-11-26_bildirim_metinleri_turlu_inceleme.md` (beş tur, iki bağımsız göz). Bu dosya o raporun uygulanacak özetidir; çelişki olursa bu dosya geçerlidir.
**Sınır:** kodu yaz, testleri koş, PR #23'ü güncelle. **Birleştirme ve yayın Mehmet'in sözüyle.** Canlı veriye yazma yok.
**Önemli:** PR #23'ün bugünkü hâli (taslak 3) birleştirilmeyecek; bu görev onun yerine geçer. Kayıt sürümü `copy_v4`.

## 1. Metinler
{n} ve {fiyat} her yerde gerçek veriden gelir; bilinmiyorsa cümlenin o parçası yazılmaz (aşağıda "süresiz" hâller verildi). {Türkçe ad}: `SubtitleTR`, yoksa `Title`. Sabit `TypicalStoryMinutes` hiçbir metinde kullanılmaz.

| Kod | Tür (koddaki) | Koşul | Başlık | Gövde |
|---|---|---|---|---|
| E1 | StreakStart | serisi 1–2 gün, bugün okumamış | Bugünkü hikâye geldi | Dün okudun, bugünkü de burada: {Türkçe ad}, {n} dakikalık. · süresiz: Dün okudun, bugünkü de burada: {Türkçe ad}. · hikâye bilinmiyorsa: Dün okudun, bugünkü hikâye de geldi. |
| E2 | Streak | serisi 3 gün ve üstü, bugün okumamış | {n} gündür okuyorsun | Bir gün bile atlamadın. Bugünkü hikâye geldi. |
| E3 | StreakRepair | bugünkü koşul | İyi haber | {n} günlük okuma serini bugün geri alabilirsin. Bir hikâye bitirmen yeter. |
| E4 | günün quizi | bugünkü koşul | Günün quizi | {n} kısa soru geldi. Canın isterse bir dene. |
| E5 | kelime tekrarı | bugünkü koşul | Senin kelimelerin | Defterine eklediğin {n} kelimeyi tekrar etme günü. Bir göz at. · {n} 15'ten büyükse: Defterine eklediğin kelimeleri tekrar etme günü. Bir göz at. |
| E6 | yeni içerik | bugünkü koşul + kullanıcı o hikâyeyi bugün açabiliyor | Yeni hikâye geldi | {Türkçe ad} bugün eklendi, {n} dakikalık. Hemen oku. |
| E7 | ilk okuma, 1. gün | hiç etkinliği yok | Hoş geldin, {ad} · adsız: Hoş geldin | İlk hikâyeni seviyene göre seçtik: {Türkçe ad}. {n} dakika sürer, bir bak. |
| E8 | ilk okuma, yarım hikâye | bir hikâyeye başlamış, bitirmemiş | Yerini tuttuk | {Türkçe ad} hikâyesinde kaldığın yer işaretli. Açınca oradan devam edersin. |
| E9 | ilk okuma, 3. gün | hiç etkinliği yok | İlk hikâyen hazır | {Türkçe ad}, {n} dakikalık ve senin seviyende. Bugün bir bak. |
| E10 | ilk okuma, 7. gün | hiç etkinliği yok | Son hatırlatmamız | İlk hikâyen {Türkçe ad}, {n} dakikalık. Bundan sonra yazmayacağız; canın isteyince aç. |
| E11 | günlük hatırlatma | bugünkü koşul | Okuma vakti | üç gövde dönüşümlü, bkz. 2.4 |
| E12 | geri dön, 3. gün | bugünkü koşul | Selam {ad} · adsız: Selam | Sıradaki hikâyen {Türkçe ad}, {n} dakikalık. Müsait olunca uğra. |
| E13 | geri dön, 7. gün | son 7 günde kullanıcının seviyesine uyan en az bir metin eklenmiş | Yeni hikâyeler var | Bu hafta {n} hikâye eklendi. İlki {Türkçe ad}. · {n}=1 ise: Bu hafta yeni bir hikâye eklendi: {Türkçe ad}. |
| E13b | geri dön, 7. gün | eklenen yok | Merhaba {ad} · adsız: Merhaba | {Türkçe ad} hazır, {n} dakikalık. Müsait olunca uğra. |
| E14 | geri dön, 14. gün | bugünkü koşul | Son hatırlatmamız | Bundan sonra seni dürtmeyeceğiz. {Türkçe ad} hazır, {n} dakikalık; canın isteyince buradayız. |
| – | geri dön, 30. gün | – | **kaldırılır** | – |

### Deneme hatırlatması (bitişten 2 gün önce, bir kez)
Başlık dördünde de **"Küçük bir hatırlatma"** (Mehmet'in seçtiği söz; ad başlıkta kesildiği için gövdenin başına alındı). Adı olmayan kullanıcıda gövde adsız başlar.
| Kod | Koşul | Gövde |
|---|---|---|
| D1 | yenileme açık, denemede en az bir hikâye bitirmiş | {ad}, {n} hikâye okudun. Denemen {gün} bitiyor, sonra {plan} ({fiyat}) başlar. İstemezsen {son gün} {saat}'e kadar Profil'den iptal edebilirsin. |
| D2 | yenileme açık, hiç bitirmemiş | {ad}, denemen {gün} bitiyor, sonra {plan} ({fiyat}) başlar. İstemezsen {son gün} {saat}'e kadar Profil'den iptal edebilirsin. O zamana kadar bütün hikâyeler açık. |
| D3 | **yeni tür:** yenileme kapalı, en az bir hikâye bitirmiş | {ad}, denemende {n} hikâye okudun. Denemen {gün} bitiyor, senden ücret alınmayacak. Sonra da her gün bir hikâye ücretsiz. |
| D4 | **yeni tür:** yenileme kapalı, hiç bitirmemiş | {ad}, denemen {gün} bitiyor, senden ücret alınmayacak. O güne kadar bütün hikâyeler açık; sonra da her gün bir hikâye ücretsiz. |
- {n}=1 ise "bir hikâye okudun".
- {plan}: "haftalık plan" / "aylık plan" / "yıllık plan". {fiyat} sunucuda güvenilir biçimde biliniyorsa parantez içinde; bilinmiyorsa parantez yerine "ücretli {plan}".
- {son gün} {saat}: mağazanın bildirdiği bitiş anından 24 saat öncesi, kullanıcının yerel saatiyle, saat başına aşağı yuvarlanır ("perşembe 14.00"). Saat ekinin ses uyumu doğru yazılır (14.00'e, 9.00'a).

## 2. Kurallar
1. **Açılabilen hikâye:** adı geçen hikâye yalnız kullanıcının o gün açabildiği hikâyeyse yazılır. Açamıyorsa o bildirim o gün gitmez (E6) ya da adsız yedek kullanılır (E1).
2. **"Son hatırlatmamız" sözü tutulur:** E10 ya da E14 giden kullanıcıya, uygulamayı yeniden açana kadar hiçbir tür gitmez. Tek istisna deneme hatırlatması (D1–D4). Bu sağlanamıyorsa E10 ve E14 kullanılmaz; rapora yaz, ekip yedek metin verir.
3. **Ad:** yer tutucuysa, rakam ya da "@" içeriyorsa ya da 10 harften uzunsa adsız başlık ve adsız gövde.
4. **E11 dönüşümlü gövde:** (a) "Çayını al {ad}, bugünün hikâyesi geldi: {Türkçe ad}." (b) "Bugünkü hikâye {n} dakikalık: {Türkçe ad}." (c) "{ad}, seçtiğin saat. Bugünkü hikâye: {Türkçe ad}." Aynı kullanıcıya üst üste aynı gövde gitmez; (a) haftada en çok iki kez ve yerel 07–22 arasında. Hangi gövdenin gittiği gönderim kaydına yazılır.
5. **Dokununca:** adı geçen hikâyenin kapak sayfası (PR #23'teki gibi); E4 quiz sekmesi, E5 kelime tekrarı, D1–D4 Profil'deki üyelik kartı.
6. Günde en çok bir bildirim, 09–23 arası ve öncelik sırası bugünkü gibi; D3–D4 deneme uyarısıyla aynı öncelikte.

## 3. Önce doğrula (koddan; biri tutmuyorsa o satırı uygulama, rapora yaz)
| Satır | Doğrulanacak |
|---|---|
| E3 | Kırılan seri bugün bir hikâye bitirince gerçekten geri geliyor mu; ücretsiz ve Premium kullanıcıda aynı mı? |
| E4 | {n} günün quizindeki gerçek soru sayısı mı? |
| E7, E9 | Adı geçen hikâye kullanıcının seviyesindeki başlangıç yolculuğunun ilk hikâyesi mi; seviyesi bilinmeyen kullanıcıda ne oluyor? |
| E8 | Uygulama hikâyeyi kaldığı yerden açıyor mu (kapak sayfası üzerinden dahil)? |
| E10 | 7. günden sonra hiç okumamış kullanıcıya bugün başka bir tür gidiyor mu? |
| E13 | "Son 7 günde eklenen, seviyeye uyan metin sayısı" hesaplanabiliyor mu? |
| D1–D4 | "Profil'den iptal" yolu iOS ve Android'de çalışıyor mu; mağaza bitiş anı kayıtta saatle var mı; {fiyat} sunucuda var mı? |

## 4. Ölçüm
Gönderim kaydında tür, `copy_v4` ve E11 için gövde harfi. Yayından iki hafta sonra tür başına dokunma oranı (bugün: toplam %2,3; seri hatırlatma %16,7; seri başlat %3,8; geri dön %0,5).

## 5. Rapor
`raporlar/2026-11-26_editor_bildirim_metinleri.md`: doğrulama cevapları, uygulanmayan satırlar ve nedeni, test sonucu, Mehmet'ten beklenen (birleştirme).
