# Sınav sistemi: Charles'ın değerlendirmesi ve ekip kararları

**Tarih:** 22 Kasım 2026, 02:30 · Tek geçiş; üyeler kurgusaldır.
**Dayanak:** editörün dosyaları `raporlar/veri_2026-11-22/sinav_sistemi/` (H1–H8), `veri_2026-11-22/belge_sorulari.md`, `2026-11-22_editor_gece_notu_cevabi.md`. Kod ve canlı veri editörden; bu raporda yeni varsayım yok, hipotezler işaretli.

## 1. Tablo: sistem bugün ne yapıyor
- **İki test var, üç değil.** Onboarding'de kullanıcı seviyesini kendi seçiyor; "emin değilsen ölçelim" yeniden ölçme testini açıyor.
- **Yeniden ölçme** (kelime taraması + en çok 3 boşluk doldurma parçası): 118 müşteri turu, 106 tamamlandı, ortanca 3,2 dakika. Kısa ve bitiriliyor; iskeleti sağlam.
- **Belge testi** (6 ısınma + 3 metin + sınır soruları): müşteriden 0 deneme. 176 soru üretimle yazıldı, insan okumadı, gerçek kullanıcıyla denenmedi.
- Hiçbir seviye etiketi (kelime bantları, parçalar, sorular) bir uzman ya da veriyle doğrulanmamış. İlk gerçek veri H4.

## 2. Bulgular (önem sırasıyla)
**B1. Test, B1 okurunu A2'ye indiriyor.** Kelime taraması B1 kestirdiği 34 turun **27'si A2** bitti. Neden parçalarda: B1'de doğru boşluk oranı %42 (3 şıkta şans %33).
**B2. Neden zorluk değil, belirsiz sorular.** Altı B1 parçasının dördünde birden fazla şık cümleye uyuyor:
| Parça | Boşluk | Doğru sayılan | Uyan öbür şık | Doğru yapan |
|---|---|---|---|---|
| 39 | animal ___ | shelter | hospital | 3/18 |
| 39 | learn to ___ him | trust | follow | 7/18 |
| 38 | she ___ the sound of traffic | missed | hated | 1/14 |
| 41 | customers' ___ | names | orders | 5/15 |
| 41 | couldn't ___ on price | compete | survive | 3/15 |
| 40 | wouldn't ___ two days | last | wait | 2/10 |
Sağlam görünen iki B1 parçası var: 37 (ortalama 1,75) ve 42 (2,33). Okur doğru cevabı ancak parçanın sonunu okuyup geri dönerek bulabiliyor; bu B1 okumasını değil sabrı ölçüyor (ilke 3).
**B3. Sınanmamış seviye veriliyor.** Üçüncü parçada 3/3 yapan okur "bir üst seviye" alıyor ve tur orada bitiyor. Taraması A1 çıkan 5 tur böyle **B2** oldu; hiç B2 parçası görmeden. Sonuç, okurun geçtiği en yüksek parçanın seviyesini aşmamalı.
**B4. Belge testi seviyeyi düşürebiliyor.** Doğrulanmamış bir araç, belge almaya gelen okurun seviyesini indirmemeli.
**B5. "Seviyen yükseldi" çoğu zaman doğru değil.** 106 kaydın 86'sında "önceki seviye" hiç seçilmemiş varsayılan A1. Bunlar ilk ölçüm; yükselme değil.
**B6. Puan yanıltıyor.** Belge testinde en yüksek puan 69 (B2). "100 üzerinden 62" düşük okunur, oysa B2'nin ortası.
**B7. Seviye değişince yolculuk değişmiyor** (1.0.4). Ölçümün en görünür sonucu olması gereken yer aynı kalıyor.
**B8. Kelime taraması kelime bazında kaydedilmiyor;** bantların doğruluğu sınanamıyor.
**B9. Tek tek sorular** (az veri, 10–17 tur; okuyup karar verilecek): A2 parça 59 ikinci boşluk (busy; closed da uyuyor, 4/17), A2 parça 58 ve 60 üçüncü boşluk (5/16, 5/14), A2 parça 33 üçüncü boşluk (7/16), A1 parça 50 ilk boşluk (2/8). B2 parçaları için veri yok (14 parça gösterimi).
**İyi çalışanlar:** sözde kelime denetimi (81 turda sıfır yanlış alarm), süre koruması, yarıda kalan turun kaldığı yerden sürmesi, A1 parçaları (%83).

