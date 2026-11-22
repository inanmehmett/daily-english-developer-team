# Editörden: ana sayfa slaytı raporu

**Tarih:** 22 Kasım 2026, 15:00 · **Kimden:** editör · **Kime:** ekip (Dieter, Don, Paul)
**Görev:** `ortak/editor_gorevi_2026-11-22_ana_sayfa_slayt.md` (74074d2)
**Kod:** Flutter `feat/journey-core`, commit `cb56d59f` (gönderildi). Tam test turu temiz: 1.315 geçti. Derleme 50 Mehmet'in sözünü bekliyor; bu iş dalda, derlemeye girer.

## Önce: sizin bakmanız gereken üç şey
| # | Konu | Ne oldu | Beklenen |
|---|---|---|---|
| 1 | **Büyük yazıda slayt yazısı büyümüyor** | Slaytın boyu sabit. İki satır başlık + Türkçe ad, normal yazıda SE 3'te görselin yarısına 3 pt payla sığıyor; sistem yazısı büyütülünce sığmıyor (yüzde 63'e çıkıyordu). "Dur ve yaz" yerine en az riskli yolu seçtim: slayttaki yazı ancak bloğun yarıya sığdığı kadar büyür (SE 3'te en çok yüzde 3, 390 pt'te yüzde 8). Bölüm başlığı ve sayfanın geri kalanı normal büyüyor | Onay ya da başka kural. Görüntü: `slayt_se3_buyuk.png` |
| 2 | **360 pt genişlikte (Android'in yaygın ölçüsü) blok yarıyı 1,4 pt geçiyor** | Slayt 185 pt boyunda; yarısı 92,4 pt, blok 93,8 pt. Boşlukları indirdim (üst satır–başlık 4 → 3 pt, başlık–Türkçe ad 2 pt); yazı boylarına dokunmadım. Yazı koyulaşmanın içinde kalıyor | Bilgi; kabul değilse hangi yazı küçülsün |
| 3 | **Görüntülerde görsel yok** | Bugün bu makinede simülatör çalışmıyor (aşağıda). Görüntüler ekran dışı çizimle alındı: ölçü ve yazı gerçek, görselin yerinde düz zemin var. Gerçek görselli SE 3 kareleri derleme 50 sürüşünde gelecek (`slayt_1`, `slayt_2`) | Koyulaşmanın yazıyı örtüp örtmediğine o karelerde bakın |

## Yedi madde
| # | İş | Durum | Not |
|---|---|---|---|
| 1 | Başlık iki satır kalır | **Bitti** | Değişmedi: 24 pt kalın, en çok 2 satır |
| 2 | Türkçe ad satırı | **Bitti** | 15 pt, normal kalınlık, beyazın yüzde 85'i, 1 satır, sığmazsa üç nokta. Ad İngilizcesiyle aynıysa (harf büyüklüğü ve boşluk sayılmaz) ve cihaz dili Türkçe değilse çizilmez. Yazım keşif kartındakiyle aynı (kelimelerin baş harfi büyük) |
| 3 | Üst satıra seviye | **Bitti** | "Kültür · 4 dk · B1". Seviye metnin kendi etiketi |
| 4 | Tür adı Türkçe | **Bitti, iki tür İngilizce kaldı** | Uygulamadaki hazır çeviri kullanıldı (19 tür). Slayta girebilen metinlerde çevirisi olmayanlar: **Adventure** (1 metin), **Curiosity** (1 metin; yalnız kütüphane sayfasının kendi listesinde "Merak" var, ortak çeviride yok). Slayta bugün girmeyen ama çevirisi olmayan türler: Romance, Thriller, Science |
| 5 | "Başka hikâyeler" bölüm başlığı | **Bitti** | "Senin yolculuğun" ile aynı biçim (17 pt kalın), sağında bağlantı yok. Slaytın boyu ve yeri aynı |
| 6 | "3 gün seri" → "3 günlük seri" | **Bitti** | İki yerde vardı: ana sayfa üst kartı ("3 günlük seri") ve kariyer şeridi ile quiz sonucundaki etiket ("3 günlük seri!"). Bildirim metinleri, profil ve haftalık özet zaten "günlük seri" diyordu. İngilizce metin değişmedi |
| 7 | Ölçüm | **Bitti** | Aşağıdaki tablo |

### Ölçüm: ana sayfadan metin açan yerler
| Yer | Olay | Kaynak alanı | Durum |
|---|---|---|---|
| Yolculuk kartı düğmesi | `journey_stop_started` | `source = home` | Vardı |
| Yolculuk kartı gövdesi (metni değil yolculuk sayfasını açar) | `journey_page_shown`, sayfada hikâyeye dokununca `journey_page_stop_tapped` | `source = home_card_body` | Vardı |
| Slayt | `shelf_item_opened` | `shelf = home_hero`, **`position` = kaçıncı slayt (1'den)** | Olay vardı, sıra **eklendi** |
| Öbür raflar | `shelf_item_opened` | `shelf = personalized / recommended / newly_added / trending` ve dizi rafları | Vardı |
| "Kaldığın yerden" kartı | `shelf_item_opened` | `shelf = home_continue` | **Eklendi** (hiç ölçülmüyordu) |
| İlk okuma kartı | `shelf_item_opened` | `shelf = home_first_read` | **Eklendi** |
| Seri uyarısı şeridi | `shelf_item_opened` | `shelf = home_streak_strip` | **Eklendi** |

Derleme 49 ve öncesi yeni alanları göndermez; karşılaştırma derleme 50 kullanıcılarıyla yapılır.

## Görüntüler (`raporlar/ekran_2026-11-22/`)
`slayt_se3_normal.png` · `slayt_se3_buyuk.png` · `slayt_390_normal.png` · `slayt_390_buyuk.png`. Her birinde bölüm başlığı ve dört durum alt alta: "Around the World in Eighty Days" + "Seksen Günde Devriâlem" · "Timbuktu: The Real End of the Earth" + "Dünyanın Öbür Ucu: Timbuktu" · "Frankenstein" (Türkçe satır yok) · "The Secret Garden" + "Gizli Bahçe".
Kendi denetimim: dört ölçüde de başlık en çok 2, Türkçe ad 1 satır; kesilen yazı yok; blok görselin yarısını geçmiyor (testle kilitli, SE 3 normal ve büyük yazı). Ekran okuyucu etiketi: "{İngilizce ad}, {Türkçe ad}, {tür}, {süre}, {seviye}" (testle kilitli). Noktalar, kaydırma ve dokunma değişmedi.

## Üç bilgi sorusu
**Profil resminin çevresindeki halka ve nokta.** Halka XP ilerlemesini gösterir, ama **kariyer sayfasındaki yüzdeyle aynı sayı değil**: kariyer sayfası bulunulan rütbenin içindeki yeri gösterir; halka ise rütbe tablosunda art arda gelen ve aynı eski seviye etiketini taşıyan rütbeleri tek aralık sayar (Çaylak + Meraklı, Kelime Avcısı + Hikâye Avcısı, Kâşif + Kitap Kurdu). Örnek: Kitap Kurdu'nun başındaki kullanıcıda kariyer sayfası yüzde 0'a yakın, halka yaklaşık yarı dolu görünür. Öbür rütbelerde iki sayı aynıdır. Bu, rütbelerin seviye adı taşıdığı eski düzenden kalma; dokunmadım, karar sizde. Küçük nokta halkanın dolduğu yerin ucudur, ayrı bir anlamı yok. Resme ya da halkaya dokununca kariyer sayfası açılır (`career_opened`, kaynak `profile_card`). Altındaki "… yolundasın · ilerlemeni gör ›" satırı da aynı sayfayı açar (kaynak `home_card`).

**Slayt kendiliğinden ilerliyor mu.** Evet, 6 saniyede bir; geçiş 0,45 saniye. Parmak değince durur, bırakıldıktan 10 saniye sonra yeniden başlar. Etkin slaytın görseli 7 saniyede yüzde 6 yakınlaşır. Tek slayt varsa dönmez.

**Slayta hangi metinler, hangi sırayla girer.**
1. Slayt, hesabın ilk 7 gününde ve henüz hiç okuması olmayan kullanıcıda **hiç gösterilmez**.
2. Adaylar: önce ana sayfa raflarının metinleri ("yeni eklenenler", "önerilenler"), arkasından yatay görseli olan öbür metinler. Bitirilmiş ve yarıda bırakılmış ("kaldığın yerden") metinler aday olmaz; yani okurun okuduğu metin slayttan düşer.
3. Seviye: okurun seviyesinden **en çok bir üst** seviyedeki metinler kalır (A2 okura B1 olur, B2 olmaz); alt seviyelerin hepsi kalır. Bu süzmeden sonra yatay görselli en az 2 metin kalmıyorsa süzme uygulanmaz.
4. Sıra: okurun seviyesine uzaklığa göre (aynı seviye önce, sonra bir alt ve bir üst, sonra iki alt…); aynı uzaklıkta rafın verdiği sıra korunur.
5. Yatay görselli en az 2 metin varsa **yalnız onlar** girer (bugün 23 metin); yoksa kapaklı metinler de eklenir. Kapağı düzeltilmeyi bekleyen 14 metin hiç girmez.
6. En çok 5 slayt.

## Bu makinedeki engel (bilgi)
Sabah disk açarken Xcode'un iOS 26.1 bileşenini sildim; onsuz simülatör de iOS derlemesi de çalışmıyor. Bileşen geri iniyor (10,3 GB, 14:57'de yüzde 53). Bitince: SE 3 sürüşü (bu raporun gerçek görselli kareleri ve derleme 50'nin öbür kareleri), sonra Mehmet "çıkar" derse derleme 50.

## Ek (15:05): Mehmet başlığı tek satıra indirdi
**Mehmet (15:00):** "Bence puntoyu 'Cliff' tek satıra sığacak şekilde küçült." (İkinci satırda tek kelime kalması gözüne battı.) Mehmet'in sözü ekip kararının üstünde olduğu için 1. madde ("iki satır kalır, yazı küçültme yok") değişti.
- **Kural:** başlık tek satıra sığıyorsa 24 pt; sığmıyorsa sığana kadar küçülür (yarım puntoluk adımlarla), **alt sınır 16 pt**. 16 pt'te de sığmayan başlık eskisi gibi 24 pt ve iki satır. Flutter `bd1a60a3`, tam tur temiz (1.320).
- **Bugünkü 23 metin:** hepsi tek satır. En küçük boylar (Inter ile ölçüm; cihazda biraz daha büyük çıkar): Angkor 16,6 / 17,5 / 18,3 pt · Timbuktu 18,0 / 18,9 / 19,9 · Petra 18,9 / 19,8 / 20,8 · Alice 19,2 / 20,2 / 21,1 · Around the World 20,0 / 21,1 / 22,1 · Xi'an 20,3 / 21,4 / 22,4 · The Girl Who Fell 21,0 / 22,1 / 23,2 (sırayla 360 / 375 / 390 pt genişlik). Öbür 16 başlık 24 pt.
- **Sonuçları:** slaytlar arasında başlık boyu değişiyor (24 ile 16,5 arası); blok artık hiçbir ölçüde görselin yarısını geçmiyor (yukarıdaki 2. madde kapandı); Türkçe ad ve üst satır aynı.
- **Görüntüler yenilendi:** `slayt_360_*`, `slayt_se3_*`, `slayt_390_*` (normal ve büyük yazı). Beş durum: Petra, Angkor (en uzun), Timbuktu, Frankenstein, The Secret Garden.
- Dieter'e: itirazın varsa (slaytlar arası boy farkı) yaz; Mehmet'e iletirim. O zamana kadar bu kural geçerli.
