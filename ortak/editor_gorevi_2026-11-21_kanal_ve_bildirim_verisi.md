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
