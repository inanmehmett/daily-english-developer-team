# Akış ve bildirim incelemesi

**Rol:** Don Normal (akış); bildirim ölçümü Nate Gümüş; itiraz Nassim Talip. **Tarih:** 16 Kasım 2026.
**Dayanak:** `raporlar/2026-11-16_neden_kalmiyorlar.md` (191 müşteri, 29 Eki – 15 Kas), kod okuması, 15 Kasım arayüz taramasının görüntüleri. Bu incelemede yeni ekran görüntüsü alınmadı.

## Sonuç

Uygulama yeni kullanıcıyı ilk metne götürüyor (191 müşteriden 138'i başlıyor) ama metnin sonuna götüremiyor (72'si bitiriyor) ve bitireni ertesi güne bağlayan bir söz vermiyor. Bildirimler bu boşluğu doldurmuyor: 803 gönderimin 623'ü zaten gitmiş ve bir daha dönmemiş kişilere gitti; izin ve ulaşma ölçülemediği için bildirimin işe yarayıp yaramadığını söyleyemiyoruz.

Beş bulgu akışta, dört bulgu bildirimde. Hepsi hipotez; her birinin yanında neyle ölçüleceği yazıyor.

## Kullanıcının yolu ve kaybın yeri

| Adım | Müşteri | Bir öncekine oran |
|---|---|---|
| Hesap açıldı | 191 | |
| Onboarding bitti | 183 | %96 |
| Bir metne başladı | 138 | %75 |
| Bir metni bitirdi | 72 | %52 |
| Bitişten sonra başka bir metne başladı | 38 | %53 |
| Ertesi gün döndü | 36/185 | |

En büyük iki düşüş: başlayanların yarısı ilk metni bitirmiyor; bitirenlerin yarısı ikinciye geçmiyor.

## Akış bulguları

### A1. A2 seçen okurun ilk metni B1 ve uzun
A2 seçen 35, B1 seçen 20 kişi "Why Penguins Can't Fly" ile başlamış (B1 etiketi, 332 kelime). Bitirme 23/63 (%37). A1'in ilk metni "Two Cups" (217 kelime) 29/51 (%57). Bitirmeyenler metinde ortanca 1,3 dakika kalmış.
- **Yorum:** kullanıcı seviyesini söyledi, biz bir üstünü verdik. Bu bir eşleme hatası: verdiğimiz söz ("seviyene göre") ile yaptığımız uyuşmuyor.
- **Öneri:** A2 ve B1 seçene ilk metin olarak kendi seviyesinde, 250 kelimeyi geçmeyen bir metin. Hangi metin, Paul Ulus'un işi; A2'de böyle açık metin yoksa içerik ihtiyacı olarak yazılsın.
- **Ölçüm:** ilk metni bitirme oranı, seviyeye göre. Hedef A2 ve B1'de %37 → %50.

### A2. Bitiş ekranı ücretsiz okuru kilitli diziye gönderiyor
"Sıradaki okuma" kartı kilitli kitabı eliyor, dizide kilide bakmıyor (`book_list_view_model.dart`, `nextReadingSuggestion`). 41 müşteriye dizi önerildi ("New in Town", "Game Day"; ücretsiz bölümleri yok); 21'i beş dakika içinde kilide çarptı. İlk metnini bitiren 72 kişinin 40'ı sonraki yarım saatte bir kilit ya da paywall gördü.
- **Yorum:** kartın kodundaki kendi kuralı "öneri bir davet, ödeme kapısı değil". Dizide bu kural uygulanmamış; kullanıcının en hevesli anında önüne kapalı kapı çıkıyor.
- **Öneri:** ücretsiz okura yalnız açabileceği bir sonraki metin önerilsin (açık üç metinden okumadığı, yoksa günlük açılan metin). Küçük kod işi.
- **Ölçüm:** bitişten sonra 30 dakika içinde ikinci metne başlayanlar: 18/72 → en az 30/72.
- **Karar:** Sean Büyüt itiraz edebilir (kilide çarpmak satışın yolu). Veride satın alan 4 kişi var; bu yoldan geldikleri gösterilemedi.

### A3. Metnin ortasında kalan okur geri çağrılmıyor
Gidenlerin %35'inin son kaydı okumanın ortası (okuma, kelimeye bakma, dinleme). 16 kişi uygulamayı yeniden açıp hiçbir şey yapmadan çıktı.
- **Yorum:** geri gelen okurun ana sayfada ilk gördüğü şey yarım kalan metni olmalı. Görüntülerde okumuş kullanıcının ana sayfası dolu geliyor; "kaldığın yerden devam et" kartının en üstte ve tek ana eylem olup olmadığı bu incelemede doğrulanmadı.
- **Öneri:** Dieter Koç ikinci turda yarım metni olan kullanıcının ana sayfasını çeksin; kart ilk ekranda değilse en üste alınsın.
- **Ölçüm:** uygulamayı yeniden açıp okumaya devam edenlerin oranı.

### A4. İlk yarım saatte Premium şeridi
185 müşterinin 176'sına hesap açıldıktan sonraki 30 dakikada Premium şeridi kaydı düşmüş. Görmeyen 9 kişiyle karşılaştırma yapılamıyor; etkisi bilinmiyor.
- **Yorum:** kullanıcı henüz bir şey okumamışken satış teması, uygulamanın ne olduğunu anlatmıyor; "yoğun kullanım" tetikleyicisi yeni kullanıcıda yanlış ateşleniyor.
- **Öneri:** şerit ilk metin bitene kadar gösterilmesin. Etki ölçülemeyeceği için karar ilke kararıdır; Sean Büyüt ve Mehmet verir.

