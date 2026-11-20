# Son hâl: "Senin Yolculuğun" sayfası ve kelime balonu – arayüz ve deneyim değerlendirmesi

**Tarih:** 20 Kasım 2026, 18:50 · Tek geçiş; üyeler kurgusaldır. **İsteyen:** Mehmet ("Son hâlimiz ne? Görsel olarak incele, ekibe sun; UI ve UX sorumluları değerlendirsin.")
**İncelenen:** `raporlar/ekran_2026-11-20/yolculuk_pano.png` (dört kare, SE 3), `taslak_balon_uc_secenek.png`; editörün notları `raporlar/2026-11-20_editor_durum_raporu.md` Ek 2.

## 1. Son hâl (özet)
| | Durum |
|---|---|
| Sunucu | Yolculuk, ödeme ve iade düzeltmeleri canlıda |
| 1.0.4 derleme 48 | TestFlight'ta; Mehmet deniyor |
| Derleme 49'a girecek, kodu biten | Yolculuk sayfası (T11), kart bağlantısı (T12), uygulama içi iptal (T9), uygulama dışı promosyon (T10), misafir kurtarma, yorum ekranı (üç gerçek yorum) |
| Karar bekleyen | Balon: A, B ya da C (T13); yorum ekranı taslağına "olur" |
| Eksik | Yolculuk sayfası gerçek sunucu verisiyle telefonda baştan sona sürülmedi |

## 2. "Senin Yolculuğun" sayfası
**İyi olanlar (Dieter, Don):**
- Kapaklar büyük ve gerçek; sayfa ilk bakışta "kitaplarım" diyor. Mehmet'in "görsel olarak doysunlar" isteğini karşılıyor.
- Sıradaki hikâye açıkça ayrışıyor: turuncu çerçeve, "SIRADAKİ" etiketi, daha büyük kapak. Okunan ✓ ile, gelecek olanlar soluk.
- Altta tek düğme; ne yapılacağı tartışmasız. İlk hikâye düğmenin hemen üstünde.
- Yol aşağıdan yukarı; kariyer sayfasıyla aynı dil (tırmanış).
- Büyük yazıda taşma yok.

**Düzeltilmesi gerekenler:**
| # | Gözlem | Kim | Öneri | Önem |
|---|---|---|---|---|
| S1 | **4. kare:** sıradaki hikâye yarın açılacakken ekrandaki tek düğme "Premium'la şimdi oku". Ücretsiz kullanıcıya yapacak başka bir şey gösterilmiyor | Don | Kuralımız: teklif olan her ekranda ücretsiz yol aynı görünürlükte. Düğmenin üstüne ya da altına ikinci yol: "Yarın hatırlat" (bitiş ekranındakiyle aynı) ve tek satır "Sıradaki hikâye yarın seni bekliyor." | **Yayından önce** |
| S2 | Üstteki ad etiketi ("Başlangıç · 1/4") içeriğin üstünde yüzüyor; büyük yazıda kapağın üstüne biniyor (3. kare), en üstteki kapak durum çubuğunun altında yarım kesiliyor | Dieter | Üstte sabit, zemin renginde ince bir başlık alanı; içerik onun altından kayar. Etiket hiçbir kapağa binmez | **Yayından önce** |
| S3 | İlk açılışta sayfa sessiz: kullanıcı teklif ekranından çıkıp bir haritaya düşüyor, karşılayan bir cümle yok | Don, Paul | İlk açılışa özel, başlığın altında tek satır: "{ad}, yolculuğun burada başlıyor." Sonraki açılışlarda görünmez | Yayından önce (tek satır) |
| S4 | Gelecek hikâyelerin etiketleri (ad, süre) soluk gri; devre dışı düğme gibi okunuyor | Dieter | Kapak soluk kalsın, ad tam koyulukta olsun; "gelecek" hissini kapak verir | Küçük |
| S5 | Bütün hikâyelerde "Yaklaşık 3 dk" yazıyor (örnek veri mi, gerçek mi?) | Nate | Gerçek veriyle sürüşte doğrulansın | Doğrulama |
| S6 | Sayfa gerçek sunucu verisiyle telefonda sürülmedi; koyu tema yok | Kent | Derleme 49 sürüşünde gerçek veriyle; koyu temada açık kalması kabul | **Yayından önce** |
| S7 | Yolun sonunda "sıradaki yolculuk" yok; sayfadan kariyere geçiş yok | Steve | Sonraki sürüm (`raporlar/2026-11-20_ingilizce_yolculugu_incelemesi.md`) | Sonra |

## 3. Kelime balonu (taslak, gerçek ölçülerle)
| | straight | mountains | carries | Değerlendirme |
|---|---|---|---|---|
| **A** tür satırında küçük bağlantı | 185 pt · "Cümle ›" | 234 pt · **bağlantı yok** | 293 pt · "Cümleyi çevir ›" | En dar; ama aynı şey üç ayrı biçimde görünüyor (kısa etiket, uzun etiket, hiç). Don: tutarsız gösterge, göstergesizlikten kötü |
| **B** düğme sütununda simge | 223 pt | 272 pt | 293 pt | Her kelimede aynı yerde, aynı biçimde. Metne dokunmuyor. Bedeli 38 pt ve simgenin öğrenilmesi |
| **C** bugünkü | 287 pt | 293 pt | 293 pt | Mehmet'in şikâyet ettiği hâl; "ayrıca"yı iki kelimede siliyor |

**Ekip önerisi değişti: B.** A'yı önermiştim; gerçek ölçüler A'nın kelimelerin önemli bir kısmında bağlantıyı gösteremediğini ortaya koydu.
- **Dieter:** B'de üç eylem (dinle · çevir · ekle) yan yana, tek sırada; anlam balonun kahramanı olarak kalıyor. En temiz hâl bu.
- **Don:** Yazısız simge zayıf göstergedir; kabul etmemin şartı öğretilmesi: ilk hikâyedeki ipucu ve onboarding satırı zaten var. Ek olarak, kullanıcı cümle çevirisini hiç kullanmadıysa ilk üç balonda simgenin altında küçük "cümle" yazısı görünsün, bir kez kullanınca kalksın. Olmazsa iki hafta ölçeriz: kullanan oranı %22'den yükselmiyorsa yazılı hâle döneriz.
- **Paul:** "ayrıca: dağ gibi bir şey" gibi ikincil anlamlar bilgi taşımıyor ve balonu genişletiyor. Bu, balon tasarımının değil içeriğin işi: basit adlarda ikincil anlamın gösterilmemesi çeviri taramasına eklenir.
Seçim Mehmet'in; seçilenin eni ve boyu testle kilitlenir.

## 4. Sıra
1. Mehmet: balon seçimi (öneri B), yorum ekranına "olur".
2. Editör: S1, S2, S3, S6 + seçilen balon → derleme 49, tek tam sürüş (gerçek veriyle).
3. Mehmet: kontroller → mağaza.
4. Editör (salt okuma, yayını geciktirmeden): `ortak/editor_gorevi_2026-11-20_ilerleme_verisi.md`.
