# Editöre not – 22 Kasım gece (Mehmet'in 23:53–00:36 arasındaki sözleri)

**Kime:** editör · **Kimden:** ekip · **Ne isteniyor:** oku, aşağıdaki "senden beklenen" maddelerini yap, tek raporla cevap ver: `raporlar/2026-11-22_editor_gece_notu_cevabi.md`.
Hepsi **salt okuma** (kod, canlı veritabanı sorgusu). Kod yazılmaz, yayın yapılmaz; tek istisna bölüm 1'deki küçük iş. Bilinmeyene "bilinmiyor" yaz. Mehmet'e soru sorulmaz.

## 1. Derleme 50'den önce tek acil iş: "Seviyeni belgele" ısınma soruları
Satır Mehmet'in sözüyle yeniden görünür. İlk ekranda altı soru birden çıkıyor, sonuncusu B2 paragrafı.
**Senden beklenen:** ısınma sorularının sırası ve seçimi sunucuda mı, uygulamada mı belirleniyor, yaz. Kolaydan zora sırala (zaten öyleyse dokunma); seviyesi A1–A2 olan kullanıcıda B2 sorusu yerine bir A1 sorusu gelsin. Sunucudaysa PR aç, yayın Mehmet'in sözüyle. Ayrıntı: `ortak/editor_gorevi_2026-11-21_aksam.md` bölüm F.

## 2. Sınav sistemi: ölçme hocasına (Charles) bilgi
**Mehmet (00:36):** "Seviye bilgisi için bir hoca alacaktık. Önerisi ne sınav sistemi için? Editör üzerinden kodları, sınav bilgilerini hocamla paylaşalım; önerisini değerlendirmeli."
Hoca ekipte: Charles Kızılağaç, ölçme ve değerlendirme (21 Kasım'da eklendi; `uyeler/charles_kizilagac_olcme.md`). Bugüne kadarki önerileri kodu görmeden, ekran ve özet veriyle yazıldı. Tam öneri için aşağıdakiler gerekiyor.
**Senden beklenen** (`raporlar/veri_2026-11-22/sinav_sistemi/` altına, dosya dosya):
| # | İstenen | Ayrıntı |
|---|---|---|
| H1 | **Üç ölçmenin akışı, koddan:** ilk yerleştirme (onboarding), "Seviyeni yeniden ölç", "Seviyeni belgele" | Her biri için adım adım: hangi ekran, kaç soru, soru nasıl seçiliyor, ne zaman bitiyor, kullanıcı yarıda çıkarsa ne oluyor. İlgili dosya ve satırlar |
| H2 | **Puanlama ve seviye kararı** | Her testte ham cevaptan seviyeye giden kural tam olarak (eşikler, ağırlıklar, yuvarlama). "Belgele"de puan (ör. 62) nasıl hesaplanıyor, hangi puan hangi seviye, belge hangi koşulda veriliyor. "Yalnız yükselt" kuralı nerede geçerli |
| H3 | **Soru bankaları** | Yeniden ölçmenin kelime taraması (30 kelime nasıl seçiliyor, sahte kelime var mı) ve boşluk doldurma parçaları: tam döküm, seviye etiketleriyle. Belgeleme soruları zaten döküldü (`belge_sorulari.md`); eksik olan: her sorunun seviyesi kim tarafından, neye göre verildi (elle mi, üretimle mi) |
| H4 | **Gerçek kullanıcı verisi, soru bazında** | Tamamlanmış her ölçüm için: kullanıcının önceki seviyesi, sonuç seviyesi, süre. Soru ya da kelime bazında: kaç kişi gördü, kaç kişi doğru yaptı (seviyeye göre). Yarıda bırakılan ölçümler hangi adımda bırakıldı. Kişisel bilgi yok |
| H5 | **Ölçümden sonra ne oldu** | Seviyesi değişen müşteriler: sonraki 7 günde okudukları metinlerin seviyesi, bitirme oranı, 100 kelimede dokunma. Seviyesi düşen 4 müşteri ayrıca |
| H6 | **Seviye bugün nerelerde kullanılıyor** | Raf sıralaması, yolculuk ataması, günlük havuz, öneri, quiz: seviye yanlışsa kullanıcı neyi yanlış görür |
| H7 | **Silinen seviye geçiş sınavı** | Eylül'de neden silindi (commit notu); tablodaki 4 sınav ve 40 soru ne durumda |
| H8 | **Değiştirmenin maliyeti** | Charles'ın bugünkü önerilerinin her biri için kaba iş büyüklüğü ve sunucu mu uygulama mı: (a) belge testi de kısa kelime adımıyla başlasın ve kullanıcının seviyesinden sorsun; (b) sorular tek tek gösterilsin; (c) her seviyeye belge verilebilsin ("A1 okuma belgesi"); (d) sonuç dili teşhis dili olsun ("şu an buradasın, sıradaki adımın bu"); (e) soru bazında cevap kaydı tutulsun |
Charles bu dosyalar gelince sınav sistemi önerisini yazar (`raporlar/` altına); ekip değerlendirir, Mehmet'e sonuç raporlanır.

**Charles'ın bugünkü ön önerisi (kayıt için):** test kullanıcının seviyesinden başlamalı; ısınma kolaydan zora; "…" ile biten 29 soru tam soru cümlesine çevrilmeli; 176 soru okunmadan belge iddiası zayıf; ana sayfa kartından yeniden ölçme seviyeyi düşürmemeli (derleme 50'de düzeltildi); sonuç yargı değil teşhis diliyle söylenmeli.

