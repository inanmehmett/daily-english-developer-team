# Kariyer yolculuğu: bugünkü hâli, en iyi örnekler ve yol haritası

**Tarih:** 20 Kasım 2026 · Tek geçiş; üyeler kurgusaldır. **İsteyen:** Mehmet.
**İstek:** "Kullanıcılar burada gerçek bir ilerleme hissi yaşasın, uygulamaya dönsün, düzenli okuyarak İngilizce öğrensin. Nerede olduklarını, ne başardıklarını, nereye gittiklerini somut görsünler. Ekip bugünkü hâli incelesin, bu işi en iyi yapanlara baksın, yol haritası çıkarsın."
**Kapsam:** Bu rapor 1.0.4'e hiçbir şey eklemez; sonraki sürümlerin planıdır.

## 1. Bugünkü hâl
**Ekran** (`raporlar/ekran_2026-11-19/normal_ana_sayfa_kapak.jpg`, N18): aşağıdan yukarı kıvrılan bir yol; üstünde altıgen rütbe madalyaları (Çaylak, Meraklı, Okur, Kelime Avcısı…), hepsi kilitli; altta koyu bant: "Okuma Yolculuğun · 58 XP · 58 ort. XP/gün · ~3 gün → Çaylak".

**Kurallar** (sunucu kodu): 12 rütbe; ilk eşik 200 XP, ikincisi 900, sonuncusu 45.220. XP: okuma dakikası başına 10, quizde doğru başına 5. Rütbe adı dil seviyesi iddia etmez.

**Veri** (uygulamanın kendi kayıtları, 17–18 Kas):
| | |
|---|---|
| Sayfayı gören | 243 müşteriden 25 (%10); 18'i bir kez |
| Ana sayfadan gelen açılış | 0 |
| İlk rütbeye varan | 311 müşteriden 60 (%19); ikinciye 9; üçüncüye 2 |
| Sayfada dokunulan 19 düğümün | 14'ü kilitli olan |
| Sayfadan sonra okumaya geçiş | sıradan bir açılışla aynı |

**Teşhis (Don, Paul, Dieter):**
1. **Görünmüyor.** İlerleme, kimsenin gitmediği ayrı bir sayfada duruyor.
2. **Ölçü soyut.** "58 XP" kullanıcıya ne okuduğunu, ne öğrendiğini söylemiyor; quiz XP'yi şişiriyor.
3. **Nerede olduğunu söylemiyor.** Seviye (A2) sayfada yok; rütbe adı bir yeterliğe karşılık gelmiyor.
4. **Ne başardığını göstermiyor.** Okunan hikâye, okunan kelime, öğrenilen kelime, okuma günleri hiçbir yerde toplu durmuyor.
5. **Nereye gittiği uzak.** İlk hedef çoğu kullanıcının varamadığı yerde; sonrası haftalar uzakta.
6. **Sayfada yapacak bir şey yok.** Yol bir resim; dokununca bir şey başlamıyor.
7. **İyi olan:** "~3 gün → Çaylak" tahmini (insan diliyle hedef), yol metaforu ve rütbe görselleri. Bunlar korunur.

## 2. Bu işi iyi yapanlar
| Örnek | Ne yapıyor | Bizim için ders |
|---|---|---|
| **Duolingo – yol** | İlerleme haritası ayrı bir sayfa değil, uygulamanın ana ekranı: kullanıcı yolu görür, sıradaki halkaya dokunur, ders başlar. | İlerleme, gidilen bir yer değil, **içinden geçilen** yer olmalı. 1.0.4'teki "Senin Yolculuğun" sayfası bu yönde ilk adım. |
| **Duolingo Score** | 0–160 arası tek sayı; aralıklar CEFR'e bağlı (30–59 A2, 60–79 B1 başı…) ve her aralık "şunu yapabilirsin" diye anlatılıyor. Yeni kullanıcı ilk üniteyi bitirince açılıyor. Duolingo'nun gerekçesi: CEFR seviyesi çok geniş; kullanıcıya daha ince, her derste kıpırdayan bir ölçü gerek. | **Her okumada artan, gerçek bir şeye bağlı tek sayı.** Ve ilk ödül ilk adımın hemen ardından. |
| **LingQ** | Okuyarak öğrenme uygulaması; ana ölçüsü "bildiğin kelime sayısı". Günlük hedef ve seri bu sayıya bağlı. | Okuma uygulamasında doğal ölçü **kelime**: okunan ve öğrenilen. |
| **Xreading (kademeli okuma)** | Öğrenciye okuduğu kitap sayısını, **toplam okunan kelimeyi**, okuma hızını ve seviyesini gösteriyor; öğrenciler hedefleriyle gerçekleşeni karşılaştırıyor. Okuma öğretiminde yerleşik ölçü okunan kelime sayısı. | "Şu ana kadar 12.400 kelime okudun" dürüst, hep artan ve okumaya özgü bir sayı. |
| **Busuu – çalışma planı** | Kullanıcı gün ve süre seçer; uygulama hedefe **tahmini varış tarihi** verir, hatırlatma ve ilerleme bildirimi yollar. (Etkisine dair sayı yayımlamıyor.) | Bizde günlük dakika ve okuma saati zaten soruluyor; "bu hızla şu tarihte" demek için veri hazır. |

