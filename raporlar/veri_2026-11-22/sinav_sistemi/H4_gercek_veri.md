# H4 – Gerçek kullanıcı verisi, soru bazında

**Kaynak:** canlı veritabanı, 22 Kasım 2026, salt okuma. **Yalnız müşteri hesapları** (ekip, test ve promosyon hesapları hariç). Kişisel bilgi yok. Dönem: 2026-10-31 – 2026-11-21.

## Özet
- **"Seviyeni yeniden ölç":** 118 tur, 107 müşteri. Hepsi kullanıcının kendi başlattığı tur olarak kayıtlı (`Trigger = User`): ana sayfa kartı da bugüne kadar aynı işareti gönderiyordu, ikisi ayırt edilemiyor. İlk yerleştirme (onboarding) diye ayrı bir tur yok: onboarding'deki "emin değilsen ölçelim" bağlantısı aynı testi açıyor.
- **"Seviyeni belgele":** müşterilerden **0** deneme. Toplam 3 deneme var, üçü de ekip ve test hesabı (biri Mehmet'in 21 Kasım denemesi: B2, puan 62). Soru bazında müşteri verisi yok.

## 1. Turların sonu
| Durum | Tur |
|---|---|
| yarıda (açık) | 11 |
| tamamlandı | 106 |
| güvenilmez (okunmadan geçildi) | 1 |

Tamamlanan turların süresi: ortanca 3,2 dk, en kısa 1,1 dk, en uzun 1292,6 dk; 13 tur 2 dakikanın altında, 3 tur 10 dakikanın üstünde (uygulama arka planda kalmış olabilir).

### Yarıda kalan turlar hangi adımda kaldı
| Adım | Tur |
|---|---|
| kelime taramasında (30 kelime bitmeden) | 5 |
| 1. parçada | 4 |
| 2. parçada | 2 |

Not: yarıda kalan tur kapanmıyor; kullanıcı döndüğünde kaldığı yerden sürüyor. "Yarıda" = 22 Kasım itibarıyla bitmemiş.

## 2. Kelime taramasının kestirdiği bant ve sonuç
Tarama parça aşamasının başlangıcını seçer; sonucu parçalar belirler. Satır: taramanın bandı. Sütun: turun sonucu.

| Tarama \ Sonuç | Pre-A1 | A1 | A2 | B1 | B2 | Toplam |
|---|---|---|---|---|---|---|
| A1 | 3 | 17 | 11 | 2 | 5 | 38 |
| A2 | · | 7 | 18 | 1 | 1 | 27 |
| B1 | · | · | 27 | 7 | · | 34 |
| B2 | · | · | 2 | 2 | 1 | 5 |
| C1 | · | · | · | 2 | · | 2 |

Sözde kelimelere "biliyorum" deme oranı (yanlış alarm): 81 turda 0; 29 turda 0 ile 0,5 arası; 3 turda 0,5 ve üstü (tarama güvenilmez sayılır, parça A1'den başlar). Ortalama 0,06.

**Kelime bazında veri yok:** hangi kelimeye "biliyorum" dendiği kaydedilmiyor; yalnız sunulan kelimeler, kestirilen bant ve yanlış alarm oranı tutuluyor. Kelimelerin zorluğu bu veriyle sınanamaz.

## 3. Ölçümden önceki ve sonraki seviye
Seviye geçmişi kaydından (`UserLevelHistories`, kaynak: yerleştirme), müşteri: 106 kayıt. Satır: önceki seviye. Sütun: yeni seviye.

| Önce \ Sonra | Pre-A1 | A1 | A2 | B1 | B2 | C1 | C2 | Toplam |
|---|---|---|---|---|---|---|---|---|
| A1 | 3 | 21 | 46 | 11 | 5 | · | · | 86 |
| A2 | · | 2 | 6 | 2 | 1 | · | · | 11 |
| B1 | · | · | 5 | 1 | 1 | · | · | 7 |
| B2 | · | 1 | 1 | · | · | · | · | 2 |

Yükselen 66, aynı kalan 28, **düşen 12**.

## 4. Parça ve soru bazında
Yalnız puanlanan parçalar (okunmadan geçildiği için reddedilenler hariç). "Doğru" sütunları sırasıyla 1., 2., 3. boşluk.

| Seviye | Parça | Gören tur | Ortalama puan (3 üzerinden) | 1. boşluk | 2. boşluk | 3. boşluk | Okunmadan geçildi |
|---|---|---|---|---|---|---|---|
| A1 | 50 | 8 | 1,88 | 2/8 | 5/8 | 8/8 | 0 |
| A1 | 53 | 8 | 2,50 | 8/8 | 7/8 | 5/8 | 0 |
| A1 | 54 | 12 | 2,75 | 12/12 | 11/12 | 10/12 | 0 |
| A1 | 55 | 7 | 2,57 | 7/7 | 7/7 | 4/7 | 0 |
| A1 | 56 | 6 | 2,50 | 5/6 | 5/6 | 5/6 | 0 |
| A1 | 57 | 11 | 2,64 | 10/11 | 10/11 | 9/11 | 0 |
| A2 | 32 | 17 | 2,24 | 9/17 | 16/17 | 13/17 | 0 |
| A2 | 33 | 16 | 2,25 | 13/16 | 16/16 | 7/16 | 0 |
| A2 | 52 | 16 | 2,19 | 15/16 | 11/16 | 9/16 | 1 |
| A2 | 58 | 16 | 1,88 | 13/16 | 12/16 | 5/16 | 0 |
| A2 | 59 | 17 | 2,00 | 15/17 | 4/17 | 15/17 | 0 |
| A2 | 60 | 14 | 1,93 | 12/14 | 10/14 | 5/14 | 0 |
| B1 | 37 | 12 | 1,75 | 8/12 | 8/12 | 5/12 | 1 |
| B1 | 38 | 14 | 1,29 | 12/14 | 1/14 | 5/14 | 0 |
| B1 | 39 | 18 | 0,72 | 3/18 | 7/18 | 3/18 | 0 |
| B1 | 40 | 10 | 0,90 | 2/10 | 3/10 | 4/10 | 1 |
| B1 | 41 | 15 | 0,93 | 3/15 | 6/15 | 5/15 | 0 |
| B1 | 42 | 12 | 2,33 | 10/12 | 10/12 | 8/12 | 1 |
| B2 | 43 | 3 | 0,67 | 0/3 | 0/3 | 2/3 | 0 |
| B2 | 44 | 0 | – | – | – | – | 0 |
| B2 | 45 | 1 | 0,00 | 0/1 | 0/1 | 0/1 | 1 |
| B2 | 46 | 4 | 1,25 | 2/4 | 2/4 | 1/4 | 0 |
| B2 | 47 | 2 | 1,50 | 1/2 | 1/2 | 1/2 | 0 |
| B2 | 48 | 4 | 1,00 | 1/4 | 1/4 | 2/4 | 0 |

Seviye toplamı (doğru boşluk / sorulan boşluk): A1 130/156 (%83) · A2 200/288 (%69) · B1 103/243 (%42) · B2 14/42 (%33)

Veri azken okuma kuralı: bir parçayı 10'dan az tur gördüyse oranı yorumlamayın. Sorunun kendisi için `H3_soru_bankalari.md` içindeki `s<numara>` ile eşleştirin (boşluk sırası aynı).

## 5. Parça puanlarının dağılımı (seviyeye göre)
| Parçanın seviyesi | 0/3 | 1/3 | 2/3 | 3/3 | Toplam |
|---|---|---|---|---|---|
| A1 | 0 | 6 | 14 | 32 | 52 |
| A2 | 2 | 17 | 48 | 29 | 96 |
| B1 | 17 | 35 | 19 | 10 | 81 |
| B2 | 5 | 5 | 3 | 1 | 14 |

Kural hatırlatması: 3/3 bir üst seviyeye taşır, 0/3 bir alta indirir (ilk parçadaysa önce bir alt seviyeden teyit parçası), 1–2/3 aynı seviyeden ikinci parça ister.
