# Güncel iş listesi – tek görev kaynağı

**Son güncelleme:** 26 Kasım 2026 (editör). Mehmet'in sözüyle ("hepsi onaylı, yap") sadeleştirildi. 26 Kasım'a kadarki liste ve Mehmet'in bütün doğrudan sözleri: `raporlar/2026-11-26_is_listesi_arsivi.md`.

## Kurallar
- Ekip görevi yalnız buraya yazar, günde en çok bir kez günceller. **Editörün işi tek yerde:** `ortak/editor_kuyrugu.md`; burada yalnız özeti durur.
- Ürün kararını ekip verir. Mehmet'e yalnız canlıya yazma, sunucu ve mağaza yayını, fiyat ve silme sorulur. Mehmet'in editöre doğrudan sözü bu listenin üstündedir.
- Bir özellik hakkında konuşmadan önce koda bakılır. Her toplantının başında mağaza durumu iki konsoldan okunur.
- Bir derleme, bir konu. Editörün görüntüleri Mehmet'e gitmeden önce Dieter ve Don'dan geçer.

## Hedef
Yeni gelen kullanıcı ilk gün iki hikâye bitirsin; ertesi gün dönsün ya da ödesin. (Bir hikâye bitiren %54 → %65; iki bitiren %22 → %35; ertesi gün dönen %21 → %28; yayından sonraki ilk 250 yeni müşteride.)

## Durum
| Konu | Durum | Kaynak |
|---|---|---|
| iOS | 1.0.4 (50) yayında | App Store Connect, 25 Kas |
| Android | 1.0.4 (47) yayında; (50) için Mehmet: "yayına gönderdim" | Play Console 25 Kas; Mehmet 26 Kas. **Konsoldan doğrulanmadı** |
| Sunucu, canlıda | PR #15, #16, #18, #19 ve #20 (özel isimler: ülke, deniz, şehir; 25 Kas) | depo |
| Açık PR, sunucu | #21 şık karıştırma ve B2 soruları · #22 ad değişiklikleri · #23 bildirim metinleri · #17 (21 Kas'tan beri) | depo |
| Açık PR, uygulama | #5: mağazadaki 1.0.4 (50) `main`'e | depo |
| Canlı sayımlar | Çekilemedi (editör oturumunda veritabanı erişimi reddedildi) | `raporlar/2026-11-26_editor_cevap.md` |

