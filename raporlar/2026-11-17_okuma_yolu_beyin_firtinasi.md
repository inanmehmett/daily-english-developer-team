# Okuma yolu – beyin fırtınasının toparlanması

**Tarih:** 17 Kasım 2026 · Tek geçiş; üyeler kurgusaldır. **Durum: yön tartışması, karar Mehmet'in.**

## Mehmet'in ilkesi
Kullanıcı karar vermesin; uygulama onun yerine düşünsün. Açtığında, döndüğünde ne bulacağını net bilsin. Hipotez: karar yükü bırakmanın bir nedeni.
**Destekleyen veri (tek):** `2026-11-16_neden_kalmiyorlar.md` S5 – giden 16 kişi uygulamayı yeniden açıp hiçbir şey yapmadan çıkmış. Doğrudan kanıt değil, uyumlu bir işaret.

## Mehmet'in fikirleri, iki eksende
| Fikir | Seçim yükü | İlerleme birimi |
|---|---|---|
| Belirli sayıda kitaplık set, her gün bir okuma | Sıfır (set verilirse) | Gün |
| Sıralı seri / yolculuğu tamamlama | Sıfır | Metin |
| Tüm içerik tek sırada | Sıfır | Metin |
| Kur sistemi | Sıfır (kur ölçümle atanırsa) | Seviye |
| Tema rozeti (sağlık parçaları → sağlık rozeti) | Seçim gerektirir ya da kendiliğinden gelir | Tema |
Bunlar birbirinin alternatifi değil; bir iskelet (kur + sıra + gün) ve bir süs (tema rozeti) olarak birleşiyor.

## Ekibin ortak önerisi: atanmış kur, her gün bir okuma
1. Kur = CEFR bandı; kullanıcı seçmez, onboarding ölçümü atar.
2. Her kur sabit bir sıra (ör. 20–30 metin). Sırayı Paul seviyelendirir: kısa ve bitirilebilir başlar, kelimeler metinler arasında tekrar eder.
3. Ana sayfada tek kart: "Gün 7 · bugünün okuması". Döndüğünde hep aynı yerde aynı soru: bugünün metni.
4. Metin bitince: yarının metni görünür; o metinde bakılan kelimeler yarının kısa tekrarı olur.
5. Tema rozetleri yolun içinden kendiliğinden gelir (sağlık metinleri bitince sağlık rozeti); sırayı belirlemez.
6. Keşfet yerinde kalır ama varsayılan değil.
7. Kur sonu: seviye ölçümü; geçen sonraki kura.

## Üyeler
- **Steve:** Tek yol, atanmış. Seçim yalnız isteyen için, kenarda.
- **Paul:** Sıra pedagojik olarak kurulmalı, rastgele değil. Önce her seviyede kaç uygun metin olduğu sayılmalı; kur uzunluğu buna bağlı.
- **Don:** Açılışta sıfır karar. Ama tek kaçış hakkı olsun: "Bugün bunu değil" → uygulama başkasını verir.
- **Dieter:** Ana sayfa tek kart, tek düğme.
- **Sean:** Para tarafının en net teklifi bu olabilir: "A2 kurunu bitir". Kullanıcı ne aldığını bilir. İlk günler ücretsiz, kurun devamı Premium; 7 günlük deneme = kurun ilk 7 günü.
- **Nate:** Ölçüler: bugünün okumasını bitirme oranı ve ertesi gün dönüş, sürüme göre.
- **Nassim:** "Karar yükü yüzünden gidiyorlar" kanıtlanmadı. Tek metin dayatılır ve sevilmezse alternatifsiz kullanıcı gider; kaçış hakkı şart. "Günde bir" istekli okuru kısıtlamasın: bitirince "bir tane daha" serbest olsun.

## Mehmet'ten beklenen kararlar
1. Günde bir okuma mı, bitirince "bir tane daha" serbest mi?
2. Kur uzunluğu (önce seviye başına metin sayısı çıkarılacak).
3. Ücretsiz/Premium sınırı kurun neresinde?
4. "Bugün bunu değil" kaçış hakkı olsun mu, günde kaç kez?

---

## Tur 2 (14:36): "A2 kurunu bitir" çok geniş bir vaat

**Mehmet'in itirazı:** Kur vaadi geniş; tema bazlı kurlara içerik bulmak zor; seviye + kur, kurun geçerliliği ve kapsamı nasıl çözülecek? Yoksa vaat etmeyen bir yolculuk mu?

**Ekibin cevabı: "kur" değil, "yol". Seviye vaat değil, filtre.**
- **Paul:** CEFR dört beceri (okuma, dinleme, konuşma, yazma). Biz yalnız okumayı ölçüyoruz. "A2'yi bitirdin" diyemeyiz; diyebileceğimiz "A2 düzeyindeki metinleri okuyabiliyorsun". Kur, müfredat ve kazanım vaadi taşır; bunu karşılayacak içerik ve ölçüm yok.
- **Nassim:** Okurun hissetmediği bir vaat güveni bitirir (README madde 9: dürüstlük).
- **Sean:** Soyut vaat ("A2 bitir") somut vaatten ("7 günde 7 kısa hikâye") daha az satar. Sayılabilen şeyi vaat et.
- **Don:** İnsanlar bitirebildikleri küçük birimleri sever. Bütün yol açık uçlu olabilir; ama her hafta kapanmalı.
- **Paul (tema):** Tema başına ayrı yol içerik açısından yürümez. Tema, yolun içinde kendiliğinden gelen rozet olsun; yeterli içerik olan temada ileride kısa, isteğe bağlı bir koleksiyon olabilir.
- **Nate (geçerlilik):** Bir metnin yola uygunluğu veriyle sınanır: 50 kelimede bakış sayısı ve bitirme oranı. Uymayan metin yoldan çıkar ya da yer değiştirir.

**Önerilen yapı:**
1. **Okuma yolu:** kullanıcının seviyesine göre tek, sıralı, açık uçlu yol. Kullanıcı seçmez.
2. **Hafta (bölüm):** 7 metinlik, bitirilebilir birim; her gün bir metin. Vaat yalnız sayılabilen şey: "Bu hafta 7 kısa hikâye, yaklaşık X yeni kelime."
3. **Seviye geçişi:** vaat değil. Yeterli hafta bitirene isteğe bağlı okuma seviyesi ölçümü; geçen bir üst seviyedeki yola geçer.
4. **Tema:** rozet olarak, sırayı belirlemeden.
5. **Premium:** ilk hafta ücretsiz (7 günlük denemeyle örtüşür), sonrası Premium.

**Önce bilinmesi gereken:** her seviyede kaç uygun metin var (kaç hafta çıkar), kaçı ücretsiz, kaçı dizi.
