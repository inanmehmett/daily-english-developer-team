# Editör görevi – satış kanalı ve bildirim verisi (salt okuma)

**Tarih:** 21 Kasım 2026 · **Dayanak:** `raporlar/2026-11-21_satis_kanali_ve_bildirim_toplantisi.md` · **Öncelik:** yayın işlerinden sonra; kod ve veritabanı değişikliği yok.
Canlıya salt okunur bağlan; yalnız `AccountKind='customer'`; kişisel bilgi yok. Önceki raporlardaki sayıyı yeniden hesaplama, yalnız 18 Kasım'dan sonrasını ve eksikleri ekle. Rapor: `raporlar/2026-11-2X_kanal_ve_bildirim_verisi.md`.

## 1. Satış ve kaynak
1. Bugüne kadarki gerçek satışlar (testçi, promosyon, ücretsiz verilen hariç): tarih, platform, plan, deneme mi, bugünkü durumu. 18 Kasım'dan sonra yeni satış, iptal ya da iade var mı?
2. Sunucu kullanıcı başına **kurulum/geliş kaynağı** tutuyor mu (`InstallSourceReport` ve ilgili alanlar)? Ne tutuyor, hangi sürümden beri, kaç müşteride dolu? Alıcılarda ve satın almaya basıp tamamlamayanlarda ne yazıyor?
3. Kaynak bilgisi yoksa: App Store kampanya bağlantısı ve Play yönlendiren bilgisi uygulamaya ulaşıyor mu, bugün okunuyor mu; okunmuyorsa okumak ne kadar iş (kabaca).
4. 17 Kasım'daki 76 kayıt: saat saat dağılım, platform, seviye seçimi, ilk gün davranışı; bir paylaşımın saatine denk geliyor mu görülsün diye.

## 2. Bildirim
1. 18 Kasım tablosunun güncel hâli: türe göre gönderim (bugüne kadar, son 7 gün), kişi sayısı.
2. **Her türün bugünkü metni** (başlık ve gövde, Türkçe; değişken yerleriyle) ve hangi koşulda, hangi saatte gönderildiği.
3. Kişi başına sıklık: bir müşteriye bir günde ve bir haftada giden bildirim sayısı (ortanca, en çok). Aynı türün aynı kişiye tekrar sayısı (özellikle "geri dön", "ilk okumaya çağrı", "seri başlat").
4. Gönderim saatlerinin dağılımı (kullanıcının yerel saatiyle); 09–21 dışında giden var mı.
5. Dokunma kaydı gönderim kaydıyla eşleşiyor mu (bildirim kimliğiyle)? Eşleşiyorsa türe göre dokunma. Eşleşmiyorsa neden.
6. Bildirim adresi olup hiç bildirim almamış müşteri; adresi geçersiz dönen (gönderim hatası) sayısı, platforma göre.
7. Bildirim tercihini kaydetmedeki sunucu hatası (6 müşteri): neden; düzeltmesi ne kadar iş.
8. Bildirim alıp sonraki 24 saatte bildirimleri kapatan ya da uygulamayı bir daha açmayan var mı (ölçülebiliyorsa).
9. Derleme 49 ile gelenler: izin alanı, ulaşma kaydı ve "Yarın hatırlat" kapısı canlıda hangi tabloya, hangi adla düşecek (yayından sonraki okuma için).

## Ek: En sadık kullanıcılar neden gitti? (Mehmet, 21 Kas 00:58; salt okuma, öncelikli)
Mehmet'in gözlemi: 5-6 gün giren, hatta en çok giren müşteriler 6-7 gündür girmiyor. Kişi adı ve e-posta yazma; müşteri başına bir satır, sıra numarasıyla.
1. En az 4 ayrı gün okuma yapmış gerçek müşterilerin tamamı: ilk gün, son gün, okuma günü sayısı, bitirdiği hikâye, okuduğu kelime, defterindeki kelime, seviyesi, cihaz (iOS/Android), uygulama sürümü, ödeme durumu, satın alma ekranını gördü mü / satın al'a bastı mı.
2. Her biri için **son oturum**: son açtığı metin (bitirdi mi, yarıda mı), son gün bir sınıra çarptı mı (dokunma, kilit, defter), son gördüğü ekran biliniyorsa o.
3. Son günden sonra kendisine giden bildirimler: kaç tane, hangi metinle, dokundu mu. Bildirim izni açık mı.
4. Son okudukları ne tür: dizinin ortasında mı kaldılar, dizi mi bitti, seviyelerinde okunmamış ücretsiz metin kalmış mıydı?
5. Özet: gidişlerde ortak bir an var mı (aynı gün, aynı sınır, aynı metin, dizi bitişi)? Kaçı hâlâ etkin sayılır (son 3 gün)?
Çıktı: `raporlar/2026-11-21_sadik_kullanicilar.md`.
