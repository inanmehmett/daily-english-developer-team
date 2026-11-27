# İçerik üreticisine istek: 5 Ekim tam paketinin eksikleri

**Kimden:** Daily English uygulama ekibi · **Tarih:** 27 Kasım 2026
**Konu:** `TESLIM - TAM PAKET (5 Eki 2026)` içindeki 16–23 Eylül üretimi (159 okuma metni). Metinleri okuduk; gövdeler, kelime tabloları ve quizler tam. Paketi önümüzdeki hafta sisteme yüklüyoruz. Yayına alabilmemiz için aşağıdakilere ihtiyacımız var. Gövde metnine dokunulmasını **istemiyoruz**; istenenlerin hepsi üst bilgi (META) ve ek alanlar.
**Teslim biçimi:** tek tablo dosyası (CSV ya da md tablo), her satır bir metin, ilk sütun `Slug`. Mevcut paket dosyalarını yeniden yazmaya gerek yok.

## 1. Türkçe kart adı (159 metnin tamamı) — en öncelikli
Uygulamada kartta üst satırda İngilizce ad, altında **Türkçe ad** görünüyor. Paketteki `SubtitleTR` alanı İngilizce alt adın çevirisi ("Dinner at Ten → Saat onda akşam yemeği"); bizim ihtiyacımız metnin Türkçe **adı**. Yeni alan adı: `TitleTR`.
Kurallar (Mehmet'in ölçütleri, 25–26 Kasım'da kesinleşti):
1. **En çok 28 karakter** (boşluk ve noktalama dahil). Uygulama daha uzun adı kartta hiç göstermiyor. Her adın yanına karakter sayısını yazın.
2. Ad heyecan ya da duygu uyandırsın; Türkçesi eğreti durmasın; uydurma söz olmasın.
3. Ad metinle alakasız olamaz. Gerçek bir olayı anlatan metin masal gibi adlandırılmaz.
4. Türkçe ad İngilizce adın birebir çevirisi olmak zorunda değil, ama ikisi **aynı hikâyeyi** vaat etmeli. Kartta iki satır birlikte okunuyor; özel isim ve yer İngilizce satırda varsa Türkçe adda tekrarlanması gerekmez.
5. İngilizce ad yalnız bir özel isimse (Şahmeran, Gezellig, Hygge, Wabi-Sabi) Türkçe ad onun çevirisi sanılmamalı: ismi taşısın ya da ne olduğunu söylesin.
6. Ad metnin sonunu ya da sırrını söylemez (dizi bölümlerinde özellikle).
7. Kısalık için kalite feda edilmez: kısa ad, uzun adın sakat hâli olmamalı.
Örnekler (onaylanmış): "Gökten Amazon'a Düşen Kız", "Haritadan Silinen Ada", "İki Kez Kahvaltı Eden Ülke", "Baba Yaga ve Yürüyen Kulübe", "İtalyanlar Neden Konuşkan?". Reddedilmiş: "Kırık Teknede 41 Gün" (öyle bir söz yok), "Kratersiz Patlama" (uydurma), "3 Kilometreden Düşen Kız" (soğuk).

## 2. Türkçe ve İngilizce açıklama (78 metin: 16, 17, 18 Eylül teslimleri ve It Wasn't Always Like This)
Bu metinlerde yalnız `## SUMMARY (EN)` var; `DescriptionTR` ve `DescriptionEN` yok. Kurallar:
1. En çok iki üç cümle ve **200 karakter**; A1–A2 metinlerde **140 karakter**.
2. Tek zaman, en çok iki isim. Kurguda şimdiki zaman, gerçek olayda geçmiş zaman.
3. Metnin içinde olanı değil, metni açtıran soruyu yazar. Sonu söylenmez.
4. Yorum yok ("sıcak bir hikâye", "kitap dersini söylemez").
5. Okur metni okumadan anlayabilmeli. Gerçek olaysa gerçek olduğu anlaşılmalı.
19–23 Eylül metinlerinin açıklamaları bu kurallara göre gözden geçirilebilirse iyi olur; zorunlu değil, biz denetleyeceğiz.

## 3. Merak cümlesi (`NextHook`) (85 metin: 19, 21, 22, 23 Eylül teslimleri)
Bir önceki hikâye bitince "sıradaki hikâye" kartında görünen tek cümle. Türkçe, en çok 90 karakter, sonu söylemez. 16–18 Eylül metinlerindeki `NextHook` örnekleriyle aynı biçim.

## 4. Türkçe çeviri
Eski paketlerde her metnin `## TRANSLATION (TR)` bölümü vardı ve kayıtta o çeviri esas alınıyordu. Eylül paketinde yok.
1. Bilerek mi çıkarıldı; gerekçesi ne?
2. En azından **A1 ve A2 metinler** (97 metin, yaklaşık 32.000 kelime) için, aynı paragraf yapısıyla Türkçe çeviri istiyoruz. Bu seviyedeki okur cümle çevirisine en çok bakan okur.
3. B1 ve üstü için karar bizde; şimdilik istemiyoruz.

## 5. Kelime tablosunda seviye sütunu
Tablolar üç sütunlu (kelime, Türkçesi, metinden örnek). Kayıt aracı dördüncü sütunu bekliyor: `WordLevel` (A1–C2). Her kelime için seviye.

## 6. Küçük düzeltmeler
1. Kategorisi **"Cities"** olan dört metin (The Town Under the Rock, The Streets Under the Streets, The Bridge Was a Boat, The Pink City): sistemde bu kategori yok. Şunlardan biri: History, Travel, Culture.
2. İki A1 mini kitabın (Four Who Were Too Old, The Bird Who Was Wrong) 2.–5. bölümlerinde seviye ve kategori alanı boş; ilk bölümdekiyle aynı mı?
3. Aynı mini kitaplarda kapak tarifi yalnız birer bölümde var. Kitap başına tek kapak mı, bölüm başına mı?
4. **It Wasn't Always Like This** iki klasörde iki sürümle duruyor (`TESLIM - It Wasnt Always Like This (16 Eyl 2026)` ve `Teslim 16 Eyl 2026`); çatal metninin adı ve adresi farklı ("In Italy, the Fork Was Rude" / "Italy Called the Fork Rude"). Hangisi geçerli?

## 7. Yatay görsel tarifi (sonra, liste bizden gelecek)
Ana sayfa slaytı yatay görsel kullanıyor; kapak tarifleri yalnız dikey (3:4). Slayta çıkacak metinleri seçince listesini göndereceğiz; yalnız onlar için yatay tarif.

## İstemediklerimiz
- Gövde metinlerinde değişiklik (ses üretimi metne bağlı; metin kayıttan sonra donacak).
- Kulvar A/B klasiklerinin gövdeleri (ayrı iş, sonra).
- Yeni metin.
