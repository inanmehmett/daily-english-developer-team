# Sahiplenme verisi: profil, rozet, defter

**Tarih:** 21 Kasım 2026 · **Görev:** `ortak/editor_gorevi_2026-11-21_toplu.md`, bölüm I · **Hazırlayan:** editör
**Yöntem:** canlı veritabanı (salt okuma; yalnız müşteri hesapları, 365 kişi; kişisel bilgi yok) ve canlı kod. Dayanak: `2026-11-21_profil_ve_sahiplenme_mevcut_durum.md`.

## Özet

1. **Müşterilerin %89'u misafir** (324/365). Üye 41: e-posta 18, Google 14, Apple 9. Üyelerin 31'i misafirken üyeliğe geçmiş, 22'si kaydın ilk gününde.
2. **Kendi yüklediği profil resmi olan müşteri yok.** Resmi olan 7 kişinin 7'si de Google ile giriş yapmış; resim Google hesabından geliyor.
3. **Adını hemen herkes giriyor** (onboarding soruyor): 365'in 318'i. Biyografi yazan 1 kişi.
4. **Rozet bol, ama çoğu kendiliğinden düşüyor:** müşterilerin %56'sında en az bir rozet; en sık üçü İlk Kitap, İlk Quiz ve **Top 100** (83 kişi). Rozet sayfasını açan 102 kişi (%28).
5. **Defter sınırına çarpan 13 kişi**, 244 kez; hiçbiri satın almadı.
6. **Kendi bir şey ekleyenler 7. günde daha çok dönüyor** (%24 ile %11), ama bu büyük ölçüde zaten okuyan kişiler olmalarından; okuyanlar arasında fark küçülüyor (%27 ile %16). Az veri.

## 1. Misafir ve üye

| | iOS | Android | Toplam |
|---|---|---|---|
| Misafir | 201 | 123 | **324** |
| Üye: e-posta | 11 | 7 | 18 |
| Üye: Google | 5 | 9 | 14 |
| Üye: Apple | 9 | – | 9 |
| **Toplam** | 226 | 139 | 365 |

- Üyelerin 31'i **misafirken geçmiş** (ilerlemesi taşınmış), 10'u doğrudan üye olarak açılmış (Google 6, Apple 3, e-posta 1).
- **Misafirden üyeliğe geçiş günü** (kayıt günü = 0): 0. gün 22 · 1. gün 4 · 2. gün 1 · 5. gün 3 · 13. gün 1. Geçenlerin %71'i ilk gün geçiyor; sonra neredeyse hiç.
- Kaynak: giriş kayıtları (`AuditLogs`, `LoginSuccess`, yöntem `email_upgrade` / `google_upgrade` / `apple_upgrade`).

## 2. Profil resmi

