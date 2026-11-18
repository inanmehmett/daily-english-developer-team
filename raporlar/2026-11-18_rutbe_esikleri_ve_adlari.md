# Kariyer yolculuğu: ilk rütbe ne zaman geliyor, rütbe adları

**Tarih:** 18 Kasım 2026, 18:37 · Tek geçiş; üyeler kurgusaldır. **İsteyen:** Mehmet ("İlk seviye çabuk kazanılsın, buna bak. İsimleri ekibe sun, incelesinler.")
**Kaynak:** sunucu kodu `DataAccess/Seed/LevelLadder.cs`, `Services/Common/GamificationConstants.cs` (18 Kas okundu). Müşteri XP dağılımı henüz yok; eşik önerisi editör verisiyle doğrulanacak.

## 1. Bugünkü durum (koddan)
**XP nasıl kazanılıyor:** okuma dakikası başına 10 XP; quizde doğru cevap başına 5 XP (5 soruluk quiz en çok 25); kelime kartı doğru başına 1; günlük tavan 300; 2. gün sürprizi +25.

**Merdiven (12 rütbe):**
| # | Rütbe | Eşik (XP) | Bir öncekinden uzaklık |
|---|---|---|---|
| 1 | Çaylak | 200 | 200 |
| 2 | Meraklı | 900 | 700 |
| 3 | Okur | 1.940 | 1.040 |
| 4 | Kelime Avcısı | 3.290 | 1.350 |
| 5 | Hikâye Avcısı | 5.050 | 1.760 |
| 6 | Kâşif | 7.330 | 2.280 |
| 7 | Kitap Kurdu | 10.300 | 2.970 |
| 8 | Aydın | 14.170 | 3.870 |
| 9 | Simyacı | 19.190 | 5.020 |
| 10 | Usta | 25.710 | 6.520 |
| 11 | Bilge | 34.200 | 8.490 |
| 12 | Efsane | 45.220 | 11.020 |

**Neden böyle:** İlk rütbe 14 Eylül'de 50 XP'ydi ve ilk oturumda geliyordu. 15 Eylül'de bilerek 200'e çekildi: ilk günün rozetleriyle (İlk Kitap, İlk Quiz) çakışmasın ve "Çaylak'a 60 XP kaldı" ertesi gün dönmek için sebep olsun diye. Yani ilk rütbe 2.–3. güne tasarlandı.

**Veri bu tasarımı doğrulamadı:** müşterilerin %64'ü en fazla bir gün görülüyor; 243 müşteriden yalnız 40'ı (%16) ilk rütbeye varmış. "Yarın dönersen rütbe" sözü, dönmeyen kullanıcıya hiçbir şey vermedi. Mehmet'in teşhisi doğru: çoğu kullanıcı kariyerde hiçbir şey kazanmadan gidiyor.

## 2. Öneri: ilk üç rütbe öne
Bir hikâye 2–5 dakika: 20–50 XP; quizle birlikte 45–75 XP.

| # | Rütbe | Bugün | Öneri | Ne zaman gelir (tahmin) |
|---|---|---|---|---|
| 1 | Çaylak | 200 | **20** | İlk hikâye biterken (ilk oturum) |
| 2 | Meraklı | 900 | **150** | 3.–4. hikâye: başlangıç yolculuğu biterken (2.–4. gün) |
| 3 | Okur | 1.940 | **500** | İlk hafta sonu |
| 4 | Kelime Avcısı | 3.290 | 1.200 | 2.–3. hafta |
| 5 | Hikâye Avcısı | 5.050 | 2.400 | |
| 6 | Kâşif | 7.330 | 4.200 | |
| 7 | Kitap Kurdu | 10.300 | 6.800 | |
| 8 | Aydın | 14.170 | 10.300 | |
| 9 | Simyacı | 19.190 | 15.000 | |
| 10 | Usta | 25.710 | 21.500 | |
| 11 | Bilge | 34.200 | 30.000 | |
| 12 | Efsane | 45.220 | 41.000 | |

