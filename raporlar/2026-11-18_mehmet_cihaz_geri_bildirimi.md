# Sürüm 1: Mehmet'in cihaz testi geri bildirimi

**Tarih:** 18 Kasım 2026. **Yazan:** editör. **Okuyacak:** ekip.
**Bağlam:** Mehmet, Sürüm 1 dalını kendi iPhone'unda denedi. Derleme canlıya değil, Mac'teki yerel sunucuya bağlıydı. Aşağıdakiler Mehmet'in söyledikleri, editörün her biri için değerlendirmesi ve ekibin `raporlar/2026-11-18_surum1_ekip_degerlendirmesi.md` kararlarıyla kesiştiği yerlerdir.
**Durum:** Hiçbir şey uygulanmadı. Mehmet önce değerlendirme, sonra sıralama istiyor. Ekip kararlarının uygulaması da bu sıralamayı bekliyor.

## Mehmet'in söyledikleri

### 1. Yolculuk sayfası
> "Kitap yolculuğu sayfası çok kötü. Önceki yolculuk ilerleme sayfasında kutular içine kitaplar konulacak sanmıştım."

- **Hangi ekran:** Editör bunu Profil'den açılan harita sayfası (`/career`) olarak anladı. Mehmet henüz doğrulamadı.
- **Ne yapılmıştı:** Eski ilerleme sayfası kaldırıldı, yerine düz bir liste kondu: seviye, yolculuk adı, durak satırları. Kutu yok, kapak yok. Görünüm Mehmet'e gösterilmeden değişti.
- **Mehmet'in beklentisi:** Eski sayfanın düzeni kalsın, kutuların içine yolculuğun kitapları (kapaklarıyla) girsin.
- **Ekip kararıyla ilişkisi:** Karar 5 "harita dönüşümü kapalı kalır" diyor. Bu sürümde eski sayfa geri gelir; çakışma yok.
- **Açık iş:** "Eski düzen + kutularda kapak" tasarımı sonraki sürüme kalır. Önce taslak, Mehmet görmeden kod yok.

### 2. "Sıradaki durak"
> "Sıradaki durak pek olmamış. Bir okur için, İngilizce öğrenen için soğuk bir kelime."

- **Kapsam:** "Durak" kullanıcıya görünen yaklaşık 10 metinde geçiyor:
  - "Sıradaki durak" (ana sayfa düğmesi, bitiş ekranı);
  - "SIRADAKİ DURAK · 2/4";
  - "Sıradaki durak yarın açılır";
  - "YOLCULUĞUNUN 4 DURAĞI" (onboarding plan ekranı);
  - "Ücretsiz başla: günde bir durak" (onboarding teklifi);
  - "Bütün duraklar açık, beklemek yok" (satın alma sonrası);
  - "4 durak" (başlangıç sonu ilerleme kartı);
  - kilitli içerik sayfasının gövdesi.
- **Editörün önerisi:** "Durak" yerine "hikâye"; "yolculuk" kalır. Uygulama bu kelimeyi zaten kullanıyor ("2/7 hikâye", "şimdi 3 hikâye açık"). Örnek: "Sıradaki hikâye", "Sıradaki hikâye yarın açılır", "Ücretsiz başla: günde bir hikâye".
- **Dikkat:** B1 başlangıç metinleri kurgu değil (penguenler, Berlin Duvarı). Uygulama onlara da "hikâye" diyor; yeni bir tutarsızlık doğmaz ama ekip bilsin.
- **Ekip kararıyla ilişkisi:** Bütün plan ve ekip kararları "durak" ile yazılmış (`ortak/butun_plan.md`, karar 2 ve 3, TestFlight listesi). Kelime değişirse bu metinler de yeni kelimeyle yazılır. **Bu karar, karar 2 ve 3'ün uygulamasından önce verilmeli.**
- **Karar bekliyor:** Kelimeyi Mehmet seçecek; ekibin (Paul) önerisi istenir.

### 3. Kitap kapakları
> "Kitap kapaklarını görseler sıradakine geçince daha iyi etkilenirler, motive olurlar."

