# Toplantı: ilerleme hissi – kariyer yolculuğu ve okuma yolculuğu birlikte

**Tarih:** 18 Kasım 2026, 17:40 · Tek geçiş; üyeler kurgusaldır. **Çağıran:** Mehmet.
**Bu toplantı, 15:55 toplantısının "tek sayfa" kararının ve 15:58 ekinin yerine geçer.** Yön Mehmet'ten geldi; ekip nasıl yapılacağını çalıştı.

## Mehmet'in yönü
1. Kariyer yolculuğu **kalkmıyor.** Okuma yolculuğu **ekleniyor**, görsel olarak güzel bir ekranla. İkisi de etkin kullanılacak.
2. Kariyer yolculuğu ilerlemeye teşvik etmeli; **ilk rütbeler hızlı kazanılmalı.**
3. Kullanıcıya seçim yaptırma: sıradaki neyse onu okusun, geçsin. "Başka yolculuk seç" yok.
4. Sayfayı ana sayfaya yığmadan göstermenin yolu bulunmalı: bildirim, uygulama içi bildirim, okumadan sonra "bak buradasın, şu kadar kazandın".
5. Amaç: geri dönmek için sebep. İlerleme hissi yoksa gelmek için sebep de yok.

## Masadaki veri
- Rütbe eşikleri sunucuda (`LevelSystems`); koddaki notlara göre **Çaylak 50 XP** (karşılama rütbesi), **Meraklı 900 XP.** Bir hikâye bitişinde ekranda "+5 XP" görünüyor; taslaktaki örnekte iki hikâye sonrası 25 XP.
- Yani yeni kullanıcı ilk oturumunu **rütbesiz** bitiriyor; ikinci rütbe haftalar uzakta. 243 müşteriden 40'ı ilk rütbeyi geçmiş.
- Sayfayı %10 görmüş; açılışların yarısı rütbe kutlamasından. Kutlama nadir olduğu için sayfa da nadir görülüyor. Kutlamanın kendisi kaydedilmiyor.
- Kesin XP ekonomisi (hangi eylem kaç XP, eşikler, kim kaç günde hangi rütbeye varmış) bilinmiyor → editörden istenecek.