- Hiçbir eşik yükselmiyor: **kimse rütbe kaybetmez**, bazı mevcut kullanıcılar yükselir (onlara tek, sakin bir bildirim; kutlama yağmuru yok).
- Üst rütbeler katalog kapasitesinin (yaklaşık 36.400 XP) içinde kalır; Efsane yine açık uç.
- **Kesinleşmeden önce (Nate):** editör müşterilerin ilk gün XP'sini ve bu eşiklerle kimin nereye çıkacağını hesaplar (`ortak/editor_gorevi_2026-11-18_xp_ekonomisi.md`). Eşik değişikliği sunucu kodu + canlı tablo eşitlemesidir: Mehmet onayıyla.

**15 Eylül'ün kaygısı (ilk gün kutlama kalabalığı) nasıl çözülür (Don, Dieter):** ilk hikâye bitişinde tek an olur. Rütbe, bitiş ekranının içinde gösterilir ("Çaylak oldun · Meraklı'ya 3 hikâye"), ayrı pencere açılmaz; "İlk Kitap" rozeti sessizce profile düşer. Ardından ana eylem yine "Sıradaki hikâye".

**İtirazlar:** Nassim: hızlı rütbenin dönüşü artıracağı kanıtlı değil; 15 Eylül'de de tersini düşünüp değiştirmiştik. Ölçü: ilk oturumda rütbe alanların ertesi gün dönüşü, 4 hafta. Paul: rütbe adı seviye iddiası taşımaz; "Okur oldun" A2 demek değildir (kod da böyle söylüyor).

## 3. Rütbe adları – ekip incelemesi
Kodun kuralı: tek metafor okuma; kapsam büyür (kelime → hikâye → kitap → derinlik → ustalık); rütbe emeği anlatır, dil seviyesini değil.

| # | Ad | Görüş | Öneri |
|---|---|---|---|
| 1 | Çaylak | Oyun dilinde tanıdık, sıcak ve biraz şakacı; büyüme payı bırakıyor. Paul: "çaylak" küçümseme gibi okunabilir, ama ilk hikâyede gelen ilk unvan için kabul edilebilir. | Kalsın |
| 2 | Meraklı | En iyi adlardan; kullanıcıyı doğru tarif ediyor. | Kalsın |
| 3 | Okur | Sade, hedefin kendisi. | Kalsın |
| 4 | Kelime Avcısı | Güçlü ve ürünün ana eylemine (kelimeye dokunma) bağlı. | Kalsın |
| 5 | Hikâye Avcısı | Arka arkaya iki "avcı": ayırt edilmiyor, ilerleme hissi vermiyor. | **Hikâye Tutkunu** |
| 6 | Kâşif | Uygun. | Kalsın |
| 7 | Kitap Kurdu | Herkesin bildiği deyim; çok uygun. | Kalsın |
| 8 | Aydın | Türkçede erkek adı, il adı ve "entelektüel" anlamı var; rütbe olarak belirsiz ve biraz siyasi çağrışımlı. | **Derin Okur** |
| 9 | Simyacı | Okuma metaforunun dışında görünse de okurların bildiği bir kitap adı; çağrışımı iyi. | Kalsın |
| 10 | Usta | Uygun. | Kalsın |
| 11 | Bilge | Uygun. | Kalsın |
| 12 | Efsane | Uygun; açık uçlu son basamak. | Kalsın |

- Kullanıcıların büyük çoğunluğu yalnız ilk üç adı görecek (Çaylak, Meraklı, Okur); üçü de sağlam.
- İki değişiklik önerisi (5 ve 8). Ad değişince rozet adları kendiliğinden güncellenir (kod notu); görseller değişmez.
- **Dieter:** kariyer sayfasında ad tek başına yazılsın ("Çaylak"), "Çaylak Okur" gibi ekli hâl 3. rütbeyle ("Okur") karışır.
- Ad değişikliği görünen metindir: Mehmet onaylarsa uygulanır.