## 3. Yolculuk rozetleri (Mehmet 23:56: "yolculuklar tespit edilip rozetler tasarlanacak")
Karar: her yolculuğa bir rozet, yolculuk bitince; ara rozet yok; rozet bir şey açmaz. Sonraki sürüm.
**Senden beklenen:** canlıdaki yolculukların dökümü (ad, seviye, tema, durak sayısı, ücretsiz durak sayısı, atanan ve bitiren müşteri) ve S10–S12 (`raporlar/2026-11-21_editore_bilgi_istekleri.md` sonu).

## 4. Profil resmi (sonraki sürüm; Mehmet 00:29)
Karar: misafir dahil herkese **6** hazır profil resmi (baykuş, kedi, tilki, kaplumbağa, ayı, tavşan; düz renkli daire, yalnız baş, kodla çizilir); fotoğraf yükleme üyede kalır. Ayrıntı: `raporlar/2026-11-22_profil_resmi_toplanti.md`. Mehmet örnek çizimi gördü (ekip çizdi, sohbetteydi); itiraz etmedi, onay da vermedi.
**Senden beklenen:** profil resmi sunucuda nasıl tutuluyor; uygulamada nerelerde çiziliyor; 1.0.2 bilinmeyen bir resim değeriyle ne yapar; üye hesapla fotoğraf yükleme gerçek telefonda çalışıyor mu (41 üyeden 0 yükleme var). İş büyüklüğü tahminin (ekip 3–5 saat dedi).

## 5. Hesap açma ve profil resmi teşviki (Mehmet 00:34)
**Mehmet:** "Kullanıcıyı arada teşvik etmek lazım; hem hesap oluşturması hem profil resmi için. Hesap için kayıp riski hatırlatılsın."
Ekibin ön görüşü: hatırlatma sayısı artmasın, anı ve içeriği değişsin. Kullanıcının bir şey biriktirdiği anda (3. hikâye, 3 günlük seri, defterde 10 kelime, rütbe) kendi birikimiyle söylensin; en çok haftada bir. Profil resmi ayrı bir istek olmasın: hazır resim misafire açık, kendi fotoğrafı hesabın karşılığı. Sonraki sürüm.
**Senden beklenen:** S13–S15 (aynı dosyanın sonu): bugünkü hesap hatırlatmalarının yeri, sıklığı ve getirdiği kayıt; misafir uygulamayı silince ya da telefon değiştirince ilerlemesine ne oluyor; üyeliğe geçen 31 misafirin geçmeden önceki son adımları.

## Sıra ve rapor
1 → 2 → 5 → 3 → 4. Bölüm 2 en büyüğü; dosyaları hazır oldukça gönder, hepsini bekleme. Raporun başına: ekibin karar vermesi gerekenler.
