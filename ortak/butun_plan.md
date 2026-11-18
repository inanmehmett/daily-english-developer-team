# Bütün plan: tut ve sat – tek yol

**Tarih:** 18 Kasım 2026 · **Karar sahibi:** ekip · **Mehmet'in yönergesi:** "Kullanıcıyı tutacağız ve para alacağız. İkisi birbirinden bağımsız değil; bütün olarak düşün."
**Dil (18 Kas, cihaz testi):** kullanıcıya görünen kelime "durak" değil **"hikâye"**; bu belgedeki "durak" ekibin iç terimidir. Var olan bir ekranın görünümü Mehmet taslağı görmeden değiştirilmez. Kararlar: `raporlar/2026-11-18_cihaz_geri_bildirimi_kararlar.md`.
**Yolculuk sayfası (18 Kas toplantısı):** kariyer ve okuma yolculuğu tek sayfa ("Okuma Yolculuğun"); yol hikâyelerden, rütbe ve seviye üstte unvan, rütbe mantığı değişmez; Sürüm 1'de eski sayfa, birleşik sayfa balon sürümünden sonra. Karar 4 hafta veri gelmeden yeniden açılmaz: `raporlar/2026-11-18_yolculuk_sayfasi_toplantisi.md`.
Bu belge tek kaynaktır. Ayrıntılar: `raporlar/2026-11-17_tutma_ve_satis_plani.md`, `raporlar/2026-11-18_odeme_alma_plani.md`, `ortak/okuma_yolu_sistemi.md`. Çelişki olursa bu belge geçerlidir.

## Tek fikir: her bitişte iki kapı
Kullanıcının her adımı bir durakla biter ve her bitişte iki kapı vardır:
- **"Yarın devam et"** → geri gelir (tutma).
- **"Premium'la şimdi devam et"** → öder (satış).

İkisi de bizim için kazanç; kaybettiğimiz tek kullanıcı, ikisinden de geçmeyen. Bekleme, hem geri dönmenin hem ödemenin sebebidir. Bu yüzden tutma ve satış ayrı özellikler değil, aynı ekranın iki düğmesi.

**Tek ölçü:** yeni müşteri kayıttan sonraki 48 saat içinde **ya döndü ya ödedi** mi? (Bugün: ertesi gün dönüş ~%15–20, ödeme %1,5.) Hedef: %35.

## Kullanıcının yolu
| An | Kullanıcı ne görür | Tutma işi | Satış işi |
|---|---|---|---|
| **0. dakika** – onboarding sonu | "{ad}, yolculuğun hazır": 4 durağın adı | Sahiplik: plan onun | Teklif yolculuğu satar: "7 gün ücretsiz: bütün yolculuk bekleme olmadan" / "Ücretsiz başla: günde bir durak" (iki düğme aynı ekranda) |
| **İlk oturum** – durak 1 | Okuma; dokunma serbest | İlk metni bitirmek (bitirenin dönüşü 19/53, bitirmeyenin 7/63) | Premium şeridi görünür |
| Durak 1 bitişi | "Yolculuğun 1/4" + sıradaki durağın merak cümlesi + "Sıradaki durak" | İlk gün 2 metin (7/11 dönüyor) | — (kesme yok; akış bozulmaz) |
| Durak 2 bitişi | "2/4 · Sıradaki yarın açılır" | **Kapı 1:** yarın {saat}'te hatırlat | **Kapı 2:** "Premium'la şimdi oku" |
| **2.–3. gün** | Bildirim: "Durağın açıldı: {ad}" → durak 3, 4; defterindeki kelimelerin tekrarı | Doğru haber, gerçek sebep | Her bitişte sakin iki kapı |
| **Başlangıç bitince** | İlerleme kartı: 4 durak, {n} kelime, {n} gün | Başarı duygusu, yeni yolculuk görünür | **Ana teklif:** 7 gün deneme |
| **4. gün ve sonrası** | Seviye yolculuğu: 2 durak ücretsiz, 3. kilitli; dokunma 25/gün, defter 15 | Günde bir durak, seri | Kilit, dokunma ve defter eşiği: istediği anda teklif |
| **Deneme / Premium** | "Premium açıldı: yolculuğun bekliyor" → doğrudan sıradaki durak | **Ödeyeni tutmak:** deneme içinde en az 3 durak okutmak (hiç okumadan deneme başlatan iptal etti) | Deneme bitmeden 2 gün önce dürüst hatırlatma + okuduklarının özeti |
| **Satın al'a basıp vazgeçen** | Ekran kapanmaz: "Aylık planla başla" · ertesi gün tek hatırlatma | — | Ödeme adımındaki 10/14 kaçak |

## Kurallar
- Bir ekranda tek ana eylem; teklif olan her ekranda ücretsiz yol aynı görünürlükte.
- Ekranı kesen teklif: ilk oturumda en çok iki (onboarding sonu, durak 2 bitişi), sonra günde bir. Şerit, kilit ve bitiş ekranındaki ikinci kapı kesme sayılmaz.
- Sahte aciliyet, geri sayım, utandıran ret yok (README madde 9).
- Sayılar yalnız doğru olanlar; fiyat mağazadan.

## Yapım sırası: konuya göre değil, kullanıcının zamanına göre
Müşterilerin %64'ü en fazla bir gün görülüyor. Bu yüzden önce ilk oturum.
| Sürüm | Kapsadığı an | İçerik |
|---|---|---|
| **1.0.4** (hazır) | — | Ölçüm, tetikleyici, vazgeçme nedeni. Mehmet yayınlar. |
| **Sürüm 1 – ilk oturum** | 0. dakika → durak 2 bitişi | Yolculuk tanımı ve atama; onboarding sonu teklif; ana sayfa yolculuk kartı; bitiş ekranı (ilerleme, merak cümlesi, iki kapı); ilk gün 2 durak; paywall açıklığı, ikinci yol, küçük ekran; ücretsiz sınırlar (başlangıç istisnasıyla); kilitli içerik ekranı; deneme başlatanı durağa götürme; olaylar |
| **Sürüm 2 – ilk hafta** | 2.–7. gün | "Durağın açıldı" bildirimi; vazgeçene hatırlatma; başlangıç sonu ilerleme kartı ve ana teklif; 3. durak kilidi; sınır ekranları; deneme içi yönlendirme ve bitiş hatırlatması |
| **Sürüm 3 – sonrası** | 2. hafta+ | Görev listesi, kelime tekrarı, harita ve rütbe, bildirim düzeni |

Her sürümden sonra aynı tablo okunur (Nate): 100 yeni müşteride teklif gören, durak 1 ve 2'yi bitiren, 48 saatte dönen ya da ödeyen. Bir sürüm ölçüyü kıpırdatmıyorsa sonraki sürüm üstüne eklenmez; önce neden bakılır.

## İtirazlar
- **Nassim:** Sürüm 1 büyük. Tek akış olduğu için bölünmüyor, ama her parçası ayrı commit ve ayrı olayla ölçülmeli; onboarding'den okumaya geçiş (%81–85) düşerse onboarding sonu teklifi ilk geri alınacak parça.
- **Paul:** Başlangıç duraklarının merak cümleleri henüz yazılmadı; cümle yoksa bitiş ekranı metnin adı ve açıklamasıyla çalışmalı.
- **Sean:** Deneme süresi ve fiyat Mehmet'in alanı; vazgeçme nedeni fiyat çıkarsa öneriyle gelinir.