## Tartışma
- **Steve:** Mehmet'in ayrımı net bir cümleye iner ve o zaman iki sayfa çakışmaz: **okuma yolculuğu "bugün ne okuyacağım", kariyer "ne kadar yol aldım".** Biri yakın hedef, biri uzun yol.
- **Paul:** Buna katılırım, çünkü kariyerin hikâye yolunun ölçemediği bir şeyi ölçme şansı var: **bütün emek.** Hikâye, quiz, kelime tekrarı hepsi XP veriyor. Kelime tekrarı yapan da ilerlediğini görmeli. Rütbenin anlamı buradan gelir.
- **Don:** Rütbe ancak iki şartla anlam taşır: ulaşılabilir olması ve bir sonraki adımı söylemesi. "900 XP" bir şey söylemez; "**Meraklı'ya 2 hikâye kaldı**" söyler. Kodda bunun temeli var (sonraki rütbeye kalan, "bugün 1 metin okursan" cümlesi).
- **Sean:** İlk rütbe ilk oturumda gelmeli. İnsan ilk ödülü ne kadar erken alırsa ikinciye o kadar inanır (hedefe yaklaşma etkisi). Öneri: 1. hikâye bitince Çaylak; başlangıç yolculuğu bitince (3.–4. gün) ikinci rütbe; ilk hafta sonunda üçüncü. Sonra aralık açılır.
- **Nate:** Eşikleri sayıyla söylemeden önce XP ekonomisini görmem lazım. Yanlış ayarlarsak ya herkes ilk gün üç rütbe atlar ya da yine kimse varamaz. Kutlama gösterimi de mutlaka kaydedilmeli.
- **Kent:** Eşikler sunucudaki tabloda; değiştirmek canlıya yazma demek (Mehmet onayı, yedek). Eşik düşerse kimse rütbe kaybetmez, bazıları yükselir; yükselenlere toplu kutlama patlamamalı.
- **Dieter (sayfa nasıl görünür – Mehmet'in 4. maddesi):** Ana sayfaya yeni bir şey koymayalım. İlerleme, **kazanıldığı anda** gösterilir: bitiş ekranında "+XP" sayısı bir çizgiye dönüşür, çizgi sonraki rütbeye doğru dolar. Rütbe atlanınca kutlama, oradan kariyer sayfası. Ana sayfada zaten kişi kartındaki halka var; ona dokunmak kariyeri açar, yeter.
- **Don:** Sıra önemli. Bitiş ekranı: (1) "+XP, Meraklı'ya şu kadar kaldı" çizgisi kısa bir an, (2) sıradaki hikâye kartı ve düğme. İlerleme gösterisi ana eylemi geciktirmez, 1–2 saniyelik bir geçiştir.
- **Tony:** Bildirimde de aynı dil: "Meraklı rütbesine 1 hikâye kaldı." Kullanıcıya ne yapacağını söyleyen bildirim şikâyet getirmez.
- **Nassim:** İki itiraz. (1) Rütbeyi hızlandırmak ilk hafta için iyi; ama rütbe aralığı açılınca his yine söner. Uzun vadede dönüş sebebi hikâyenin kendisi ve kelime tekrarı olmalı; rütbe yardımcı. (2) Bugün ikinci kez yön değişti; bundan sonrası için tek kural: **Mehmet yönü verir, ekip yapılışı çalışır, taslak görülmeden kod yok.**
- **Paul (seçim konusu):** Mehmet haklı; seçenek sunmak kararsızlık üretir. "Başka yolculuk seç" kalkar. Yolculuk bitince sıradaki hikâye, yeni yolculuğun ilk hikâyesidir; kullanıcı için değişen bir şey yoktur, yalnız "Sıradaki hikâye" der.

## Kararlar
**A. İki sayfa, iki soru**
| Sayfa | Cevapladığı soru | Ne gösterir | Ad |
|---|---|---|---|
| Okuma yolculuğu (yeni, görsel) | Bugün ne okuyacağım? | Hikâye kapaklarından yol; okunan, sıradaki, kilitli | **Senin Yolculuğun** |
| Kariyer yolculuğu (var olan) | Ne kadar yol aldım? | Rütbeler, XP, sonraki rütbeye kalan | **Okur Kariyerin** (bugün başlığı "Okuma Yolculuğun"; iki sayfa aynı adı taşıyamaz) |

**B. Kariyeri canlandırmak**
1. **İlk rütbeler hızlı:** hedef eğri: 1. hikâye bitince ilk rütbe; başlangıç yolculuğu bitince ikinci; ilk hafta sonunda üçüncü. Kesin eşikler XP verisi gelince (editör görevi). Eşik değişikliği canlıya yazmadır: Mehmet onayı ve yedekle.
2. **İnsan diliyle hedef:** her yerde "X rütbesine N hikâye kaldı"; ham XP ikincil.
3. **Rütbe, bütün emeği sayar:** hikâye, quiz, kelime tekrarı.

**C. İlerleme nerede görünür (ana sayfaya yeni kart yok)**
1. **Bitiş ekranı:** "+XP" → sonraki rütbeye dolan çizgi ("Meraklı'ya 2 hikâye") → sıradaki hikâye. Kısa geçiş; ana eylemi geciktirmez.
2. **Rütbe kutlaması:** rütbe atlanınca kutlama → "Kariyerini gör". Kutlama gösterimi ve dokunuşu kaydedilir.
3. **Kişi kartındaki halka** (ana sayfada zaten var) kariyeri açar. "Senin yolculuğun" kartındaki ilerleme çizgisi okuma yolculuğu sayfasını açar.
4. **Bildirim:** sonraki rütbeye bir hikâye kaldığında, günün görev çağrısı bu cümleyle gider ("Meraklı rütbesine 1 hikâye kaldı"). Ayrı bildirim türü eklenmez; günlük sınır aşılmaz.
5. **Haftalık özet** (pazar, uygulama içi kart): bu hafta okunan hikâye, kelime, kazanılan XP, rütbeye kalan. Sürüm 3 adayı.

**D. Seçim yok**
- "Başka yolculuk seç" kaldırıldı. Yolculuk bitince sıradaki kendiliğinden gelir; bitiş ekranı her zaman yalnız "Sıradaki hikâye" der. Başlangıç bitişindeki ilerleme kartı ve teklif kalır.
- Ücretsiz kullanıcı kilide varınca: "Premium'la devam et" / "Ücretsiz devam et: {ekibin seçtiği tek hikâye}". Liste gösterilmez.

**E. Sıra**
1. Sürüm 1: değişmez (kariyer eski sayfasıyla, yeni okuma yolculuğu sayfası yok).
2. Balon sürümü.
3. **İlerleme sürümü:** B ve C'nin 1–4'ü + "Senin Yolculuğun" sayfası. Önce XP verisi ve iki taslak (bitiş ekranındaki ilerleme çizgisi; okuma yolculuğu sayfası); Mehmet görür, sonra kod.

**Ölçü:** ilk oturumda rütbe kazanan yeni müşteri oranı; rütbe kutlamasından sonra ertesi gün dönüş; kariyer ve yolculuk sayfasını gören oran (bugün %10); hepsinin üstünde 48 saatte "döndü ya da ödedi".

## İtirazlar
- **Nassim:** Rütbe hızlandırmanın dönüşü artıracağı kanıtlı değil; ilerleme sürümünden sonra 4 hafta ölçülür, kıpırdamazsa rütbeye daha fazla yatırım yapılmaz.
- **Kent:** Eşik değişince yükselen eski kullanıcılara tek, sakin bir bildirim; kutlama yağmuru yok.
- **Paul:** Hızlı rütbe sahte başarı hissi vermemeli; rütbe adı seviye iddiası taşımaz (A2 demek değildir).
