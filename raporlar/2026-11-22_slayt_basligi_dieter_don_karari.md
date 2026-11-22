# Ana sayfa slaytı: Dieter ve Don'un kararı

**Tarih:** 22 Kasım 2026, 14:40 · Tek geçiş; üyeler kurgusaldır.
**Soru (Mehmet, 14:30):** slayttaki kitap adı tek satıra sığmıyor, normal mi? Türkçe ad da yazmalı mı?
**Dayanak:** `raporlar/2026-11-22_editor_slayt_basligi.md` (kod ve 23 slaytın ölçümü), `ekran_2026-11-22/ana_sayfa_slayt_mehmet.png`.

## Kararlar (derleme 50)
| # | Karar | Gerekçe |
|---|---|---|
| S1 | **İki satır başlık normal; kalır.** Yazı küçültülmez, üç nokta konmaz | 23 başlığın 7'si iki satır, kesilen yok. Tek satıra zorlamak ya başlığı keser (7 başlık yarım kalır) ya da slayttan slayta yazı boyunu değiştirir; ikisi de bugünkünden kötü (Dieter) |
| S2 | **Türkçe ad eklenir:** İngilizce başlığın altında tek satır, daha küçük ve hafif (15 pt, normal kalınlık, beyazın %85'i); sığmazsa üç nokta | Keşif kartlarıyla aynı kural (Ağustos kararı: ana başlık İngilizce, altında Türkçe). A1–A2 okur "Carved from a Cliff"i çözemez; "Gül Rengi Şehir: Petra" onu içeri çağırır. Ana sayfanın işi okuru bir metne sokmak (Don) |
| S3 | Türkçe ad İngilizce adla **aynıysa gösterilmez** (Frankenstein, Jane Eyre, Peter Pan). Cihaz dili Türkçe değilse gösterilmez (keşif kartındaki kural) | Tekrar satırı gürültü |
| S4 | Üstteki satır kalır ve **seviye eklenir:** "tür · süre · seviye" ("Culture · 4 dk · B1") | Slayt okurun seviyesine "yakın" metinleri gösteriyor, aynı seviyeyi değil. Yolculuk kartı seviyeyi yazıyor, slayt yazmıyor; okur dokunmadan önce bilmeli (Don) |
| S5 | Tür adı Türkçe arayüzde Türkçe yazılır ("Kültür") — **yalnız çevirisi kodda zaten varsa.** Yoksa dokunma, raporla | Türkçe ekranda "Culture" yabancı duruyor; ama yeni çeviri tablosu bu sürümün işi değil |
| S6 | Yazı bloğu görselin yarısını geçmez. En uzun durum SE 3'te sınanır: "Around the World in Eighty Days" + "Seksen Günde Devriâlem" | Üç satır yazı + üst satır görseli boğmamalı; alttaki koyulaşma yazının tamamını kapsamalı |

Reddedilenler: B (yazı küçülür), C (üç nokta), E (süre kalkar; süre "kısa, okurum" kararını verdiren bilgi).

## Görüntüde ayrıca görülenler
| # | Gözlem | Karar |
|---|---|---|
| G1 | "3 gün seri" Türkçe değil | "3 günlük seri" (derleme 50; tek metin). Aynı kalıp başka yerde varsa orada da |
| G2 | Slayt, yolculuk kartından daha büyük ve daha çekici; ana eylemle ("Sıradaki hikâye") yarışıyor | Bu sürümde dokunulmaz. Yayından sonra ölçülür: ana sayfadan açılan metinlerin kaçı yolculuk kartından, kaçı slayttan. Ana sayfa sadeleşmesi konuşulursa veri bu olur |
| G3 | Profil resminin çevresindeki halka ve üstündeki küçük nokta açıklamasız bir ilerleme göstergesi | Editör ne gösterdiğini koddan yazar (bilgi). Değişiklik yok |
| G4 | Yolculuk kartında "1/4" ve dört dilimli çizgi aynı şeyi iki kez söylüyor | Kabul; başlık sayıyı, çizgi yeri gösteriyor. Değişiklik yok |

## Editöre
S1–S6 ve G1, `feat/journey-core`'a, derleme 50'ye. Tahmin: yarım gün. Görüntü: SE 3 ve 390 pt'de üç slayt (tek satır başlık, iki satır başlık, iki dilde aynı ad), büyük yazıyla da. G3'ün cevabı raporda.

## Ek (14:45, Mehmet: "kararları ver")
G2 için karar değişti: bu sürümde slaytın üstüne "Başka hikâyeler" bölüm başlığı gelir (boy ve yer aynı) ve ana sayfadan açılışların kaynağı ölçülür. G3 bilgi olarak kalır. Editörün talimatı: `ortak/editor_gorevi_2026-11-22_ana_sayfa_slayt.md`.
