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
| Android | 1.0.4 (47) yayında; (50) için Mehmet: "yayına gönderdim". Canlı veride derleme 50'de bugün yalnız 1 müşteri var: yayın henüz kullanıcıya ulaşmamış ya da yeni ulaşıyor | Play Console 25 Kas; Mehmet 26 Kas; canlı veri 26 Kas 17:50. **Konsoldan doğrulanmadı** |
| Sunucu, canlıda | PR #15, #16, #18, #19, #20 (özel isimler; 25 Kas), **#21** (şık karıştırma ve B2 soruları; 26 Kas 17:22) ve **#23** (bildirim metinleri; 26 Kas 17:30). İki yayın da başarılı, API cevap veriyor, günlükte hata yok | depo, Railway |
| Ad değişiklikleri | PR #22 canlıda (17:48), betik canlıda çalıştırıldı (17:52): 15 metin yeni adıyla, önceki adlar yedekte | `raporlar/2026-11-26_editor_ad_degisiklikleri.md` |
| Açık PR, sunucu | **#24 bildirim metinleri, onaylı son hâl (`copy_v4`)**: testler geçti, **birleştirme Mehmet'in sözünü bekliyor**. Canlıda şu an taslak 3 (`copy_v3`, PR #23) gidiyor · #17 (21 Kas'tan beri) | depo; `raporlar/2026-11-26_editor_bildirim_metinleri.md` |
| Uygulama deposu | PR #5 birleşti (26 Kas): `main` artık mağazadaki 1.0.4 (50) ve bekleyen iki okuyucu düzeltmesi | depo |
| Canlı sayımlar | Çekildi (26 Kas 17:50): sürüm dağılımı, 29 Kasım sayımı, tutunma, abonelikler, geri bildirimler, bildirimler, haftalık tablo, çekirdek grup | `raporlar/2026-11-26_editor_canli_sayimlar.md` |

