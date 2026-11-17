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

---

## Gözden geçirme (18 Kas 2026, 00:21) – "Doğru mu yapıyoruz, en iyisi bu mu?"

**Hüküm:** Yön doğru, plan olduğu hâliyle en iyisi değildi. Dört düzeltme yapıldı, bir de planın çözmediği asıl sınır yazıldı.

### 1. Planın kendi içinde çelişkisi (düzeltildi)
Tutmanın kaldıracı "ilk gün 2 metin bitirmek" dedik; aynı planda her dokunuşu sayan günde 25 sınırı koyduk. İlk metinde ortanca 16 dokunuş var; iki metin yaklaşık 32 eder. Yani sınır, tam da kalmasını istediğimiz kullanıcıyı ikinci metnin ortasında durdururdu (A2'de ilk metinde bile %45'i). **Düzeltme:** başlangıç yolculuğunun 4 durağında dokunuş haktan düşmez. Başlangıç tam tat; sınır ondan sonra ve diğer metinlerde.

### 2. Çok şey aynı anda (düzeltildi)
Sınırlar, yolculuk, görev listesi, bildirimler, harita, paywall: hepsi birden çıkarsa hangisinin işe yaradığı okunamaz ve büyük bir yapı hata riski taşır (onboarding'i kilitleyen tooltip hatası tek küçük değişiklikti). **Düzeltme:** yolculuk iki sürüme bölündü. Sürüm 1: yolculuk tanımı, ana sayfa kartı, bitiş ekranında "sıradaki", ilk gün 2 durak, başlangıç sonu teklifi, 3. durak kilidi, ölçüm. Görev listesi, bildirim eşlemesi, harita ve rütbe sürüm 2'ye, veriden sonra.

### 3. Hazır düzeltmeler rafta bekliyor
Müşterilerin en yeni sürümü 1.0.2+45. Satın alma vazgeçme nedenleri, paywall tetikleyicisi, küçük ekran düzeltmeleri, ilk hikâye sonu: hepsi yayınlanmamış kodda. Ölçemediğimiz her gün kayıp. **En değerli tek adım: 1.0.4'ü yayınlamak** (Mehmet). Yarım kalan 10 satın almanın 10'u yıllık plandaydı; 14 basandan 4'ü aldı. Bu kaçağın nedeni öğrenilirse satış, başka hiçbir şey yapmadan ikiye katlanabilir.

### 4. Ölçüm gerçeği
Günde yaklaşık 13 yeni müşteri var. Ertesi gün dönüşteki değişim 3–4 haftada okunur; satıştaki değişim (bugüne dek 4 satış) 2 haftada **okunamaz**. "2 haftada bir bakıp geri alırız" sözü dönüş için geçerli, satış için değil. Satış kararları aylar boyunca hipotez kalacak.

### 5. Planın çözmediği asıl sınır: hacim
Ayda yaklaşık 400 yeni müşteri × %1,5 satın alma = ayda 6 satış. Uygulama içi plan kusursuz işleyip oranı üçe katlasa ayda 18 satış. Bu, uygulamayı iyileştirir ama tek başına bir iş yapmaz. 140 bin takipçili hesaptan 20 günde 268 müşteri gelmiş; en büyük boşluk burada. Üstelik alıcıların çoğu kayıttan 3 dakika sonra aldı: satış uygulamada değil, uygulamaya gelmeden önce (Instagram'daki güvenle) yapılmış görünüyor (hipotez, 4 kişi).
**Sıra yine de doğru:** önce kova (tutma), sonra su (trafik). Ama kova için aylar beklenmez. **Kural:** sürüm 1 yayınlandıktan sonra ertesi gün dönüş %25'e yaklaşırsa ağırlık Instagram'dan uygulamaya geçişe kayar; 4 haftada kıpırdamazsa yolculuk fikri sorgulanır, üstüne yeni katman eklenmez.

### 6. Açık riskler
- Android: 93 müşteri, 0 satış. Mağazadaki gerçek satın alma akışı doğrulanmadı.
- A1'de 24 metin var; en kalabalık başlangıç grubu A1. Premium alan A1 kullanıcısına satılan içerik az.
- Editör büyük işlerde hata üretebilir; her sürüm gerçek cihazda, küçük ekranda ve büyük yazıda denenmeden çıkmaz.

**Başarı ihtimali (Nassim, açıkça):** Bu planla uygulamanın tuttuğunu ve sattığını *öğrenme* ihtimalimiz yüksek. Para kazanan bir işe dönüşmesi ise plana değil, tutma düzeldikten sonra Instagram kitlesinin uygulamaya taşınıp taşınamayacağına bağlı. Bunu bugünden kimse bilemez; 4–6 hafta içinde verinin söyleyeceği şey bu.
