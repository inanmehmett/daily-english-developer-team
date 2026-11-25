# Editöre iş tanımı – 25 Kasım 2026

**Kimden:** ekip · **Kaynak:** haftalık toplantı ve Mehmet'in 16:56 sözü. Bu dosya tek başına okunur; haftalık raporun 9. bölümündeki iş tanımının yerine geçer (onu içerir).
Gerekçeler: `raporlar/2026-11-25_haftalik_rapor_ve_toplanti.md`, `raporlar/2026-11-25_tutunma_ve_kullanici_sesi_plani.md`.
**Kural:** A bölümü salt okuma (kod yazma yok, yayın yok). B bölümü küçük sunucu ve veri işi; Mehmet'in "6. maddeyi de düzeltelim" sözü B için onaydır (tam test temizse yayın, canlıya yazma yedekli). Yeni uygulama derlemesi **yok.** Karar gerektiren şeyi Mehmet'e sorma; yaz, ekip karar verir. Kişisel veri raporlara girmez (ad, e-posta yok; sayı ve takma kimlik).
**Cevap:** `raporlar/2026-11-26_editor_cevap.md`; A1–A3 hazır olunca beklemeden gönder.

## A. Bilgi (salt okuma)
| # | İstenen | Neden |
|---|---|---|
| A1 | **Sürümler:** son 7 günde etkin kullanıcıların sürüm ve derleme dağılımı (iOS, Android ayrı). Play'de 20 Kasım'dan beri 1.0.4 (47) yayında görünüyor; kaç kullanıcı 47'de? iOS'ta 1.0.4 (50) hangi gün yayına girdi, kademeli yayın açık mı; o günden beri sunucu hatası, çökme ya da satın alma hatası var mı? | Ekip üç gün yanlış sürümü varsaydı |
| A2 | **Okunmamış geri bildirim:** profildeki "bize ulaş" (geri bildirim) alanından gelen iletiler nereye düşüyor; toplam kaç ileti var, tarihleri, cevaplanmış mı. İletilerin metni (kişisel bilgi çıkarılarak) ayrı dosyada: `raporlar/veri_2026-11-26/geri_bildirimler.md`. Profildeki "mağazada değerlendir" ve "bize ulaş" girişlerine kaç kişi dokundu (ölçülüyorsa) | Hiç okunmadı |
| A3 | **Tutunma, uygulamanın kendi kayıtlarından:** başladığı haftaya göre gruplar (30 Eki'den beri), her grup için 1., 7., 14. günde dönen oranı; platforma ve ilk sürüme göre. Ayrıca yeni gelenlerin ilk gün bir hikâye bitirme oranı ve onboarding'i bitirenlerin okumaya başlama oranı (11–25 Kasım, sürüme göre; 29 Kasım sınavı) | Mağaza ölçüsü yalnız izin veren iOS kullanıcılarını kapsıyor |
| A4 | **Çekirdek grup:** en az üç hikâye bitirmiş ve son 14 günde uygulamayı açmış kaç kullanıcı var (platform, üye ya da misafir, bildirim izni). Bu grubun son 14 günü: kişi başına bitirilen hikâye, açılan gün sayısı, kelimeye dokunma, günün quizi; en çok okudukları 10 metin. (E-posta ve anket soruları kaldırıldı; Mehmet: "e-posta boşa uğraş, verilerden devam") | Ürünü gerçekten kullananlar ne yapıyor |
| A5 | **Satın alanlar:** etkin her abonelik için (kimlik yok): platform, plan, başlangıç günü, denemede mi, deneme bitiş günü, üye mi misafir mi, bildirim izni var mı, son 7 günde kaç hikâye bitirdi. Promosyon ve testçi planları ayrı işaretli | Satın alanların davranışı; "ödeyen abone" sayımı. Mesaj gönderilmeyecek |
| A6 | **Yorum isteme:** mağazanın uygulama içi değerlendirme penceresi kodda bir yerde çağrılıyor mu; çağrılıyorsa hangi koşulla. Profildeki "değerlendir" girişi ne yapıyor (mağaza sayfasını mı açıyor) | Sonraki sürümün işi |
| A7 | **Haftalık tablo (19–25 Kasım):** yeni müşteri (gün gün, platform), günün quizi başlayan ve bitiren, seviye ölçümü başlayan ve bitiren, belge testi denemesi, "geri dön" bildirimi gönderim ve dokunma (22 Kasım'dan sonrası ayrı), yeni abonelik (promosyon ve testçi hariç) | Nate'in tablosu |
| A8 | **Belge testi:** şıklar ekranda kayıttaki sırayla mı görünüyor, karıştırılıyor mu; puandan seviyeye giden eşikler; soru bazında cevap kaydı tutuluyor mu; mağaza açıklamasında ve sitede seviye ya da sertifika iddiası geçen cümleler | `raporlar/2026-11-22_belge_seviye_iddiasi_plani.md` |
| A9 | **Derleme 50 görüntü soruları:** kariyer alt şeridi neden gün tahmini yerine "…'ya doğru ilerliyorsun" diyor; belge testinde şıklar ekranın altında kalınca kaydırma ipucu var mı | Sonraki derleme |

| A10 | **Yorum isteme altyapısı:** A6'ya ek: uygulamada sunucudan açılıp kapanan bir kart ya da duyuru alanı var mı; bildirim bir mağaza adresini açabiliyor mu. Mağazalardaki yorum sayısı ve son 10 yorumun metni (iki mağaza) | `raporlar/2026-11-25_bildirim_donus_orani_ve_yorum_isteme.md` bölüm 2 |
| A11 | **Bildirim, 22 Kasım'dan sonra:** türe göre gönderim, dokunma ve dokunan kişi sayısı; "geri dön" için adlı ve yedek metin ayrı; 1.0.4 kullanıcılarında dokunmadan sonra hikâye açılıyor mu. Kelime tekrarındaki 3 gün arası hatası PR #15 ya da #16 ile düzeldi mi | Aynı rapor, bölüm 1 |

## B. Düzeltme (sunucu ve canlı veri; derleme yok)
| # | İş | Not |
|---|---|---|
| B1 | **Şıkların karıştırılması.** A8'in cevabı "karıştırılmıyor" ise: şıklar her gösterimde karıştırılır; doğru cevap konuma değil şıkkın kimliğine bağlıdır. Sunucuda yapılabiliyorsa yap (1.0.2, 1.0.4-47 ve 1.0.4-50 istemcileri bozulmamalı; testle göster). Yalnız uygulamada yapılabiliyorsa yapma, iş büyüklüğünü yaz. Aynı soru "Seviyeni yeniden ölç" boşluk şıkları için de | Belgenin geçerliliği için en önemli düzeltme |
| B2 | **Dört yeni B2 sorusu** (eski 130, 146, 136, 144 kapatılır, silinmez), **iki şık düzeltmesi** (133 "cheap" → "simple"; 161 doğru şık "believed it would be" ve öbür şıklar), **tür etiketleri** (56 ve boş olanlar). Kaynak: `raporlar/2026-11-22_belge_sorulari_paul_okumasi.md` bölüm 2–3. Yedekli betik; tohum dosyaları da aynı hâle | Mekanik denetimden geçmeli; doğru şıkkın konumu karıştırılır |
| B4 | **Kelime tekrarı bildirimi:** 3 gün arası, araya başka tür girse de tutulsun (hâlâ bozuksa). Ayrıca "ilk okumaya çağrı" 1. gün başlığı hikâye adı biliniyorsa her zaman adlı gitsin. PR aç; **yayınlama**, raporla (yayın Mehmet'in sözüyle) | Bildirim raporu, öneri 1 ve 2 |
| B3 | B1 ve B2'den sonra canlıda doğrula: B2 için etkin metin sorusu sayısı aynı; rastgele üç soruyu oku | – |

## Bu görevde olmayanlar
Uygulama derlemesi, anket gönderimi, kullanıcıya e-posta ya da bildirim, mağaza ayarı, profil resmi, rozetler, hesap teşviki. Bunlar ekibin kararını ve Mehmet'in sözünü bekler.