## Tarihli işler
| Tarih | İş | Sahibi | Durum |
|---|---|---|---|
| 27 Kas | Açıklama sonu için 5 dönüşümlü tek satır | Tomris | açık |
| 27 Kas | Öne çıkanlara "Uygulama" | Adam → Mehmet | açık |
| 28 Kas 01:13 | Abonelik kaydı 31'in denemesi bitiyor: **yenileme açık**, kullanıcı denemede hiç hikâye bitirmedi ve 24 Kas'tan beri gelmedi. Ücret alınırsa ödeyen müşteri 5 olur; iade ya da şikâyet riski var | Nate, Sean | izleniyor; yapılacak bir şey var mı, ekip kararı |
| 28 Kas | Kampanya bağlantıları (bio, hikâye, devam); bio linki | Sean → Mehmet | açık |
| 29 Kas | Okumaya başlama sınavı (hedef %90) | Nate | **Sayı geldi: %74** (11–25 Kas, 179/241); 1.0.4 ile gelen yalnız 28 müşteri var. Karar 5 gereği 1.0.4 için sınav kayar: iOS 1 Aralık, Android 50 yayın teyidinden 7 gün sonra |
| 30 Kas | "Daily English Founder" 50 kod bitiyor (19 Kas'ta 0 kullanılmış) | Mehmet | Android'de 50 yayındaysa dağıt; değilse yeni promosyon |
| 30 Kas | Köprü denemesi tasarımı; metinlerin ücretsiz olduğunun koddan doğrulanması | Mr. Feast; editör | açık |
| 30 Kas | Pazartesi raporunda iki ekip yan yana | Nate, Steve | açık |
| 1 Ara | Abonelik kaydı 34'ün denemesi bitiyor | Nate | izleniyor |
| 4 Ara | Checkpoint: ödeyen abone en az 5. **Bugün 4 ödeyen müşteri**, 6 deneme sürüyor (5'inin yenilemesi açık; bitişler 28 Kas–2 Ara); PMF anketi tutmayacak | Nate | izleniyor |

## Mehmet'te
1. Telefonda bir bakış: katalogda yeni adlar; bu akşamki bildirimin yeni metinle gelip gelmediği.
2. Founder kodları: Mehmet "sonra bakarız" dedi (26 Kas); promosyon 30 Kasım'da bitiyor.
3. Play'de 1.0.4 (50) yayınının konsoldan teyidi.
4. Telefonda denenmeyenler (T16): Google'da uygulama içinden iptal, gerçek promosyon koduyla Premium, misafir hesabın geri gelmesi.
5. Kapalı test kanalı (T8): testçi listesindeki işaret kaldırılır, kanal duraklatılır.
6. Instagram: bio linki ve öne çıkan (yukarıda).

## Editörde (ayrıntı `ortak/editor_kuyrugu.md`)
- 3 Aralık: bildirim tablosunun yeni metinlerle (`copy_v3`) yeniden çekilmesi; tutunmanın sürüme göre ayrımı.
- Canlıda şıkların karıştığının ilk gerçek denemede görülmesi (yayından beri deneme yok).
- "Hiç olay göndermemiş" 35 müşterinin incelenmesi.
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

## Bugünkü sayımlardan ekibe düşenler (26 Kas)
| Bulgu | Kim |
|---|---|
| Android'de yeni müşteri 23–25 Kasım'da 3, 0, 1 (önceki dört gün ortalama 8). Neden? Play Console edinme ve mağaza sayfası, Instagram akışı | Sean, Nate |
| Android 7. gün dönüşü 16 Kasım haftasında 8/53 (%15), öncesinde 1/66. 1.0.4 (47) etkisi mi? Sürüme göre ayrım istenecek | Nate, Don |
| Bildirimde dokunma yalnız seri ailesinde (%12–17); öbür altı türde 172 gönderimde sıfır. Yeni metinlerle 3 Aralık'ta karşılaştırma; sıfır kalan türler kapatılsın mı | Don, Paul |
| Uygulama içi değerlendirme penceresi bugüne kadar 1 kez istendi. Koşullar gevşetilsin mi (ihtiyaç tanımı, sonraki derleme) | Sean, Don |
| Abonelik kaydı 28 (Android, 19 Kas) müşteri sayılıyor ama test satın almasına benziyor; hesap türü düzeltilsin mi | Nate; Mehmet teyit eder |
| Profildeki "bize ulaş"tan müşterilerden hiç ileti gelmemiş (4 iletinin hepsi testçi ve geliştirici). Giriş görünür mü | Tony, Don |
| Çekirdek grup 64 kişi, 41'i misafir; 7 gün ve üstü etkin 9 kişi. Hesap teşviki ve "kullanıcının sesi" kutusu için dayanak | Steve |

## Derleme 51 (kapsamı ve tarihi ekip belirleyecek)
- Dalda bekleyen iki okuyucu düzeltmesi (`2687ee03`, `6e07653f`).
- Derleme 50 görüntü bulguları: büyük yazıda sıkışan "Yeni yol başladı" etiketi, %92'de rozete değen bayrak, belge testinde altta kalan şıklar için kaydırma ipucu.
- T5 (kişi kartında geciken rütbe satırı), T7 (Rozetlerim'de "%1 tamamlanma").

## Sonraki sürüm adayları
Profil resmi ve hesap teşviki · yolculuk rozetleri · "kullanıcının sesi" kutusu (uygulama içi tek soruluk kart, "bize ulaş"ın görünürlüğü) · ana sayfa sadeleşmesi (veriyle) · belge testinde kelime adımı · her dizinin ilk bölümü ücretsiz.

## Durdurulanlar
Günde iki bildirim düzeni · kelime balonu A/B · rütbe adları · kariyer ve yolculuk adı üzerine yeni tartışma · anlam motorunun kalanları · kampanyalar · kullanıcıya e-posta (Mehmet, 25 Kas).

## Mehmet'ten doğrudan (editör yazar; öncekiler arşivde)
- 26 Kas 23:19: kartta görünmeyen beş ad için kısa karşılıklar **onaylandı** ("tamam, editöre prompt ver"). Editör kuyruğu 9. Soru: "Penguen Neden Uçamaz mı, Penguenler Neden Uçamaz mı?" Ekip görüşü: çoğul (İngilizce ad "Penguins"; öğrenen iki satırı karşılaştırıyor); Mehmet'in kararı bekleniyor.
- 26 Kas 21:18: "The Market That Moves ve Rabbit Island'ın Türkçe isimleri kartta görünmüyor; Game Day dizisinin adı hiç gösterilmiyor." Neden koddan bulundu: kart 28 karakterden uzun Türkçe adı gizliyor (28 metin; onaylı 15 yeni addan 5'i); dizi kartı adı kapak resminde varsayıyor. Rapor ve karar: `raporlar/2026-11-26_kartta_gorunmeyen_adlar.md`; editör kuyruğu 6.
- 26 Kas 17:44: bildirim metinleri **"onay… editöre emir için hazırla"**. Editör görevi: `ortak/editor_gorevi_2026-11-26_bildirim_metinleri.md` (kuyruk 5). Deneme başlığı "Küçük bir hatırlatma", ad gövdede. Konu cümlesi eklenmedi.
- 26 Kas 17:30–17:31: "Duygu uyandırıyor mu bu bildirimler? Psikoloji ekibi inceledi mi?" → "Ekle ve yap." Ekibe **BJ Sis** (davranış ve duygu) eklendi. Bildirimler duygu turundan (tur 4–5) ve ikinci bağımsız gözden geçti; son hâl aynı raporun sonunda. Ürün kararları: geri dön dizisi üç bildirim ve 14. gün "son hatırlatmamız" + susma; hiç okumamışa 7. gün son; yenilemesi kapalı denemeye hatırlatma. Mehmet'e iki konu: deneme başlığının kesilmesi, hikâyenin konusunu tek düz cümleyle söylemek.
- 26 Kas 17:18: "Bekleyen iki iş bu düzenden geçsin." Bildirim tablosu ve deneme hatırlatması üç turdan ve bağımsız gözden geçti: `raporlar/2026-11-26_bildirim_metinleri_turlu_inceleme.md`. Mehmet'in onayı bekleniyor; PR #23 o zamana kadar birleştirilmez. Çözülmeyen tek itiraz: deneme başlığı kesiliyor.
- 26 Kas 17:16: **"Tasarruflu çalış, alt ajan yok, tek geçiş kuralını iptal et. Bize kaliteli sonuç lazım. İkinci tur gerekirse sonraki turlardan olsun. Amacımız en iyi sonucu almak."** README'de çalışma modu yeniden yazıldı: taslak → itiraz turu → düzeltme turları (sınır yok) → kullanıcıya giden işlerde bağımsız göz. Raporların başındaki "Tek geçiş" ibaresi bundan sonra yazılmaz; yerine kaç turdan geçtiği yazılır.
- 26 Kas: "Yayına gönderdim. Editördeyiz zaten. Hepsi onaylı, yap; tüm yetkiler sende." Editör: şık karıştırma ve B2 soruları (PR #21), ad betiği (PR #22), bildirim metinleri (taslak 3, PR #23), uygulama deposu (PR #5) hazırlandı; birleştirme ve canlı veri erişimi oturumun izin katmanında reddedildiği için Mehmet'te. Liste sadeleştirildi, bildirim kuralı `ortak/uygulamanin_sesi.md`'ye girdi. Rapor: `raporlar/2026-11-26_editor_cevap.md`.
- 26 Kas (akşam): "Hepsini sen yap. 3. kalsın, sonra bakarız." Editör: sunucu #21 ve #23 birleştirildi ve yayında; uygulama #5 birleştirildi. Canlı veritabanı bağlantısı yine reddedildi; #22 ve sayımlar bekliyor. Founder kodları ertelendi.
- 26 Kas (17:45): "İzin kuralını sen ekle." Editör: salt okunur canlı sorgu ve yalnız ad betiği için iki izin kuralı eklendi (`~/.claude/settings.json`). Canlı sayımlar çekildi (`raporlar/2026-11-26_editor_canli_sayimlar.md`); PR #22 birleştirildi ve ad betiği canlıda çalıştırıldı.
- 26 Kas (akşam): "`editor_gorevi_2026-11-26_bildirim_metinleri.md` dosyasını oku ve uygula… Birleştirme ve yayın için bana sor." Editör: görev geldiğinde PR #23 zaten yayındaydı (17:30); onaylı son hâl yeni PR olarak yazıldı (sunucu #24), birleştirilmedi. Rapor: `raporlar/2026-11-26_editor_bildirim_metinleri.md`. Ayrıca iki soru cevaplandı: kayıt 34'te deneme bitince ücret alınmayacak; iade edilen satın alma kayıt 29, kayıt 28 7 günlük deneme olarak bitmiş görünüyor.
