# Editör görevi: onaylı ad değişiklikleri (15 metin)

**Veren:** ekip (Tomris Uyum, Paul Ulus) · **Onay:** Mehmet, 26 Kas 2026 00:34 ("Hepsi onay"). Adların içeriği onaylı; **canlıya yazma adımı yine Mehmet'in "yap"ıyla.**
**Dayanak:** `raporlar/2026-11-25_ad_degisiklikleri_onay_listesi.md`, `raporlar/2026-11-25_ad_ve_aciklama_analizi.md`.

## Değişecek adlar
"(değişmiyor)" yazan hücreye dokunma.
| Kimlik | İngilizce ad (`Title`): önce | sonra | Türkçe ad (`SubtitleTR`): önce | sonra |
|---|---|---|---|---|
| 1059 | The Girl Who Fell From the Sky | The Girl Who Fell into the Amazon | Gökten Düşen Kız | Gökten Amazon'a Düşen Kız |
| 1023 | The Island Where Rabbits Won | Rabbit Island: Missing from the Map | Haritadan Silinen Ada | Haritadan Silinen Tavşan Adası |
| 1016 | The Night the Sky Fell | The Morning the Sky Fell on Siberia | Gökyüzünün Düştüğü Gece | Gökyüzünün Düştüğü Sabah |
| 1017 | The Sound Heard Around the World | Krakatoa: The Sound Heard Around the World | Dünyanın Duyduğu Ses | (değişmiyor) |
| 1020 | The Man Who Said No | The Man Who Would Not Sign | Hayır Diyen Adam | Üçüncü İmzayı Vermeyen Adam |
| 1060 | The Most Successful Failure | Shackleton: The Most Successful Failure | En Başarılı Başarısızlık | (değişmiyor) |
| 1061 | The Woman They Hired to Sew | The Seamstress of Wrangel Island | Dikiş İçin Tutulan Kadın | Buz Adasındaki Terzi |
| 1055 | Forty-One Days by the Sun | Forty-One Days After the Hurricane | Güneşle Kırk Bir Gün | Kasırgadan Sonra Kırk Bir Gün |
| 1082 | The Lamp Nobody Lit | The Moon's Borrowed Light | Kimsenin Yakmadığı Lamba | Ay Işığı |
| 1064 | The Fish That Needs No Sauce | When Sushi Was Street Food | Sos İstemeyen Balık | Suşinin Sokak Günleri |
| 1045 | Baba Yaga | (değişmiyor) | Tavuk Bacaklı Kulübe | Baba Yaga: Tavuk Bacaklı Kulübe |
| 1053 | Urashima Tarō | (değişmiyor) | Açılmaması Gereken Kutu | Urashima Tarō ve Yasak Kutu |
| 1063 | The Country That Eats Breakfast Twice | (değişmiyor) | İspanya'nın Kahvaltı Kültürü | Günde İki Kahvaltı Yapan Ülke |
| 148 | Why Italians Love Talking | (değişmiyor) | İtalyanların Konuşma Aşkı | İtalyanlar Neden Çok Konuşur? |
| 1066 | The Night India Turns On Its Lights | (değişmiyor) | Hindistan'ın Işıl Işıl Gecesi | Uzaydan Görülen Gece |

## Önce doğrula (salt okuma; cevapları rapora yaz, bir şey çıkarsa yazmadan önce dur)
1. **1016:** metinde geceyle ilgili bir bölüm var mı (ad eskiden "Night" diyordu; açıklama ve ilk cümle "morning")? Yeni ad "The Morning the Sky Fell on Siberia / Gökyüzünün Düştüğü Sabah" metinle çelişiyor mu?
2. **1020:** "Üçüncü İmzayı Vermeyen Adam / The Man Who Would Not Sign" metinle uyuşuyor mu (üç onay gerekiyordu, biri vermedi)? Metinde silahın nükleer olduğu açıkça yazıyor mu?
3. **1059:** metin düşülen yeri Amazon (yağmur ormanı) diye anıyor mu?
4. **1061:** metinde kadın terzi olarak alınıyor ve ada buzla kaplı diye anlatılıyor mu ("Buz Adasındaki Terzi")?
5. **1055:** "Kasırgadan Sonra Kırk Bir Gün": süre kasırgadan sonra mı sayılıyor?
6. Bu 15 metnin eski adı başka nerede geçiyor: İngilizce alt ad (`SubtitleEN`), merak cümleleri (başka metinlerin `NextHook`'u dahil), bildirim metinleri, yolculuk tanımları, mağaza görselleri ya da açıklaması? Liste çıkar; adla çelişen her yeri öneriyle yaz.
7. Ayrı soru (bu işin parçası değil, yalnız cevap): Room 214'ün 7. bölümünün Türkçe adı "Kayıkhanedeki Kardeş". Önceki altı bölümde kardeşin nerede olduğu okurdan saklanıyor mu?

## Uygula (Mehmet "yap" deyince)
- Yalnız görünen ad alanları değişir (`Title`, `SubtitleTR`). **Adres (`slug`) değişmez;** paylaşılmış bağlantılar ve ilerleme kayıtları bozulmasın.
- İngilizce alt ad yeni adla aynı şeyi söylüyorsa (1059, 1016, 1060 olası) dokunma; öneriyle raporla, Tomris karar verir.
- Yazmadan önce bu 15 satırın yedeği; SQL dosyası repoda (`MigrationScripts`), geri alma betiğiyle birlikte.
- Yazdıktan sonra canlıda 15 satırı okuyarak doğrula; uygulamada önbellek varsa ne zaman yenileneceğini yaz.
- Uygulama güncellemesi gerekmiyor olmalı (adlar sunucudan geliyor); gerekiyorsa söyle.

## Rapor
`raporlar/2026-11-26_editor_ad_degisiklikleri.md`: doğrulama cevapları, eski adın geçtiği yerler, yazılan satırlar, yapılamayanlar.