**Ortak nokta:** (1) ilerleme ana akışın içinde, (2) ölçü somut ve sık kıpırdıyor, (3) kullanıcının durduğu yer bir seviyeye bağlı, (4) sıradaki hedef yakın ve tarihli, (5) haritadan eylem başlıyor.

## 3. Ekip değerlendirmesi
- **Paul:** Okuyarak öğrenen biri için gerçek ilerleme dört şeydir: okuduğu hikâye, okuduğu kelime, öğrendiği kelime, düzenli okuduğu gün. XP bunların gölgesi. Sayfanın başına bu dördü gelmeli. Seviye atlamayı okunan hikâye sayısına bağlayıp söz veremeyiz; ama kodda seviye hazırlığı ve değerlendirme altyapısı var: kullanıcı yeterince okuyunca "B1 denemesine hazırsın" denir, denemeyi geçerse seviye yükselir. Söz yok, kanıt var. *(Düzeltme, 21 Kas: hazırlık sinyali ve geçiş sınavı Eylül'de koddan silinmiş; çalışan yalnız seviye ölçümü. Bkz. sondaki ek.)*
- **Don:** Sayfa üç soruya cevap vermeli, bu sırayla: **Neredeyim? Ne başardım? Sırada ne var?** Bugün yalnız üçüncüye, o da XP diliyle cevap veriyor.
- **Dieter:** Yol ve madalyalar kalır. Üstüne bir "Buradasın" kartı, yolun üstünde kullanıcının kendi işareti, kazanılan madalyada tarih ve o güne kadar okunanlar. Daha az süs, daha çok kanıt.
- **Sean:** Dönüş sebebi yakın hedeftir: "Meraklı'ya 2 hikâye". Haftalık özet ("bu hafta 5 hikâye, 1.240 kelime") hem bildirim hem paylaşım kartı olur; paylaşılan kart Instagram'dan yeni kullanıcı getirir.
- **Nate:** Bugün ölçemediklerimiz: kutlama gösterimi, sayfaya nereden girildiği (1.0.4'te geliyor). Okunan kelime sayısını sunucunun bugün tutup tutmadığını bilmiyoruz; editör bakmalı.
- **Kent:** Rütbe eşiklerini değiştirmek sunucu tablosu; okunan kelime sayacı yeni bir alan olabilir. Seviye denemesinin 176 sorusu okunmadan öne çıkarılamaz.
- **Nassim:** Bu sayfanın dönüşü artırdığına dair elimizde kanıt yok; hepsi iyi gerekçeli hipotez. 1.0.4 önce çıkar, "Senin Yolculuğun" sayfasının verisi gelir; sonra en ucuz parçadan başlanır. Tek seferde büyük yeniden yazım yok.
- **Steve:** İki "yolculuk" sayfası uzun vadede tek resmin iki ölçeği olmalı: yakın (bu yolculuğun hikâyeleri) ve uzak (bütün yol). Şimdilik iki sayfa, aralarında tek dokunuş.

## 4. Hedef resim
**Ad önerisi:** "İngilizce Yolculuğun" (Mehmet'in ifadesi; ne olduğunu söylüyor). Hikâye sayfası kendi yolculuğunun adını taşır ("Başlangıç · 2/4").

| Soru | Sayfada karşılığı |
|---|---|
| **Neredeyim?** | Üstte "Buradasın" kartı: seviye (A2) · rütbe (Çaylak) · yolun üstünde kullanıcının işareti |
| **Ne başardım?** | Dört sayı: okuduğun hikâye · okuduğun kelime · öğrendiğin kelime · okuduğun gün. Kazanılan her rütbede tarih ve o güne kadar okunanlar |
| **Sırada ne var?** | Yakın hedef insan diliyle ve tahminle: "Meraklı'ya 2 hikâye · bu hızla perşembe". Uzak hedef: seviye yolu A1 → A2 → B1 → B2 → C1; bu seviyede okudukların; hazır olunca seviye denemesi |
| **Ne yapayım?** | Sayfanın altında tek düğme: "Sıradaki hikâye" |

## 5. Yol haritası
| Aşama | Ne | Neden bu sırada | "Bitti" ölçütü |
|---|---|---|---|
| **0 · 1.0.4 (şimdi)** | Bitiş ekranında rütbe satırı; "Senin Yolculuğun" sayfası; sayfaya girişlerin ölçümü. Başka bir şey eklenmez | Yayın bekliyor | Mağazada |
| **1 · Görünür ve hızlı** (sonraki sürüm) | İlk üç rütbe öne (20 / 350 / üçüncü veriyle); ilk bitişte tek kutlama; rütbe kazanılınca sayfaya götüren kutlama; sayfada "Sıradaki hikâye" düğmesi; her yerde insan diliyle hedef | En ucuz parça; bugün %19 olan "ilk rütbeye varan"ı hemen değiştirir | İlk oturumda rütbe alan yeni müşteri ≥ %50; sayfayı gören ≥ %40 |
| **2 · Kanıt** | "Buradasın" kartı ve dört sayı; kazanılan rütbede tarih ve okunanlar; sayfanın adı; haftalık özet (pazar bildirimi + paylaşılabilir kart) | Gerçek ilerleme hissi buradan gelir; okunan kelime sayacı için editörün veri denetimi gerekir | Haftalık özet bildirimini açan oranı; 7. gün dönüşü (bugün %3) |
| **3 · Seviye yolu** | A1 → C1 istasyonları; bu seviyede okunanlar; hazır olunca seviye denemesi; geçince yeni seviyenin yolculukları ve belge | En güçlü "nereye gidiyorum" cevabı; ama 176 sorunun incelenmesi ve her seviyede yeterli içerik şart | Denemeye giren ve geçen sayısı; seviye atlayanın 30. gün dönüşü |
| **4 · Plan ve tarih** | Günlük dakika hedefinden tahmini varış ("bu hızla 14 Aralık'ta Okur"); ay sonu özeti | Veri birikince anlamlı | Tahmini gören kullanıcının haftalık okuma günü |

Her aşamadan sonra en az iki hafta ölçülür; ölçü kıpırdamıyorsa sonraki aşama başlamaz (yol haritası toplantısının kuralı).

## 6. Editörden istenecek veri (kod yok, 1.0.4'ten sonra)
1. Sunucu her okumada okunan kelime sayısını tutuyor mu; müşteri başına toplam okunan kelime hesaplanabiliyor mu?
2. Müşterilerin okuduğu hikâye, okuduğu kelime, defterde "öğrenildi" sayılan kelime ve okuma günü dağılımı.
3. Seviye hazırlığı ve değerlendirme altyapısının bugünkü durumu: ne çalışıyor, müşteriye ne açık.
4. Önerilen eşiklerin denemesi (`ortak/editor_gorevi_2026-11-18_xp_ekonomisi.md` madde 6'nın sonucu genel durum raporunda var: 20 XP'de ilk hikâyede 159/163 rütbe alır; ikinci rütbe için 300–350).

## İtirazlar
- **Nassim:** Rütbeyi 15 Eylül'de "ertesi gün dönsünler" diye geciktirmiştik, tutmadı; şimdi tersini yapıyoruz. İkisi de tahmin; bu kez ölçerek.
- **Paul:** Okunan kelime sayısı hızlı geçilen sayfaları da sayarsa sahte ilerleme olur; yalnız bitirilen hikâyelerin kelimeleri sayılmalı.
- **Sean:** Seviye denemesi ücretsiz mi Premium mu olacağı ayrıca konuşulmalı; güçlü bir satış anı olabilir.

## Kaynaklar
- [Duolingo Score](https://blog.duolingo.com/duolingo-score/)
- [Duolingo'da ilerleme nasıl ölçülür](https://blog.duolingo.com/how-to-measure-progress-on-duolingo/)
- [LingQ istatistikleri](https://lingq-support.groovehq.com/help/understanding-lingq-statistics)
- [Busuu çalışma planı](https://blog.busuu.com/new-feature-study-plan-achieve-language-learning-goals/)
- [Xreading ile kademeli okuma yönetimi (JALT)](https://jalt-publications.org/node/4184)

---

## Ek (21 Kasım 2026): veriyle netleşen plan
**Dayanak:** `raporlar/2026-11-20_ilerleme_verisi.md` (editör, 350 müşteri). Tek geçiş; üyeler kurgusaldır.

### Veri planın neresini değiştirdi
| Bulgu | Sonuç |
|---|---|
| Dört sayının dördü de bugün ve geriye dönük hesaplanabiliyor; yeni alan gerekmiyor | Aşama 2 sanıldığından ucuz |
| "Öğrenilen kelime" bugünkü tanımla (tekrar aralığı en az 7 gün) 350 müşteriden 2'sinde var | Sayfaya "öğrendiğin kelime" yazılmaz; yerine **"defterindeki kelime"** (127 kişide var). "Öğrenilen" sayısı sıfırdan büyük olunca ayrıca görünür (Paul: sıfır gösteren sayı ilerleme değil, eksik gösterir) |
| Okunan kelime dürüst: ortanca hız dakikada 46 kelime; şüpheli hızdaki bitirişler toplamın %1,7'si | "Okuduğun kelime" güvenle kullanılır |
| İlk hafta en az 3 gün okuyan 30 kişi: 4 hikâye, ~750 kelime, 15 kelime, 3 gün | Kart, kalan kullanıcıda ilk haftada anlamlı sayılar gösterir |
| 20 XP: ilk gün XP kazananların %70'i rütbe alır. 350 XP: düzenli okuyan 4. günde ikinci rütbede (11/17) | İlk iki eşik: **20 ve 350** |
| Üçüncü eşik için 17–21 kişilik veri | Üçüncü eşik şimdilik **1.000** (geçici); bir ay sonra yeniden bakılır. Dördüncü ve sonrası değişmez |
| Bitiş ekranındaki "Artık Çaylak!" satırı ile çıkıştaki tam ekran kutlama aynı şeyi iki kez söylüyor | **İlk rütbe bitiş ekranında kutlanır** (satır zenginleşir: rütbe görseli + "Yolunu gör ›"); tam ekran kutlama ilk rütbede çıkmaz, böylece "Sıradaki hikâye"nin önü kesilmez. İkinci rütbeden itibaren tam ekran kutlama kalır. İlk bitişte en çok bir rozet kutlaması (dar düzeltme) |
| Kutlamanın gösterildiği ölçülmüyor | Aşama 1'e iki olay: kutlama gösterildi, "Yolunu gör"e dokunuldu |
| Eşik inince 148 eski kullanıcı rütbeyi sessizce alır | Kabul; çoğu etkin değil, ayrı tören yapılmaz |
| Seviye hazırlığı ve geçiş sınavı Eylül'de koddan silinmiş; "Seviyeni belgele"yi hiçbir müşteri denememiş; seviyesi sonradan değişen 9 kişinin 4'ü aşağı inmiş; içerik dengesiz (A1 24, C1 20, C2 4 hikâye) | **Aşama 3 (seviye yolu) beklemeye alındı.** İncelemedeki "altyapı var" cümlesi yanlıştı; düzeltildi |
| Çalışan ve kullanılan şey: seviye ölçümü (97 tamamlanmış ölçüm) | "Neredeyim?" sorusunun cevabı ölçülen seviye olur; yanında "Yeniden ölç" bağlantısı. Yol resmi çizilmez, söz verilmez |
| 104 müşteri hiç seçim yapmadığı için varsayılan A1 görünüyor | Bu kullanıcılara seviye yerine "Seviyeni ölç" gösterilir |

### Netleşen yol haritası
| Sıra | Aşama | İçerik | Büyüklük |
|---|---|---|---|
| 1 | **Görünür ve hızlı** | Eşikler 20 / 350 / 1.000 (geçici); ilk rütbe bitiş ekranında; ilk bitişte tek rozet; kutlama olayları; kariyer sayfasında "Sıradaki hikâye" düğmesi | Küçük (eşikler tek dosya; kutlama sınırı 1–2 dosya). Eşik değişikliği sunucu yayınıdır: Mehmet onayı |
| 2 | **Kanıt** | "Buradasın" kartı: ölçülen seviye (yeniden ölç) · okuduğun hikâye · okuduğun kelime · defterindeki kelime · okuduğun gün; dördünü veren tek sunucu ucu; sayfanın adı; kazanılan rütbede tarih; haftalık özet | Orta |
| 3 | **Tarih** | "Bu hızla perşembe" (tahmin ucu hazır) | Küçük; düzenli okuyan sayısı artınca anlamlı |
| — | Seviye yolu | Beklemede: sorular okunmadan, içerik dengelenmeden ve yeniden yazım kararı verilmeden açılmaz | Büyük |

Hepsi 1.0.4'ten sonra; her aşamadan sonra en az iki hafta ölçüm.

### Yan bulgular (sonraki düzeltme sürümüne)
- Kariyer sayfasındaki Premium kartının düğmesi çift tanım yüzünden "İncele" yerine "Bütün yolculukları aç" yazıyor.
- Okuma süresi tutarsız: 137 kelimelik hikâye "3 dk", 254 kelimelik "2 dk" (veri; Paul bakar).
- "A1 öncesi" değeri sıralamada C2'nin üstüne düşüyor; seviye gösteren her yerde sıra doğru kurulmalı.