- **Bugün:** Kapak yalnız ana sayfa kartında var. Bitiş ekranında sıradaki metnin yalnız adı ve açıklaması duruyor. Onboarding plan ekranında dört metnin yalnız adı var.
- **Editörün değerlendirmesi:**
  - Bitiş ekranına kapak: küçük iş, veri hazır.
  - Onboarding plan ekranına kapak: başlangıç önizleme ucuna kapak adresi eklenmeli; o da küçük.
- **Ekip kararıyla ilişkisi:** Kararlarda yok. Karar 2 ile aynı ekran (bitiş); birlikte yapılırsa ekrana bir kez dokunulur.
- **Tasarım sorusu (Dieter):** SE 3'te bitiş ekranı zaten dolu: ilerleme çizgisi, ad, açıklama, iki kapı, quiz bağlantısı. Kapak eklenince açıklama kısalmalı mı?

### 4. Kelime balonu
> "Tooltip ekranda fazla yer kaplıyor açılınca. Okuma yaparken tooltip açınca göz merceklerini yeniden ayarlamak gerekiyor ve bu da yoruyor. Bu konuyu ciddi ele al."

- **Ne söylüyor:** Balon büyük; okurun gözü metinden balona, balondan metne geçerken yeniden odaklanmak zorunda kalıyor. Okumanın ana eylemi yoruyor.
- **Editör henüz ölçmedi.** Balonun bugünkü boyutu, kelimeye uzaklığı ve yazı boyu farkı bu turda incelenmedi; aşağıdaki yön bir varsayım.
- **Önerilen yol:**
  1. Kod değiştirmeden ölçüm (SE 3 ve Mehmet'in telefonu):
     - balon ekranın yüzde kaçını kaplıyor;
     - dokunulan kelimeden ne kadar uzakta açılıyor;
     - metinle yazı boyu farkı ne;
     - içinde kaç satır ve kaç düğme var.
  2. Ekran görüntüleriyle bir iki seçenek. Beklenen yön: ilk dokunuşta kelimenin hemen yanında tek satır anlam; ayrıntı (diğer anlamlar, örnek, deftere ekle) ikinci dokunuşta.
  3. Mehmet seçer, sonra uygulanır.
- **Ekip kararıyla ilişkisi:** Paketin dışında. Pakete eklenirse Nassim'in "paket büyüdü, tek tek ölçülemez" itirazı ağırlaşır. Öte yandan kelimeye dokunmak ilk oturumun ana eylemi; Mehmet konuyu ciddi görüyor.
- **Karar bekliyor:** Bu pakete mi girsin, sonraki sürüme mi? Editörün önerisi: ölçüm ve öneri şimdi; karar onu gördükten sonra.

### 5. Günlük hak ne zaman yenileniyor (Mehmet sordu)
- **Cevap:** Kullanıcının yerel gece yarısında (profildeki saat dilimi; Türkiye'de 00:00). Kullanılmayan hak birikmiyor. Hesabın açıldığı yerel günde 2 hak, sonraki günlerde 1.
- **Ekibin bilmesi gereken kenar durum:** "İlk gün" takvim günü. 23:50'de onboarding'i bitiren kullanıcının iki haklı ilk günü 10 dakika sürüyor; gece yarısından sonra hak 1'e düşüyor.
- **Karar gerekirse:** "İlk gün" yerine "ilk 24 saat" saymak mümkün. Bugünkü kural ekibin ilk kararına uygun; değişiklik istenmedi, yalnız not.

### 6. Telefonda ilk kurulumda hiçbir şey görünmedi
> "Şu an ne yeni yolculuk sayfası görünüyor ne de içerikler açılıyor."

- **Sebep test düzeniydi, üründe bir hata değil.** Derleme, telefondaki mağaza sürümünün üstüne kuruldu. Uygulama canlı sunucunun oturum anahtarıyla yerel sunucuya gitti; yerel sunucu anahtarı tanımadı.
- **Çözüm:** Uygulama silinip yeniden kuruldu; onboarding'den temiz başladı.
- **Canlıda karşılığı yok:** Gerçek kullanıcı sunucu değiştirmiyor.

## Ekip kararlarının uygulamasında editörün gördüğü noktalar

- **Karar 3 (başlık "Beklemeden oku: 7 gün ücretsiz"):** Deneme süresi yalnız mağazadan biliniyor. Planlar yüklenmeden ve Android'de mağaza okunmadan sayı bilinmiyor. Başlık koşullu olmalı: süre biliniyorsa bu başlık, bilinmiyorsa sayısız hâli (ör. "Beklemeden oku"). Başlık uzayınca SE 3 büyük yazıda seçili plan yeniden kontrol edilir.
- **Karar 5 (bildirim düzeni kapalı):** Sunucu dalındaki tek commit geri alınır. "Yarın hatırlat" telefonun kendi bildirimi; etkilenmez.
- **Karar 7 (eski sürüm):**
  - 1.0.2 yolculuk ucunu hiç çağırmıyor; o kullanıcılara yolculuk atanmıyor. "Son açtığı durağa bak" yolu onlar için çalışmaz.
  - Editörün önerisi kararın ikinci kolu: istek metin kimliği taşımıyorsa eski sayım (yalnız sözlük dışı kelime sayılır), taşıyorsa yeni sayım. Ayrım tek alana bakar, sürüm numarası gerekmez.
  - 1.0.2 derlemesi yerel sunucuya karşı çalıştırılıp 402'yi düzgün karşıladığı doğrulanır.
- **Nassim'in itirazı (ilk geri alınacak parça onboarding sonu teklifi):** Bugün bu teklifi kapatmanın yolu yeni derleme ve mağaza incelemesi. Sunucudan açılıp kapanan bir anahtar eklenirse derlemesiz kapatılır. Kararlarda yok; editör eklenmesini öneriyor.
- **TestFlight sırası:** Sunucu canlıya çıkmadan derleme yolculuğu göstermez, eski kartlara düşer. Sunucu yayını Mehmet'te; yayınla birlikte yolculuk tabloları canlıya yazılır.

## Önerilen sıra (Mehmet onaylamadı)

1. Kelime kararı ("durak" yerine ne).
2. Bitiş ekranı tek geçiş: karar 2 + kapak + yeni kelime.
3. Karar 3: koşullu başlık, SE 3 büyük yazı kontrolü.
4. Karar 5: eski ilerleme sayfası geri, bildirim commit'i geri.
5. Karar 6: 44 satırlık betik (çalıştırılmaz).
6. Karar 7: eski sayım kolu + 1.0.2 doğrulaması.
7. Testler, SE 3 sürüşü, rapor.
8. Balon: ölçüm ve öneri.
9. Sunucu yayını ve `NextHook` yazımı (Mehmet), sonra TestFlight derlemesi, bir gün kullanım.
10. Yarım kalan çeviri işi (Mehmet bunu bu işlerden sonraya koydu).

## Ekipten ve Mehmet'ten beklenen kararlar

| # | Soru | Kim | Editörün önerisi |
|---|---|---|---|
| 1 | "Durak" yerine hangi kelime? | Mehmet (Paul'un önerisiyle) | "hikâye" |
| 2 | "Yolculuk sayfası" Profil'den açılan harita mı? | Mehmet | Öyle varsayıldı |
| 3 | Bitiş ekranında kapak nasıl yerleşsin; açıklama kısalsın mı? | Dieter | Kapak solda küçük, açıklama en çok iki satır |
| 4 | Balon bu pakete mi, sonrakine mi? | Mehmet (Nassim, Don) | Ölçüm ve öneri görüldükten sonra karar |
| 5 | Eski uygulama için eski sayım korunsun mu? | Kent | Evet; ayrım metin kimliğinin varlığıyla |
| 6 | Onboarding teklifine sunucudan kapatma anahtarı eklensin mi? | Nassim, Mehmet | Evet |
| 7 | "İlk gün 2 hak" takvim günü mü kalsın, ilk 24 saat mi olsun? | Ekip | Şimdilik değişiklik yok; not edildi |
| 8 | Harita için "eski düzen + kutularda kapak" hangi sürüme? | Ekip, Mehmet | Sonraki sürüm, önce taslak |
