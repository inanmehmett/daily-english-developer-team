# Editör görevi – XP ve rütbe ekonomisi (salt okuma) + iki taslak

**Tarih:** 18 Kasım 2026 · **Dayanak:** `raporlar/2026-11-18_ilerleme_hissi_toplantisi.md` · **Öncelik:** Sürüm 1 işlerinden sonra. Kod ve veritabanı değişikliği yok.
Canlıya önceki gibi salt okunur bağlan; yalnız `AccountKind='customer'`; kişisel bilgi yok. Rapor: `raporlar/2026-11-1X_xp_ekonomisi.md`.

## Veri
1. **Kurallar:** hangi eylem kaç XP veriyor (hikâye bitirme, quiz, kelime tekrarı, seri, diğer); Premium çarpanı; `LevelSystems` tablosunun tamamı (ad, CEFR, alt basamak, min/max XP).
2. **Dağılım:** müşterilerin toplam XP dağılımı; her rütbeye varan kişi sayısı; rütbeye varış süresi (kayıttan kaç gün, kaç hikâye sonra).
3. **İlk oturum:** ilk gün kazanılan XP (ortanca, %75, %90); 1, 2, 4 hikâye bitiren kullanıcı tipik olarak kaç XP'de.
4. **Kutlama:** rütbe atlayan kaç kişi, sonraki 24 saatte dönüşleri (aynı günkü etkinlik düzeyindeki rütbe atlamayanlarla karşılaştır; az veri notuyla).
5. **Öneri tablosu (karar ekipte):** "1. hikâyede ilk rütbe, başlangıç bitince ikinci, ilk hafta sonunda üçüncü" eğrisi için hangi eşikler gerekir; eşikler böyle değişirse bugünkü müşterilerden kaçı hangi rütbeye yükselir.

6. **Önerilen merdivenin denemesi:** `raporlar/2026-11-18_rutbe_esikleri_ve_adlari.md` bölüm 2'deki eşikler (20, 150, 500, 1.200, 2.400, 4.200, 6.800, 10.300, 15.000, 21.500, 30.000, 41.000) uygulanırsa: yeni bir kullanıcı 1., 2. ve 4. hikâyeyi bitirdiğinde hangi rütbede olur (quizli ve quizsiz); bugünkü müşterilerin kaçı hangi rütbeye yükselir; ilk hikâye bitişinde aynı anda kaç kutlama/rozet tetiklenir (İlk Kitap, İlk Quiz, rütbe).

## Taslak (yalnız görüntü)
A. **Bitiş ekranında ilerleme:** "+XP" → sonraki rütbeye dolan çizgi ("Meraklı'ya 2 hikâye kaldı") → sıradaki hikâye kartı. Rütbe atlanan durum için ikinci kare.
B. **"Senin Yolculuğun" sayfası:** hikâye kapaklarından yol (önceki taslak), rütbesiz; üstte yolculuk adı ve n/4. Kariyer sayfası ayrı kalır, adı "Okur Kariyerin".
"Başka yolculuk seç" hiçbir yerde yok.