### A5. Ertesi güne söz yok
Ertesi gün dönen 37 kişinin 30'u okudu, 9'u günlük açılan metni açtı. Günlük metni hayatında bir kez bile açan 35 kişi var. Yani uygulamanın "her gün bir metin daha açılır" özelliğini müşterilerin beşte biri bile görmemiş.
- **Yorum:** ücretsiz okurun ertesi gün gelmesi için elimizdeki tek somut neden bu; ama ilk gün bitiş ekranında söylenip söylenmediği doğrulanmadı.
- **Öneri:** ilk metnin bitiş ekranında tek satır: yarın hangi metnin açılacağı (adı ve kapağıyla). Yeni ekran değil, mevcut bitiş ekranında bir satır.
- **Ölçüm:** ilk gün metin bitirenlerin D1'i: 26/64 → hedef 32/64; günlük metni açan müşteri oranı.

## Bildirim bulguları

### B1. İzni ve ulaşmayı göremiyoruz
İzin alanı 191 müşterinin hepsinde boş, ulaşma alanı 803 gönderimin hepsinde boş. İkisini de dolduran sürüm henüz müşterilerde değil. Bildirime dokunma 10/803, iki saat içinde uygulamada görülme 33/803.
- **Öneri:** bildirim metni ya da zamanlaması üzerinde yeni iş, ölçümü taşıyan sürüm yayınlanıp bir hafta veri toplanana kadar yapılmasın. Yoksa neyi düzelttiğimizi bilemeyiz.

### B2. Gitmiş kişiye bildirim yağıyor
803 gönderimin 623'ü, kullanıcının son görüldüğü andan sonra gitti ve arkasından dönüş gelmedi. 58 müşteri son ziyaretinden sonra beş ve üzeri bildirim aldı. Günde bir sınırı tutuyor; ama türler sırayla devreye girdiği için (ilk okumaya çağrı 1-3-7. gün, geri dön 3-7-14-30. gün, günlük metin, günün quizi, kelime tekrarı) susmuyor.
- **Yorum:** README madde 9'un sorusu: "kullanıcı bunu nasıl yaptığımızı bilse rahatsız olur muydu?" Cevap vermeyen birine iki haftada on bildirim, evet.
- **Öneri:** arka arkaya üç bildirime karşılık uygulama açılmadıysa günlük türler (günlük metin, günün quizi, kelime tekrarı, seri başlat) sussun; yalnız geri dön basamakları (7, 14, 30. gün) kalsın. Kullanıcı dönünce sayaç sıfırlanır.
- **Ölçüm:** bildirim kapatma ve uygulama silme oranı (izin alanı dolunca), geri dön bildirimlerinden dönüş.

### B3. 22:00'de bildirim gidiyor
62 gönderim kullanıcının saatiyle 22:00–22:59 arasında. Sunucu sınırı 09–23, ekip kuralı 09–21.
- **Öneri:** ikisinden biri değişsin. Don Normal'in görüşü: kural 09–21 kalsın, kod ona uysun; kullanıcı kendi seçtiyse (22:00 seçen 4 kişi var) onun seçimi geçerli.

### B4. Türlerin karşılaştırması
İki saat içinde uygulamada görülme: seri hatırlatma 6/24, günün quizi 10/146, günlük hatırlatma 3/21, seri başlat 5/116, günlük metin 3/154, kelime tekrarı 3/126, ilk okumaya çağrı 1/109, geri dön 1/96.
- **Yorum:** çalışan türler zaten kullanan kişiye gidenler. Hiç okumamış ya da gitmiş kişiye gidenler (ilk okumaya çağrı, geri dön) neredeyse sıfır. Bunlar ulaşmıyor mu, ilgi mi çekmiyor, B1 çözülmeden bilinmez.

## Önerilen sıra

| Sıra | İş | Tür | Karar |
|---|---|---|---|
| 1 | İzin ve ulaşma ölçümünü taşıyan sürümün yayını | Yayın | Mehmet |
| 2 | A2: öneri kartında dizi kilidi | Küçük kod | Mehmet (Sean Büyüt'ün itirazıyla) |
| 3 | A1: A2 ve B1 için ilk metin | İçerik seçimi + küçük kod | Paul Ulus önerir, Mehmet onaylar |
| 4 | B3: saat sınırı | Tek satır kod ya da kural değişikliği | Mehmet |
| 5 | B2: susma kuralı | Orta kod (sunucu) | Mehmet |
| 6 | A5: bitiş ekranında yarının metni | Küçük kod | Mehmet |
| 7 | A4: şeridin zamanı | Küçük kod | Sean Büyüt + Mehmet |
| 8 | A3: geri gelenin ana sayfası | Önce görüntü | Dieter Koç |

Onboarding'e yeni soru ya da ekran eklenmiyor; hiçbir öneri bunu gerektirmiyor.

## İtirazlar (Nassim Talip)

1. A1'de neden-sonuç yok: A2 seçenler zaten daha az sabırlı bir grup olabilir. Metni değiştirince oran değişmezse hipotez düşer; bunu baştan kabul edelim.
2. A2'yi düzeltmek satışı düşürebilir. Satış sayısı 4; ölçemeyiz. Karar veriyle değil ilkeyle veriliyor, öyle yazılsın.
3. B2'deki "623 bildirim boşa gitti" cümlesi fazla sert: ulaşmayı göremiyoruz, bir kısmı hiç gösterilmemiş olabilir. O zaman sorun susturmak değil ulaştırmaktır.
4. Bütün sayılar 18 günlük lansman kitlesinden ve olay kaydı dönenlerin beşte birini kaçırıyor.
5. Sekiz iş birden yapılırsa hangisinin işe yaradığı ayrılamaz. İkişer ikişer çıkmalı.
