# Gelen kullanıcıdan ödeme alma – ekip kararı

**Tarih:** 18 Kasım 2026 · Tek geçiş; üyeler kurgusaldır. **Görev tanımı (Mehmet):** "Mesele uygulamaya gelen kullanıcıdan ödeme alabilmek. Sizin işiniz bu." Bundan sonra ekibin birinci ölçüsü: **yeni müşteri başına satın alma.**

## Huni (uygulamanın kendi kayıtları, 261 müşteri)
| Adım | Kişi | Bir öncekinden geçen |
|---|---|---|
| Müşteri | 261 | |
| Paywall'u gördü | 93 | %36 |
| Satın al'a bastı | 14 | %15 |
| Satın aldı | 4 | %29 |

Üç kaçak, büyüklük sırasıyla:
1. **Ödeme adımı:** basan 14 kişinin 10'u tamamlamadı; 10'u da yıllık plandaydı. Aldıkları an istekli olan insanları kaybediyoruz.
2. **Teklifi görmeyenler:** müşterilerin %64'ü paywall'u hiç görmedi. Ve %64'ü en fazla 1 gün görülüyor: satış penceresi fiilen **ilk oturum.**
3. **Görüp basmayanlar:** %85.

Dış veri aynı şeyi söylüyor: abonelik uygulamalarında denemelerin ve ödemelerin çoğu kurulum günü başlıyor ([ContextSDK: ödemeli dönüşümlerin yarıdan fazlası 0. günde](https://contextsdk.com/blogposts/more-than-half-of-all-paid-conversions-happen-on-day-0); [RevenueCat verisi, iş uygulamalarında denemelerin %85'i 0. günde](https://cloud.substack.com/p/85-of-business-app-trials-start-on)). Bizde de 4 satışın 3'ü ilk 3 dakikada.

## Kararlar
**A. Ödeme adımındaki kaçak (en ucuz, en yüksek getiri)**
1. Satın alma iptal edilir ya da başarısız olursa paywall kapanmaz; tek cümleyle ikinci yol sunulur: "Yıllık fazla mı geldi? Aylık planla başla." (İndirim uydurulmaz; var olan aylık plan gösterilir.)
2. Paywall'da yıllığın **aylığa bölünmüş fiyatı** ve denemenin ne zaman, ne kadar ücrete döneceği açık yazılır ("7 gün ücretsiz, sonra … ; istediğin an iptal"). Belirsizlik vazgeçirir.
3. Satın al'a basıp tamamlamayan kullanıcıya ertesi gün tek hatırlatma: "Deneme hâlâ seni bekliyor." Bir kez; baskı dili yok.
4. İptal mi, hata mı kaydı (1.0.4'te hazır) okunur; hata çıkarsa (kart, mağaza hesabı) ayrı iş.

**B. İlk oturumda teklifi herkes görsün**
5. **Onboarding sonundaki teklif geri gelir.** "Planın hazır" ekranından hemen sonra: 7 günlük deneme, altında aynı büyüklükte okunur "Şimdilik ücretsiz devam et". 24 Eylül'de ilk okumaya ertelenmişti; bugünkü hiçbir müşteri onu görmedi, satın alanlar ise ilk dakikalarda aldı.
6. Premium şeridi baştan görünür (yapıldı). İlk metin bitişindeki teklif kalır.
7. İlk oturumda en çok iki ekran kesen teklif (onboarding sonu + ilk metin bitişi); sonraki günlerde günde en çok bir.

**C. Görüp basmayanlar**
8. Paywall'un ilk ekranında Premium'un ne açtığı sayılarla: "287 metin, sınırsız kelime, sınırsız defter". (Sayılar canlıdan gelir; yanlış söz yok.)
9. Kilitli içerik ekranı (69 kişi dokundu, 5'i bastı) aynı dille yeniden yazılır: kilitli metnin adı + "Premium'la şimdi oku" tek ana düğme.
10. Küçük ekran ve büyük yazıda seçili plan ve düğme birlikte görünür (engelleyici).

**D. Android**
11. Android'de 93 müşteri, 3 basış, 0 satış. Gerçek mağaza sürümünde satın alma akışı uçtan uca denenir (Mehmet'in cihazı gerekir).

## Sıra (değişti)
1. **1.0.4 yayını** (Mehmet): ölçüm ve hazır düzeltmeler.
2. **Satış sürümü:** A, B, C maddeleri + ücretsiz sınırlar. Küçük, tek odaklı.
3. **Yolculuk sürüm 1:** satış sürümünden sonra.
Gerekçe: satış penceresi ilk oturum; yolculuk ise dönen kullanıcıya satar. Önce büyük kaçak.

## Ölçü
Haftalık tek tablo (Nate): müşteri → paywall gördü → bastı → aldı; tetikleyiciye ve platforma göre. Hedef, satış sürümünden sonraki 100 yeni müşteride: paywall görme %36 → %80+, bastıktan sonra tamamlama %29 → %50. Satış sayısı küçük kalacağı için adım oranlarına bakılır.

## İtirazlar
- **Nassim:** Onboarding sonu teklifi bazı kullanıcıyı ilk okumadan önce kaçırabilir. Onboarding'i bitirip okumaya başlayanların oranı (bugün %81–85) düşerse teklif ilk metin sonrasına geri alınır.
- **Don:** İki yol aynı görünürlükte olmalı; "ücretsiz devam et" gizlenirse madde 9'u çiğneriz ve mağaza reddi riski doğar.
- **Sean:** Fiyat ve deneme süresi Mehmet'in alanı; kaçak nedeni fiyat çıkarsa öneriyle gelinecek.