- **Resmi olan 7 üye; hepsinin resmi Google hesabının resmi** (adresleri Google'ın resim sunucusu). Uygulamadan resim yükleyen müşteri: **0.**
- Misafirde resim yükleme kapalı; yüklemeye çalışan misafir kayıt ekranına gidiyor. **Bunu sayamıyorum:** uygulama, kayıt ekranının resim düğmesinden açıldığını kaydetmiyor. Eksik ölçü.
- Mevcut durum notundaki "Misafir resim yükleyemiyor; 'kimse yüklemiyor' gözleminin olası nedeni" doğru görünüyor: müşterinin %89'u misafir. Ama üyeler de yüklemiyor (41 üyeden 0).

## 3. Profil bilgileri

| | Misafir (324) | Üye (41) |
|---|---|---|
| Ad girmiş | 279 | 39 |
| Kullanıcı adı | – | 36 (aşağıya bakın) |
| Biyografi | 0 | 1 |
| İlgi alanı seçmiş | 310 | 31 |
| Öğrenme amacı | 307 | 30 |
| Öğrenme stili | 0 | 1 |
| "Profil herkese açık" | 324 | 39 |

- **Kullanıcı adı kullanıcı seçimi değil:** 41 üyenin 31'inde e-postanın @ öncesi, 5'inde e-postanın kendisi. Sunucu kayıtta otomatik üretiyor. Kendi kullanıcı adını seçtiği görülen müşteri yok.
- **"Profil herkese açık" varsayılan olarak açık** (sunucuda varsayılan `true`). 365 kişiden 363'ünde açık; kapatan 2. "Açan" sayılamaz; açık olması tercih değil varsayılan.
- Ad ve ilgi alanı onboarding'de soruluyor; doluluk oranı sahiplenme değil, onboarding'i bitirme göstergesi.

## 4. Rozetler

**Müşteri başına kazanılan rozet** (365): hiç 160 · 1 rozet 43 · 2–3: 78 · 4–6: 49 · 7 ve üstü 35. Ortanca 1, %90'lık 6, en çok 17.

**Hangi rozet kaç müşteride** (etkin 70 rozetin 24'ü kazanılmış):

| Rozet | Küme | Müşteri |
|---|---|---|
| İlk Kitap | Okuma | 182 |
| İlk Quiz | Quiz | 174 |
| **Top 100** | Sosyal | **83** |
| Çaylak | Rütbe | 81 |
| Gece Kuşu | Özel | 55 |
| Her Alanda | Gizli | 52 |
| 3 Gün Seri | Seri | 33 |
| **Top 50** | Sosyal | **25** |
| Geri Dönüş | Özel | 16 |
| Quiz Başlangıç | Quiz | 12 |
| Erken Kuş · Tatil Kahramanı | Özel | 10 · 10 |
| Haftalık Şampiyon | Sosyal | 8 |
| Meraklı · Gece Yarısı | Rütbe · Gizli | 6 · 6 |
| Pes Etmeyen | Gizli | 5 |
| Haftalık · Dikkatli Okuyucu | Seri · Performans | 4 · 4 |
| Seviye Lideri · İlk Kelime · Top 10 | Sosyal · Kelime · Sosyal | 3 · 3 · 3 |
| Hafta Sonu Savaşçısı | Özel | 2 |
| Okuma Başlangıç (10 metin) · Kelime Filizi (10 kelime) | Okuma · Kelime | 1 · 1 |

- **Okuma rozetinin ikincisi (10 metin) 1 kişide, kelime rozetinin ikincisi (10 kelime) 1 kişide.** Mevcut durum notundaki "eşikler tipik kullanıcıdan uzak" bulgusu sayıyla doğrulanıyor.
- **Sosyal rozetler neye göre veriliyor** (sunucu kodu, `BadgeService`): toplam XP'ye göre sıralama; liderlik tablosuyla bağı yok.
  - Top 100: en az 200 etkin kullanıcı varsa ve kişinin XP'si en az 100 ise, kendisinden çok XP'si olan 100'den az kişi varsa.
  - Top 50: en az 100 etkin kullanıcı ve en az 500 XP; Top 10: en az 50 etkin kullanıcı ve en az 1.000 XP.
  - "Etkin kullanıcı" sayısına test ve geliştirici hesapları da girebiliyor (aynı türden hesaplarla karşılaştırıyor; müşteri müşteriyle).
  - Sonuç: 363 müşteride XP'si 100'ü geçen hemen herkes Top 100'de. Sosyal rozetler toplam 122 kez verilmiş; kullanıcı hiçbir yerde bir sıralama görmüyor.
- **Rozet sayfasını açan:** 102 müşteri (%28) (rozet sayfası `badges/showcase` ucunu çağırıyor; profil sayfası çağırmıyor).
- **Rozet ayrıntısını açan: bilinmiyor.** Ayrıntı sayfası sunucuya istek atmıyor ve olay göndermiyor.
- **Rozet paylaşan:** 3 müşteri (3 paylaşım).

## 5. Okuma listesi ve haftalık özet

- **"Okuma listem"e ekleyen: 3 müşteri** (5 kayıt; 4 ekleme olayı). Liste her açılışta yükleniyor (314 kişide istek var), ama doldurulmuyor.
- **Haftalık özet sayfasını açan: 0.** Sayfa yalnız bildirimden açılıyor; haftalık özet bildirimi sunucuda gönderilen türler arasında yok (`2026-11-21_kanal_ve_bildirim_verisi.md` 2.2). Sayfa bugün kimseye ulaşmıyor.

## 6. Defter sınırı

| | Sayı |
|---|---|
| Sınıra çarpan müşteri | **13** |
| Toplam çarpma | 244 (kişi başı ortanca 8, en çok 64) |
| Çarptıktan sonra satın alma ekranını gören | 4 |
| Çarptıktan sonra satın al'a basan | 1 |
| Çarptıktan sonra satın alan | 0 |
| Ertesi gün dönen | 1 / 3 (ilk çarpması 2 günden eski olan 3 kişi; **az veri**) |

- Çarpma = deftere eklemeye sunucunun 403 dönmesi. Sınıra çarpanların çoğu son iki günde çarpmış; ertesi gün dönüş için veri henüz yok.
- 13 kişinin 9'u satın alma ekranını görmeden sınıra çarpmaya devam etmiş (bir kişi 64 kez). Sınır mesajının satın almaya götürüp götürmediği ayrıca bakılmalı.

## 7. Kendi bir şey ekleyenler ve 7. gün

"Kendi bir şey ekledi" = defterine en az bir kelime ekledi, okuma listesine en az bir metin ekledi ya da profil resmi var. Ad bu tanıma girmedi: onboarding soruyor, neredeyse herkes giriyor. 7 günü dolmuş 185 müşteri; "7. gün dönen" = kayıttan 7 gün sonra ya da daha sonra uygulamayı açan.

| | Kişi | 7. günden sonra dönen | En az bir hikâye bitiren | Bitirenler içinde dönen |
|---|---|---|---|---|
| Kendi bir şey ekledi | 63 | 15 (%24) | 49 | 13 (%27) |
| Eklemedi | 122 | 14 (%11) | 43 | 7 (%16) |

- Fark var ama çoğu okumadan geliyor: ekleyenlerin %78'i en az bir hikâye bitirmiş, eklemeyenlerin %35'i. Okuyanlar arasında da fark sürüyor (%27 ile %16). Neden-sonuç değil; **az veri** (dönen toplam 29 kişi).
- Ekleyenlerin neredeyse tamamı defterle ekliyor (okuma listesi 3 kişi, resim 0).

## 8. Liderlik tablosu

- **Ne zaman ve neden kapatıldı:** 10 Ekim 2026, `b39fdeaf`. Kod notu: "ilk haftalarda 'Anonim · 0' satırlarıyla dolu tablo 'kimse kullanmıyor' diye okunur"; aynı commit tablo sayfasına giden yolu da kapattı.
- **Açmak için:** uygulamada tek anahtar (`AppConfig.leaderboardEnabled`) ve yeni derleme. Sunucu tarafı çalışıyor.
- **Bugünkü müşterilerle tablo nasıl görünürdü:**
  - Toplam XP'si 0'dan büyük: 262 müşteri (ortanca 99, en çok 1.318).
  - Bu hafta XP kazanan: 140 müşteri; 13'ünün adı yok (tabloda "Anonim" görünür).
  - Tabloda herkesin ad + rütbe + XP'si görünür; profil resmi olan 7 kişi, kalanı baş harfle.
- Kapatma gerekçesi bugün kısmen geçersiz (haftalık tabloda 140 kişi var); adı olmayan satır oranı %9. Açılıp açılmayacağı ürün kararı.

## 9. Profil ve rozet sayfasının görüntüsü

Bu bölüm için yeni görüntü almadım. Var olan kareler: `ekran_2026-11-20/d49_surus_normal.png` ve derleme 49 sürüşündeki `260_profil*.png`, `261_profil_ayrinti.png` (simülatör çalışma klasöründe; misafir hesap). Üye hesabın profil görüntüsü yok: yerelde üye hesapla sürüş gerekiyor; kariyer taslağının görüntüleri bitince alırım.

## Mevcut durum notunda düzeltilecekler

- "Profil herkese açık" bir kullanıcı tercihi gibi yazılmış; **varsayılan olarak açık** (363/365).
- "Kullanıcı adı" alanı var ama kullanıcı seçmiyor; sunucu e-postadan üretiyor.
- "Haftalık özet: sayfa var (bildirimden açılıyor)": doğru, ama o bildirim gönderilmiyor; sayfa ölü.
- "Top 100 rozeti kazanılıyor (20 kişi)": bugün 83 müşteride; Top 50 de 25 kişide.
- Rozet sayısı: etkin 70 (12 rütbe + 58); müşterilerin kazandığı 24'ü.

## Eksik ölçüler

- Resim düğmesinden kayıt ekranına düşen misafir.
- Rozet ayrıntı sayfası açılışı.
