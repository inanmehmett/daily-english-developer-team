# Editöre: ana sayfa slaytı ve görüntüdeki öbür düzeltmeler (derleme 50)

**Tarih:** 22 Kasım 2026, 14:45 · **Kimden:** ekip (Dieter, Don, Paul) · **Kime:** editör
**Mehmet (14:35):** "Tamam. Kararları ver, editöre rapor yaz."
Bu dosya tek başına okunur. Senin sorduğun iki soru ve Mehmet'in ekran görüntüsünde görülen öbür şeyler burada karara bağlandı; açık soru kalmadı. Yetki: `ortak/editor_gorevi_2026-11-22_surum_kalan_isler.md` içindeki gibi (dal `feat/journey-core`, derleme 50). Gerekçeler: `raporlar/2026-11-22_slayt_basligi_dieter_don_karari.md`.

## Yapılacaklar
| # | İş | Ayrıntı |
|---|---|---|
| 1 | **Başlık iki satır kalır** | Bugünkü gibi: 24 pt kalın, en çok 2 satır. Yazı küçültme ve tek satıra indirme yok (seçenek A) |
| 2 | **Türkçe ad satırı** | İngilizce başlığın hemen altında, `SubtitleTR`. 15 pt, normal kalınlık, beyazın %85'i, en çok 1 satır, sığmazsa üç nokta. Gösterilmez: Türkçe ad İngilizce adla aynıysa (büyük-küçük harf ve boşluk farkı sayılmaz); cihaz dili Türkçe değilse (keşif kartındaki kuralın aynısı) |
| 3 | **Üst satıra seviye** | "tür · süre · seviye" ("Culture · 4 dk · B1"). Seviye metnin kendi etiketi |
| 4 | **Tür adı Türkçe** | Yalnız türün Türkçe karşılığı kodda ya da veride **zaten varsa** ("Kültür"). Yoksa İngilizce kalır; yeni çeviri tablosu yazma, raporda listele |
| 5 | **Slaytın üstüne bölüm başlığı** | Yolculuk kartı ile slayt arasına, "Senin yolculuğun" başlığıyla aynı biçimde tek satır: **"Başka hikâyeler"**. Sağında bağlantı yok. Slaytın boyu ve yeri değişmez |
| 6 | **"3 gün seri" → "3 günlük seri"** | Aynı kalıp başka ekranda da varsa (profil, seri kartı, bildirim metni) orada da. Tekil: "1 günlük seri" |
| 7 | **Ölçüm** | Ana sayfadan açılan her metin için kaynak yazılsın: yolculuk kartı düğmesi, yolculuk kartı gövdesi, slayt (kaçıncı slayt), öbür raflar. Olay bugün varsa yalnız eksik kaynağı ekle; hangisinin var olduğunu raporda yaz |

**5'in nedeni (ekip kararı, veriyle değil yargıyla):** slayt yolculuk kartından büyük ve ana eylemle ("Sıradaki hikâye") yarışıyor. Boyunu küçültmek, eklenen Türkçe satırla çelişir ve elde veri yok. Bölüm başlığı slaytı "ikinci raf" olarak işaretler; yolculuk kartı sayfanın tek başlıklı ana işi olarak kalmaz, ama sıra ve ad hiyerarşiyi söyler. Asıl karar 7'nin verisiyle, yayından sonra.

## Sınırlar ve denetim
- Yazı bloğu (üst satır + başlık + Türkçe ad) slayt görselinin yüksekliğinin yarısını geçmez; alttaki koyulaşma yazının tamamını kapsar. Geçiyorsa önce üst boşluğu daralt; yetmezse dur ve görüntüyle yaz.
- En kötü durumlar, SE 3 (375 pt) ve 390 pt, normal ve büyük yazı: "Around the World in Eighty Days" + "Seksen Günde Devriâlem" · "Timbuktu: The Real End of the Earth" + "Dünyanın Öbür Ucu: Timbuktu" (Türkçe ad da uzun) · "Frankenstein" (Türkçe satır yok) · tek satır başlık + Türkçe ad.
- Büyük yazıda başlık yine en çok 2, Türkçe ad en çok 1 satır.
- Ekran okuyucu: slayt tek öğe olarak okunur: "{İngilizce ad}, {Türkçe ad}, {tür}, {süre}, {seviye}".
- Slayt noktaları, kaydırma ve dokunma davranışı değişmez.

## Bilgi olarak istenen (değişiklik yok)
- Profil resminin çevresindeki halka ve üstündeki küçük nokta neyi gösteriyor (rütbe ilerlemesi mi), dokunulunca ne oluyor?
- Slayt kendiliğinden ilerliyor mu; ilerliyorsa kaç saniyede?
- Slayta hangi metinlerin, hangi sırayla girdiği ("seviyeye yakın" tam olarak ne demek; okurun okuduğu metin slayttan düşüyor mu).

## Rapor
`raporlar/2026-11-22_editor_ana_sayfa_slayt_raporu.md`: yedi madde için bitti / yapılmadı ve neden; yukarıdaki dört durumun görüntüleri (`raporlar/ekran_2026-11-22/`); üç bilgi sorusunun cevabı. Derleme 50'yi bu iş için ayrıca bekletme: derleme Mehmet'in sözüyle çıkıyor; bu iş o sırada daldaysa girer.
