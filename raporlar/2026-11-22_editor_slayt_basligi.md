# Editörden: ana sayfa slaytında başlık (Dieter ve Don'a)

**Tarih:** 22 Kasım 2026, 14:45 · **Kimden:** editör · **Kime:** Dieter (ekran), Don (akış)
**Mehmet (14:30):** "Bu ekranda slayt içindeki kitapların ismi tek paragrafa sığmıyor. Normal mi? Bir de Türkçe isim de yazmalı mı? UI ve UX sorumluları değerlendirsin, incelesin."
**Görüntü:** `raporlar/ekran_2026-11-22/ana_sayfa_slayt_mehmet.png` (Mehmet'in telefonu; "Petra: The City Carved from a Cliff" iki satır).

## Sizden beklenen karar
1. İki satıra inen başlık kalsın mı, tek satıra mı insin (nasıl)?
2. Slaytta Türkçe ad görünsün mü; görünecekse nerede, hangi durumda?

## Bugün ne oluyor (koddan)
- Dosya: `lib/features/home/presentation/widgets/home_hero_carousel.dart`.
- Başlık 24 pt, kalın, **en çok 2 satır**, sığmazsa üç nokta. Yani iki satır tasarımın izin verdiği durum; hata değil. Üç satıra hiç çıkmıyor.
- Başlığın üstünde tek satır "tür · süre" var (görüntüde "Culture · 4 dk").
- Slaytta **Türkçe ad yok.** Veri var: her metnin `SubtitleTR` alanı dolu (etkin 287 metnin 287'si). Keşif kartları bu alanı cihaz diline göre başlığın altında tek satır gösteriyor (Ağustos kararı: ana başlık her zaman İngilizce, altında Türkçe alt başlık).
- Slayta yalnız yatay görseli olan metinler giriyor: bugün **23 metin**, okurun seviyesine yakın olanlar önde, en çok birkaç slayt.

## Ölçüm (23 slayt metni, canlı veri)
Yazı genişliği Inter ile ölçüldü; cihazdaki sistem yazısı biraz daha dar, sayılar bir iki metin oynayabilir.

| Ekran | İngilizce başlık tek satır | iki satır | kesilen | Türkçe ad tek satır | iki satır |
|---|---|---|---|---|---|
| SE 3 (375 pt) | 15 | 8 | 0 | 22 | 1 |
| iPhone 13–16 (390–393 pt) | 16 | 7 | 0 | 22 | 1 |
| Pro Max (430–440 pt) | 19 | 4 | 0 | 23 | 0 |

İki satıra inen 7 başlık (390 pt): Angkor: The City the Jungle Took Back · Petra: The City Carved from a Cliff · Timbuktu: The Real End of the Earth · Xi'an: The Army Under the Field · Alice's Adventures in Wonderland · The Girl Who Fell From the Sky · Around the World in Eighty Days.
Türkçe adları: Ormanın Yuttuğu Şehir · Gül Rengi Şehir: Petra · Dünyanın Öbür Ucu: Timbuktu (bu da iki satır) · Tarlanın Altındaki Ordu · Alice Harikalar Diyarında · Gökten Düşen Kız · Seksen Günde Devriâlem.

Tam liste (İngilizce satır sayısı | Türkçe satır sayısı, 390 pt):
The Light in 9B 1|1 (9B'deki Işık) · The Village That Whistles 1|1 (Islıkla Konuşan Köy) · The Tell-Tale Heart 1|1 (Gammaz Yürek) · Frankenstein 1|1 · Jane Eyre 1|1 · Pride and Prejudice 1|1 (Gurur ve Önyargı) · The Time Machine 1|1 (Zaman Makinesi) · Baba Yaga 1|1 (Tavuk Bacaklı Kulübe) · Treasure Island 1|1 (Define Adası) · Peter Pan 1|1 · The Wonderful Wizard of Oz 1|1 (Oz Büyücüsü) · The Secret Garden 1|1 (Gizli Bahçe) · A Christmas Carol 1|1 (Bir Noel Şarkısı) · The Jungle Book 1|1 (Orman Kitabı) · The Great Gatsby 1|1 (Muhteşem Gatsby) · Dracula 1|1 (Drakula).

## Seçenekler (karar sizin; maliyet benim tahminim)
| # | Seçenek | Ne değişir | Dikkat | İş |
|---|---|---|---|---|
| A | Bugünkü gibi kalsın | Hiçbir şey | 23 metnin 7'si iki satır; kesilen yok | 0 |
| B | Başlık tek satır, sığmazsa yazı küçülür | Uzun başlık 24 → yaklaşık 19 pt | Slaytlar arasında yazı boyu değişir | Yarım gün |
| C | Başlık tek satır, sığmazsa üç nokta | "Petra: The City Carved fr…" | 7 başlık kesik görünür | 1 saat |
| D | İngilizce başlık + altında tek satır Türkçe ad | Keşif kartıyla aynı dil | İngilizce iki satırsa toplam üç satır yazı; görselin daha çoğu örtülür. Türkçe ad satırı için başlık tek satıra indirilebilir (keşif kartı böyle yapıyor) | Yarım gün |
| E | Üstteki "tür · süre" satırının yerine Türkçe ad | Satır sayısı artmaz | Süre bilgisi slayttan kalkar | 2 saat |

Bilgi: Türkçe adın çoğu çeviri değil, merak cümlesi ("Ormanın Yuttuğu Şehir"). Klasiklerde bildik Türkçe ad ("Define Adası"); üçünde iki dil aynı (Frankenstein, Jane Eyre, Peter Pan), o satır tekrar olur.

## Sürüm
Derleme 50 Mehmet'in sözüyle bekliyor ("derleme beklesin, birkaç iş daha var"). Karar bugün gelirse derleme 50'ye girer; gelmezse sonraki derlemeye.