## 3. Kararlar
### Hemen: sunucu, yeni derleme gerekmez (yayın ve canlıya yazma Mehmet'in sözüyle)
| # | Karar | Not |
|---|---|---|
| C1 | Editörün ısınma kuralı **doğru, onaylandı:** başlangıç, ısınmada sorulan en yüksek seviyeyi geçmez. Dal `fix/assessment-warmup-by-level` | Editörün gece raporu madde 1 |
| C2 | **B1 parçaları 38, 39, 40, 41 devre dışı** (silinmez; `etkin = hayır`). 37 ve 42 kalır. Önce editör doğrular: iki parçayla tur kilitlenmiyor (aynı seviyeden ikinci parça kuralı; önceki turun elemesi havuz daralınca kalkıyor) | Canlıya yazma |
| C3 | **Üçüncü parçada 3/3:** sonuç o parçanın seviyesi olur, bir üstü değil. Genel kural: sonuç, okurun geçtiği en yüksek parçanın seviyesini aşmaz | Sunucu |
| C4 | **Belge testi profil seviyesini yalnız yükseltir.** Düşürme yalnız kullanıcının kendi başlattığı yeniden ölçmede kalır | Sunucu |
| C5 | **Kelime taraması kelime bazında kaydedilir** | Sunucu, yarım gün |
C2–C5 tek PR'da (C1'in dalına eklenebilir). 1.0.2 ve derleme 50 ile uyumu editör doğrular.

### Sıradaki sürüm (uygulama)
| # | Karar |
|---|---|
| C6 | Belge testinde sorular tek tek gösterilir (yarım–1 gün) |
| C7 | Sonuç teşhis diliyle: seviye, o seviyede okurun neyi yapabildiği, sıradaki adım (önerilen hikâye). "Seviyen düştü" yazılmaz: "Seviyeni güncelledik: A2. Bu seviyedeki hikâyeler sana daha rahat gelecek." İlk ölçümde karşılaştırma yapılmaz: "Seviyen: A2". Metinler Paul'dan |
| C8 | 100 üzerinden puan gösterilmez; yerine seviye ve söz ("B2'nin ortasındasın") |
| C9 | **Seviye değişince yolculuk:** kullanıcı o yolculukta henüz hikâye bitirmediyse yeni seviyenin yolculuğu atanır; bitirdiyse bu yolculuk kalır, sıradaki yolculuk yeni seviyeden gelir (sunucu, yarım gün; C2–C5 PR'ına girebilir) |
| C10 | Belge testi kelime adımıyla başlasın önerisi (H8-a, 2–3 gün) **bekler.** Önce C1 ve C6 ile gerçek deneme verisi birikmeli; ısınma kullanıcının seviyesini artık kullanıyor |

### İçerik (Paul yazar, Charles denetler)
- Dört yeni B1 parçası. Kural: her boşlukta yalnız bir şık cümleye uyar; cevap boşluğun bulunduğu cümleden ve bir önceki cümleden çıkar; çeldiriciler aynı türden.
- B9'daki beş boşluk okunur, gerekirse şık değişir.
- 176 belge sorusu okunur; "…" ile biten 29 soru tam soru cümlesine çevrilir. Belge satırı görünürken öncelik bu.
- Kelime tarama bantları: C5 verisi 100 tura ulaşınca bakılır.

### Kalıcı kural (ilke 4): soru denenmeden güvenilmez
Editör ayda bir tablo çıkarır. En az 30 kez görülmüş bir soru şu durumlarda incelemeye alınır: doğru oranı şans düzeyinin 10 puan üstünden düşük; doğru oranı %95'in üstünde; yanlış bir şık doğru şıktan çok seçiliyor.

## 4. Bilinmeyenler ve açık uçlar
- B1'den A2'ye inen 27 kişinin gerçek seviyesi bilinmiyor; geriye dönük düzeltme yapılmaz. C2'den sonra ana sayfadaki ölçüm kartı onlara yeniden teklif edilebilir (derleme 50'de o kart yalnız yükseltir); ayrı karar.
- B2 parçaları ve belge soruları için veri yok.
- Seviyesi değişenlerin sonraki okuması pek değişmiyor (H5); editörün hipotezi: ücretsiz okurun açabildiği metinler az ve sabit. 1.0.4'ten sonra yeniden bakılır.
- Canlıda eşiklerin ortam değişkeniyle ezilip ezilmediğine bakılmadı (editör).
- Ekibin önceki "seviyesi düşen 4 müşteri" sözü yanlıştı; kayıtta 12 düşüş var.
