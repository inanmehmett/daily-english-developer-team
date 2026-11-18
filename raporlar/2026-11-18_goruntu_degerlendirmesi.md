# Değişen ekranlar, balon ve harita taslağı – ekip değerlendirmesi

**Tarih:** 18 Kasım 2026 · Tek geçiş; üyeler kurgusaldır. **Dayanak:** `raporlar/2026-11-18_cihaz_geri_bildirimi_uygulama.md`, `raporlar/ekran_2026-11-18b/`. Görsel onay Mehmet'te; aşağısı ekibin görüşü.

## Değişen ekranlar (Dieter, Don)
- **Plan ekranı:** uygun. Dört kapak, "Bugün", alt satırdaki "İlk hikâyeler ücretsiz, planın tamamı Premium ile" dürüst ve yerinde.
- **2. hikâye bitişi:** uygun. İki kapı ana eylem, quiz bağlantı, "Şimdilik bu kadar" çıkış. Beyaz kart kararı doğru.
- **Onboarding sonu teklifi:** başlık, seçili plan, düğme ve ücretsiz yol tek ekranda; uygun. **Bir düzeltme:** SE 3'te madde listesinin son satırı sabit başlığın altından yarım görünüyor ("Hikâyeleri indir…" kesik). Küçük ekranda liste ya tam satır sınırında başlasın ya da başlığın altında yumuşak bir geçişle kaybolsun; yarım satır kalmasın.
- **Büyük yazıda bitiş ekranı:** "Paylaş" satırı durum çubuğunun (saat) altına giriyor. Kaydırma konumu güvenli alanın altında başlamalı.
- Bu iki düzeltme TestFlight'tan önce.

## Kelime balonu
- **Ekip önerisi: B (anlam + ekle).** Ölçüm Mehmet'in şikâyetini doğruluyor: balon ekran genişliğinin %78'ine çıkıyor, okunan iki satırı örtüyor, anlamın yeri her dokunuşta değişiyor. B'de etiket kelimenin tam üstünde, alanın %2'si; deftere ekleme tek dokunuşta kalıyor (defter, kullanıcıyı geri getiren yatırım).
- Ekler (Don): eklenince "+" yerinde "✓" olur; uzun anlamda yalnız birincil anlam; etiket hiçbir şeyi itmez; ekranın üst kenarındaki kelimede etiket kelimenin altında açılır. Onboarding'in "kelimeye dokun" adımı aynı etiketle güncellenir ve SE 3 + büyük yazıda denenir (tooltip hatasının çıktığı yer).
- **Sıra:** Sürüm 1'den hemen sonraki küçük sürüm. Ölçüm: dokunuş başına deftere ekleme oranı ve metin bitirme oranı, önce/sonra.

## Yolculuk sayfası taslağı
- **Yön doğru:** eski yol + kutularda kapaklar, okunan ✓, sıradaki belirgin, yolun sonunda sıradaki yolculuk.
- **Rütbe (ekip kararı: kalır):** her yolculuğun bitiş noktasında rütbe madalyası (Çaylak → Meraklı…), üstte seviye ve rütbe adı; alttaki XP şeridi kalır. Böylece uzun yol (rütbe) ve adımlar (hikâyeler) tek resimde.
- **Dokunma:** okunan yeniden açılır; sıradaki okuyucuyu açar; yarın açılacak olan iki kapıyı gösterir; kilitli olan kilitli içerik sayfasını.
- Uzun yolculukta (10–12 hikâye) sayfa sıradaki hikâyeye kaymış açılır.
- Sonraki sürüm; editör rütbeli hâliyle taslağı günceller, Mehmet görür.

## Diğer
- **"Dinle" adımındaki ses hatası** (8 sürüşte 1): onboarding'de; gerçek cihazda olursa ilk oturumu bozar. TestFlight gününde çökme panelinden izlenir, görülürse Sürüm 1'i bekletir.
- **Sıra onaylandı:** görüntü onayı → iki küçük düzeltme → sunucu yayını (Mehmet) → `NextHook` "yaz" (Mehmet) → TestFlight → en az bir gün kullanım.
