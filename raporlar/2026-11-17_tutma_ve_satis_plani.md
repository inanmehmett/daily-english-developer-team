# Tutma ve satış planı – ekip kararı

**Tarih:** 17 Kasım 2026 · Tek geçiş; üyeler kurgusaldır. **Karar sahibi: ekip** (README, karar yetkisi). Bu belge bundan önceki açık soruları kapatır.

## 1. Veri neyi gösteriyor (uygulamanın kendi kayıtları)
| Bulgu | Sayı | Kaynak |
|---|---|---|
| İlk gün davranışına göre ertesi gün dönüş | hiç okumayan 3/58 · başlayıp bitirmeyen 7/63 · 1 metin bitiren 19/53 · 2+ bitiren 7/11 | 16 Kas neden kalmıyorlar |
| Müşterilerin %64'ü | en fazla 1 gün görülmüş | aynı |
| Alıcıların 3/4'ü | kayıttan sonraki 3 dk içinde, Premium şeridinden | 17 Kas satın alma anları |
| Ücretsiz sınırlar | fiilen kimseye değmiyor; tek temas kilit (69 kişi) | 17 Kas ücretsiz sınırlar |
| Yarım kalan satın almalar | 10/10 yıllık plan | 17 Kas satın alma anları |

**Sonuç:** İki ayrı kitle var. (1) Hemen alan: kapıyı açık görmesi yeter. (2) Kullanan: ücretsiz kullanıcı hiçbir eşiğe çarpmadığı için almıyor, ilk gün tek metinde kalırsa da gidiyor. Tutmanın kaldıracı: **ilk gün 2 metin bitirmek.** Satışın kaldıracı: **değer gördükten sonra gerçek bir eşik.**

## 2. Psikoloji: hangi mekanizmayı neden kullanıyoruz
| Mekanizma (kaynak) | Bizde ne demek |
|---|---|
| Davranış = motivasyon × kolaylık × tetik (BJ Fogg) | Her gün tek, küçük, belli bir iş: "bugünün durağı" (2–5 dk). Tetik: kullanıcının seçtiği saatte tek bildirim. |
| Alışkanlık döngüsü: tetik → eylem → ödül → yatırım (Nir Eyal, Hooked) | Tetik: bildirim/ana sayfa kartı · Eylem: durağı oku · Ödül: hikâyenin devamı, ilerleme · Yatırım: deftere eklenen kelime, ertesi gün tekrar olarak geri döner. |
| Açık kalan döngü akılda kalır (Zeigarnik) | Her durak, sıradakinin merak cümlesiyle biter (`NextHook`). Ücretsizde "yarın açılır". |
| Hedefe yaklaştıkça çaba artar (goal gradient, Kivetz 2006) | "Yolculuğun 3/4" ilerlemesi her ekranda; son durağa yaklaşınca çekim artar. |
| Verilmiş ilerleme (endowed progress, Nunes & Drèze 2006) | Onboarding'deki ilk okuma alıştırması yolculuğun ilk adımı sayılır: kullanıcı yola 0 ile değil 1 ile başlar. (Gerçekten okuduğu için dürüst.) |
| Karşılıklılık ve tepe anı (peak-end) | Ana teklif, başlangıç yolculuğu bitip ilerleme kartı gösterildiği anda: "7 gün ücretsiz dene". |
| Eşik anında değer görünür olur | Teklif yalnız kullanıcının bir şeyi gerçekten istediği anda: kilitli durak, 25 kelime bitti, 15 kelime doldu. |

**Kullanmadıklarımız (README madde 9):** sahte geri sayım, "kaybedeceksin" dili, gizli ret düğmesi, 09–21 dışı bildirim.

## 3. Kararlar (ekip, kesin)
**Tutma**
1. **İlk gün 2 durak açık**, sonra ücretsizde günde 1. Birinci durak bitince bitiş ekranı doğrudan "Sıradaki durak" der (bekleme yok); ikinci durak bitince "Yarın açılır".
2. **Ana sayfanın ilk kartı "Senin yolculuğun · Bugünün görevleri":** durak → kelime tekrarı → günün quizi; tek düğme "Sıradaki görev".
3. **Seri ve 7 gün sözü:** Günün görevlerinden biri tamamlanınca gün sayılır. Durak yoksa (bekleme ya da kilit), kelime tekrarı günü kurtarır; söz tutulur.
4. **Bildirim günde en çok 2:** okuma saatinde görev çağrısı; akşam yalnız gün tamamlanmadıysa "bugün 1 durak kaldı". Diğer türler bu ikisine eşlenir, geri kazanım haftada en çok 1.
5. **Harita:** "Okuma Yolculuğun" sayfası yolculuk haritası olur; rütbe adları kalkar, seviye (A1, A2…) ve duraklar görünür. Tek ilerleme dili.
6. **İçerik:** Durak sırası ve 32 sıradaki cümlesi `raporlar/2026-11-17_ilk_uc_yolculuk_ve_kancalar.md`'deki gibi. Canlıya yazmak Mehmet'in tek onayıyla, yedekli.

**Satış**
7. **Premium şeridi baştan görünür** (V8 geri alındı). Şerit, profil ve kilitli içerik teklif sayılmaz.
8. **Satış anları:** (a) başlangıç bitince ilerleme kartı + 7 gün deneme, (b) her yolculuğun 3. durağı kilitli, (c) çeviri sınırı (her dokunuş sayılır, günde 25), (d) defter sınırı (ilk günden 15), (e) kilitli içeriğe dokunma. Ekranı kesen teklif günde en çok 1.
9. **Paywall:** SE 3 ve büyük yazı hatası düzeltilir; yıllık + deneme varsayılan kalır, aylık görünür; vazgeçme nedenleri 1.0.4'teki kayıtlarla okunur, 2 hafta sonra varsayılan plan yeniden değerlendirilir.
10. **Ücretsiz bütçe:** başlangıç 4 + her yolculuğun ilk 2 durağı; günde 1 açma.

## 4. Ölçü ve geri alma
| Ölçü | Bugün | Hedef (yayından 4 hafta sonra) |
|---|---|---|
| İlk gün 2+ metin bitiren yeni kullanıcı | ölçülecek (11/166 civarı) | ×2 |
| Ertesi gün dönüş (yeni müşteri) | ~%15–20 | %25 |
| Deneme başlatma / yeni kullanıcı | ölçülecek | ölçülüp sabitlenecek |
| Ödeyen abone | 3 aktif | +5 |

Kural: 2 haftada bir okunur. Ertesi gün dönüş belirgin düşerse önce çeviri sınırı gevşetilir; satış artmazsa satış anları yeniden sıralanır. Sayılar küçük; her okuma hipotezdir.

## 5. Nasıl yapılır (editör, üç adım)
1. **Hemen (1.0.4/1.0.5):** V8 geri alma ve tetikleyici (hazır, `fix/paywall-trigger-attribution`) + ücretsiz sınırlar (`ortak/editor_gorevi_2026-11-17_ucretsiz_sinir_uygulama.md`).
2. **Yolculuk çekirdeği:** `ortak/editor_gorevi_2026-11-17_yolculuk_uygulama.md`.
3. **Bildirim eşlemesi ve görev listesi** aynı belgenin 3. bölümü.

## İtirazlar
- **Nassim:** 2+ metin bulgusu 11 kişiden geliyor; ilk gün 2 durağı açmak ucuz bir deney, ama sonuç ölçülmeden ders sayılmaz.
- **Paul:** Sınırları daraltmak A2 okuyucusunu en çok etkiler (ilk metinde 25'e sığan %55); A2 ertesi gün dönüşü ayrıca izlenecek.