## Tarihli işler
| Tarih | İş | Sahibi | Durum |
|---|---|---|---|
| 27 Kas | Açıklama sonu için 5 dönüşümlü tek satır | Tomris | açık |
| 27 Kas | Öne çıkanlara "Uygulama" | Adam → Mehmet | açık |
| 28 Kas | 21 Kasım'da başlayan deneme bitiyor: yenileme açık mı | Editör | canlı veri bekliyor |
| 28 Kas | Kampanya bağlantıları (bio, hikâye, devam); bio linki | Sean → Mehmet | açık |
| 29 Kas | Okumaya başlama sınavı (hedef %90), sürüme göre | Nate; sayı editörden | canlı veri bekliyor; gelmezse kayar |
| 30 Kas | "Daily English Founder" 50 kod bitiyor (19 Kas'ta 0 kullanılmış) | Mehmet | Android'de 50 yayındaysa dağıt; değilse yeni promosyon |
| 30 Kas | Köprü denemesi tasarımı; metinlerin ücretsiz olduğunun koddan doğrulanması | Mr. Feast; editör | açık |
| 30 Kas | Pazartesi raporunda iki ekip yan yana | Nate, Steve | açık |
| 1 Ara | Abonelik kaydı 34'ün denemesi bitiyor | Nate | izleniyor |
| 4 Ara | Checkpoint: ödeyen abone en az 5 (4 plan denemede); PMF anketi tutmayacak | Nate | izleniyor |

## Mehmet'te
1. PR'ları birleştirmek: sunucu #21 ve #23 (birleşince yayına girer), #22; uygulama #5.
2. Editöre canlı veri erişimi (sayımlar ve ad betiği bunu bekliyor).
3. Play'de 1.0.4 (50) yayınının konsoldan teyidi; Founder kodları.
4. Telefonda denenmeyenler (T16): Google'da uygulama içinden iptal, gerçek promosyon koduyla Premium, misafir hesabın geri gelmesi.
5. Kapalı test kanalı (T8): testçi listesindeki işaret kaldırılır, kanal duraklatılır.
6. Instagram: bio linki ve öne çıkan (yukarıda).

## Editörde (ayrıntı `ortak/editor_kuyrugu.md`)
- Canlı sayımlar: sürüm dağılımı, tutunma ve 29 Kasım sayımı, geri bildirimler, çekirdek grup, satın alanlar, haftalık tablo, bildirim dokunma oranları, deneme ve yenileme dökümü, abonelik sayaçlarının tutarlılığı.
- Ad betiğinin canlıda çalıştırılması (#22 yayına girdikten sonra).
- PR #21 yayına girince canlıda doğrulama (etkin soru sayısı, rastgele üç soru).
- Köprü denemesi için metinlerin ücretsiz olduğunun doğrulanması.

## Ekipte
| İş | Kim |
|---|---|
| PR #21'deki soru metni sapmaları ve iki "metin bağı" etiketi; 56'nın türü (A1'de çıkarım yasak) | Charles, Paul |
| Kalan bildirim türlerinin metni: ilk okuma 3. ve 7. gün, günlük hatırlatma, seri telafisi, geri dön 7/14/30. Kural: `ortak/uygulamanin_sesi.md` | Paul, Tomris |
| "Günün ücretsiz metni" ve "yeni rütbe" bildirimleri yeniden açılsın mı (12 Kas'tan beri kapalı) | Don, Sean |
| "Az kaldı" bildirimi: kalan süre hesaplanamıyor; istenirse ihtiyaç tanımı | Don |
| Room 214, 7. bölümün Türkçe adı kardeşin yerini erken söylüyor; İngilizce alt adlar | Tomris |
| Yorum isteme penceresi kodda var: koşullar uygun mu (3 gün, 3 etkin gün, 3 okuma, 120 gün ara), kaç kez gösterildi | Sean, Nate |
| Abonelikler sayfasında ödeme türü kendi sütununa alınsın mı (taslakla) | Dieter |
| 22 Kasım'dan kalan küçük kararlar: Adventure ve Curiosity'nin Türkçesi · slaytta büyük yazı · ana sayfa halkasının kariyer sayfasıyla aynı yüzdeyi göstermemesi · "ayrıca" satırı kuralı | Dieter, Don; Charles, Paul |
| Sonraki sürümün en çok dört konusu (1.0.4 iki mağazada yayınlanınca) | Steve |
| Mağaza yorumlarının dökümü ve cevap taslakları | Tony |
| Belge soruları için dış göz paketi | Paul, Charles |

## Derleme 51 (kapsamı ve tarihi ekip belirleyecek)
- Dalda bekleyen iki okuyucu düzeltmesi (`2687ee03`, `6e07653f`).
- Derleme 50 görüntü bulguları: büyük yazıda sıkışan "Yeni yol başladı" etiketi, %92'de rozete değen bayrak, belge testinde altta kalan şıklar için kaydırma ipucu.
- T5 (kişi kartında geciken rütbe satırı), T7 (Rozetlerim'de "%1 tamamlanma").

## Sonraki sürüm adayları
Profil resmi ve hesap teşviki · yolculuk rozetleri · "kullanıcının sesi" kutusu (uygulama içi tek soruluk kart, "bize ulaş"ın görünürlüğü) · ana sayfa sadeleşmesi (veriyle) · belge testinde kelime adımı · her dizinin ilk bölümü ücretsiz.

## Durdurulanlar
Günde iki bildirim düzeni · kelime balonu A/B · rütbe adları · kariyer ve yolculuk adı üzerine yeni tartışma · anlam motorunun kalanları · kampanyalar · kullanıcıya e-posta (Mehmet, 25 Kas).

## Mehmet'ten doğrudan (editör yazar; öncekiler arşivde)
- 26 Kas: "Yayına gönderdim. Editördeyiz zaten. Hepsi onaylı, yap; tüm yetkiler sende." Editör: şık karıştırma ve B2 soruları (PR #21), ad betiği (PR #22), bildirim metinleri (taslak 3, PR #23), uygulama deposu (PR #5) hazırlandı; birleştirme ve canlı veri erişimi oturumun izin katmanında reddedildiği için Mehmet'te. Liste sadeleştirildi, bildirim kuralı `ortak/uygulamanin_sesi.md`'ye girdi. Rapor: `raporlar/2026-11-26_editor_cevap.md`.
