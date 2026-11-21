# Editör talimatı – 21 Kasım akşam (son hâl, 21:35)

**Kaynak:** Mehmet (20:16): "Bu işlerin hepsi hemen sırayla yapılsın." · (21:31): "Hepsini yapması için editöre talimat ver."
**Bu dosya tek başına okunur** ve önceki akşam sürümünün yerine geçer; bilgi cevaplarından (`raporlar/2026-11-22_editor_bilgi_cevaplari.md`) sonraki kararlar içine işlendi. Gerekçeler: `raporlar/2026-11-21_aksam_ekip_kararlari.md`.

## Kurallar
- **Sırayla:** A → B → C → D. Kullanım sınırına takılırsan kaldığın yerden devam et. Çeviri işçileri 22 Kasım 04:30'da başlıyor; bu talimat bitmediyse onları bitene kadar ertele.
- **Önce koda bak.** Bir madde kodda zaten varsa ya da kodla çelişiyorsa yazma, raporla.
- **Onaylar (Mehmet'in 20:16 sözü):** derleme 50 için "çıkar"; sunucu PR'ı için "yayınla" (tam test temizse); içerik betiği için "yaz" (yedekli). Bu söz yalnız bu dosyadaki işleri kapsar. Bir şey ters giderse dur ve raporla.
- **Mehmet'e soru sorulmaz.** Karar gerektiren şey rapora yazılır; ekip aynı gün karar verir. O madde beklerken sıradakine geç.
- **Görüntüler önce ekibe** (Dieter, Don), sonra TestFlight.

## A. Uygulama → derleme 50 (`feat/journey-core`)
**A1. Ana sayfa yolculuk kartı**
- Kartın düğme dışındaki bütün gövdesi yolculuk sayfasını açar. Düğme olduğu gibi kalır. Olay `journey_page_shown`, kaynak `home_card_body`.
- Günlük hak kullanılmışken "Premium'la şimdi oku"nun altında "Yarın hatırlat": `JourneyReminderDoor` yeniden kullanılır; yolculuk sayfasındaki analitik metot ortak yere taşınır, kaynak `home`.
- Hiç hikâye okunmamış yolculukta sayı yazılmaz: "Senin yolculuğun · {yolculuğun adı}". İlk hikâyeden sonra "n/toplam". Başlangıç yolculuğu (n/4) değişmez.

**A2. Kariyer sayfası** (`mockup/career-readability`'deki E1 ana dala; E2 ve anahtar silinir, metinler çeviri dosyasına)
- Yol rozetin kenarından çıkar, öbür rozetin kenarında biter. Kapı ve eşik işareti yok. Sıradaki rozetin çevresindeki halka yok; sıradaki rütbe yarı renkli rozet ve "Sıradaki: {rütbe}" etiketiyle ayrışır. Uzak rütbeler küçük, soluk, kilitsiz.
- **Yolda yüzde:** dolumun ucundaki bayrak yüzdeyi taşır ("%11"). Dolum %0 iken sayı yerine "Yeni yol başladı". Etiket beyaz zemin üstünde koyu, en az 13 pt kalın; büyük yazıda 17 pt'de sabit. Hiçbir rozete ve ada binmez; yer yoksa yolun öbür yanına geçer.
- Bayrak simgesi rozet kenarına 24 pt'den yakın olamaz; dolum çizgisi gerçek yerinde kalır.
- Alt şerit: ilerleme çubuğu kalkar, yalnız cümle kalır ("Meraklı'ya yaklaşık 5 günlük okuma kaldı"; 60 XP ve altında "Meraklı olmana çok az kaldı!").
- Açılışta, yalnız son açılıştan beri XP değiştiyse, dolum eklenen kısmı bir kez 0,6 saniyede doldurur; yüzde birlikte sayar. "Hareketi azalt" açıksa animasyon yok.
- Kayıt kartı: büyük yazıda tek satır (simge, "İlerlemeni güvene al ›", ×); hiçbir yazı boyunda kullanıcının rozetini örtmez (testle kilitli). × dokunma alanı 44 × 44 pt.
- Rozeti görünmeyen rütbenin adı da çizilmez.
- Ekran okuyucu: yol için tek birleşik etiket ("Meraklı'ya giden yolun yüzde 11'i. Yaklaşık 5 günlük okuma kaldı."); rozetler düğme rolüyle ve durumuyla ("Meraklı, sıradaki rütbe").
- Dokunulmayanlar: rozet alt sayfası, eşikler, rütbe adları, rozet çizimleri.

**A3. Yorum ekranı (T3):** commit'siz taslak koda alınır. Üç gerçek yorum, kelimesi kelimesine, takma adlı, kaynağı yazılı. SE 3'te ilk yorumun tamamı ve "Devam" kaydırmadan görünür.

**A4. Günün quizi**
- Şıklar: en az 3 harf; çeldirici doğru cevapla aynı türden; türü bilinmeyen ya da karşılığı 3 harften kısa kelime çeldirici olmaz (soru olabilir).
- Sonuç başlığı skor değil: 8 ve üstü "{d}/10, harika gidiyorsun." · 5–7 "{d} kelimeyi bildin, {y} yeni kelimeyle tanıştın." · 4 ve altı "{y} yeni kelimeyle tanıştın, yarın yine buradayız."
- Ana düğme "Sıradaki hikâye" (var olan `NextReadingCard` ana eyleme çıkar). "Kaçırdığın kelimeleri çalış" → "Yeni tanıştığın kelimeler", ikincil; alt sayfanın başlığı da aynı. "Sonucu paylaş" yalnız 8 ve üstünde, ikincil. "Yeniden başla" metin bağlantısı. Toplu ekleme yazılmaz.
- Quiz sekmesinin ilk ekranı: "#49" kalkar; halkaların üstüne "Bu hafta"; çözülen gün dolu halka; ortadaki boşluk daralır.
- Yeni analitik olayı yazılmaz.

**A5. "Seviyeni yeniden ölç":** ana sayfa kartından başlatılınca uygulama `trigger: "offer"` gönderir (seviye yalnız yükselir). Profil satırı `user` kalır.

**A6. "Geri dön" bildirimi:** bildirimde hikâye kimliği varsa o hikâyenin kapak sayfası açılır; yoksa ana sayfa.

**A7. Sürüş ve derleme:** SE 3 + büyük yazı. Kariyer (277 XP, %0, %92), ana sayfa (hak var / hak kullanılmış / ikinci yolculuk), yolculuk sayfası, yorum ekranı, günün quizi (sekme, soru, üç sonuç başlığı). Görüntüler `raporlar/ekran_2026-11-22/`. Görüntüleri gönder; **ekip "temiz" deyince** derleme 50 TestFlight'a ve Play dahili teste. Daldaki önceki düzeltmeler (T15, T17, T18, T19, seslendirme, bildirim ölçümü, yolculuk kartı ölçümü, ayar uyarısı, `d2228a73`) bu derlemede.

## B. Sunucu → tek PR (tam test temizse yayınla)
- **"Geri dön" metinleri:**

| Gün | Başlık | Gövde | Sıradaki hikâye bilinmiyorsa |
|---|---|---|---|
| 3 | {hikâye} seni bekliyor | Kaldığın yerden, {dk} dakikalık bir hikâye. | Başlık: "Kısa bir hikâye okuyalım mı?" · Gövde: "Seviyene göre {dk} dakikalık hikâyeler var." |
| 7 | Bir haftadır görüşmedik | Sıradaki hikâyen hazır: {hikâye}. Defterindeki kelimeler de yerinde. | Gövde: "Seviyene göre yeni bir hikâye seçtik. Beş dakika yeter." |
| 14 | Yolculuğun yerinde duruyor | {hikâye}, {dk} dakika. Ne zaman istersen oradan devam. | Başlık: "Hikâyelerin yerinde duruyor" |
| 30 | Kapı hep açık | Kaldığın yerdeyiz. {hikâye} seni bekliyor. | Gövde: "Kaldığın yerdeyiz. Kısa bir hikâyeyle başlayabilirsin." |

  Başlık 40 karakteri geçerse "Sıradaki hikâyen seni bekliyor". {hikâye}: yarım kitap varsa o, yoksa yolculuğun şimdiki durağı. **Atama yapmayan salt okuma sorguyla** hesaplanır (`JourneyService.GetAsync` yolculuk atıyor; o kullanılmaz). Bildirime hikâye kimliği eklenir; `action` "win_back" kalır.
- **Quiz cevabı:** "doğru karşılık bu metinle başlıyor mu" kabulü kalkar; tam eşleşme. Eski sürümlerin gönderdiği kısaltılmış doğru şık yanlış sayılmamalı; önce bunu doğrula, risk varsa dur ve yaz.
- **Haftalık Şampiyon:** hafta kapanınca (pazar 23:59, Türkiye saati) en yüksek XP'li tek kişiye; şart en az 10 katılımcı ve 300 XP. Önceden verilmiş rozetler silinmez.

## C. İçerik betiği (canlıya yazma; önce yedek)
- **Etiket A2 → B1, 7 metin:** 1096, 1098, 1039, 1097, 1103, 1094, 1067. **1063 ve 1089'a dokunma.**
- **The Island Where Rabbits Won (1023):** önce okuma konumu nasıl tutuluyor, bak. Bölüm sırasıyla tutuluyorsa gövdeyi kararlar raporu bölüm 4'teki A2 yazımıyla değiştir (dört bölüm, aynı sıra; başlıklar yeni adlarıyla); çeviri, sözlük eşleşmesi ve kelime sayısı yenilenir; eski gövde yedekte kalır. Karakter ya da kelime konumuyla tutuluyorsa **çalıştırma**, raporla.

## D. Veri ve taslak (salt okuma; derleme 50'ye girmez)
- "Seviyeni belgele"nin 176 sorusunun tam dökümü: `raporlar/veri_2026-11-22/belge_sorulari.md`, doğru şık işaretli, "…" ile bitenler ayrı işaretli.
- Ana sayfa sadeleşme taslağı: ayrı dalda, gerçek ekranda, üç kullanıcı durumuyla (yeni, 3. gün, güncelleyen). **A:** kişi kartı ve yolculuk kartı tek kartta. **B:** ilk ekranda yalnız yolculuk kartı ve sıradaki hikâye; öbür kartlar altta. İkisinde de seri riski yolculuk kartının içinde tek satır.

## Rapor
`raporlar/2026-11-22_editor_aksam_isi.md`: her madde için bitti / yapılmadı ve neden; ekibin karar vermesi gerekenler en üstte. A7 görüntüleri hazır olunca ayrı bir commit ile hemen gönder (ekip onu bekliyor). İş listesinin "Mehmet'ten doğrudan" bölümüne tek satır.
