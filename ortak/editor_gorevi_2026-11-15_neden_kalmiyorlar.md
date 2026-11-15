# Editör görevi – "Kullanıcılar neden kalmıyor": canlı veritabanı sorguları

**Tarih:** 15 Kasım 2026 · **Rol:** Nate Gümüş (veri); itiraz için Nassim Talip. Tek geçiş.
**İzin:** Mehmet canlı veritabanını okumaya izin verdi (15 Kas 21:54). **Yalnız okuma.** Hiçbir satır yazılmaz, silinmez, değiştirilmez.

## Neden bu görev
Firebase'e dayanan ilk okuma yanlış çıktı (`raporlar/2026-11-15_editor_bolum1_ek.md`, V1). Onboarding'i bitirenlerin %81–85'i okumaya başlıyor; yani kayıp başka yerde. Apple'ın verisi ertesi gün dönüşü yaklaşık %10, yedinci günü yaklaşık %5 gösteriyor (yalnız izin veren kullanıcılar). Bu görev kaybın nerede ve hangi davranışla birlikte olduğunu uygulamanın kendi kayıtlarından bulur.

## Kurallar
- Yalnız müşteri hesapları (`"Users"."AccountKind"='customer'`). Test ve geliştirici hesapları hariç.
- Her oranı pay ve paydayla yaz (ör. 12/85). Paydası 20'nin altındaki satırlara "az veri" notu düş.
- Gün tanımı: kullanıcının yerel günü bilinmiyorsa UTC+3. "N. gün döndü" = kayıttan sonraki N. takvim gününde en az bir uygulama açılışı ya da herhangi bir olay.
- Kayıt anı için en güvenilir alanı kullan ve hangisini kullandığını yaz.
- Dönüşü ölçerken yalnız o günü görecek kadar eski kullanıcıları say (D7 için en az 8 gün önce kaydolanlar).
- Rapora kişisel veri koyma: e-posta, ad, tam kullanıcı kimliği yok. Tek kullanıcıdan söz etmek gerekirse "kullanıcı A" de.
- Bulduğun şey bir bağıntıdır, neden değildir; öyle yaz. Tek bir kesit hipotezdir.
- Aşağıdaki tablo ve sütun adları koddan okundu; şemayla uyuşmayan olursa şemaya uy ve notunu düş.

## Sorular

**S1. Dönüş eğrisi.** Kayıt haftasına göre D1, D3, D7 dönüş oranı. Ayrıca platforma (`SignupPlatform`) ve uygulama sürümüne göre. Apple'ın %10 / %5 sayısıyla uyuşuyor mu?

**S2. İlk gün davranışı ve dönüş.** Kullanıcıları ilk 24 saatte yaptıklarına göre grupla, her grubun D1 ve D7 dönüşünü ver:
hiç okumadı · okumaya başladı, bitirmedi · 1 metin bitirdi · 2 ve üzeri metin bitirdi; ayrıca (evet/hayır kırılımı olarak) quiz yaptı, deftere kelime ekledi, ses dinledi, günün quizine girdi.

**S3. İlk metin ve dönüş.** Kullanıcının ilk açtığı metne göre: okur sayısı, bitiren, D1 ve D7 dönüş. Paul Ulus'un hipotezi: A2 ve üstünü seçenlere önerilen "The Island Where Rabbits Won" etiketinden zor; ilk metni o olanlar daha mı az dönüyor?

**S4. Kelime bakış yoğunluğu ve dönüş.** İlk okumada 50 kelime başına bakış sayısına göre üç dilim (0–1, 1–3, 3 üzeri): bitirme oranı ve D1 dönüş.

**S5. Nerede bıraktılar.** En az 4 gün önce kaydolup son 3 gündür hiç görünmeyen müşterilerde: son oturumdaki son olay türü (ilk 10) ve ömür boyu oturum sayısı dağılımı (1, 2, 3–5, 6 üzeri).

**S6. Ücretsiz içerik sınırı.** Kaç müşteri kilitsiz metinlerin hepsini bitirdi? Bunların kaçı sonra kilitli içeriğe ya da paywall'a çarptı, kaçı ertesi gün döndü? Günlük açılan ücretsiz metin (`FreeTextUnlocks`) kaç kişide en az bir kez açıldı?

**S7. Bildirim.** Bildirim izni veren müşteri oranı. Kayıttan sonraki ilk 3 günde bildirim alan ve almayanların D3 dönüşü. Gönderilen bildirimden sonraki 2 saatte açılış oranı (hazır sorgu: `MigrationScripts/PushCopyOpenRate_2026_11_12.sql`).

**S8. Erken Premium teması.** İlk oturumunda paywall ya da Premium şeridi kaydı düşen ve düşmeyen müşterilerin D1 dönüşü.

**S9. Kalanlar.** 7 gün ve üzeri aktif kalan müşteriler: kaç kişi, platform, seçtikleri seviye, ilk metinleri, ilk gün kaç metin bitirdikleri, nereden geldikleri (`InstallSource`, `InstallReferrer`). Gidenlerden neyle ayrılıyorlar?

**S10. Kullanıcıların kendi sözleri.** `UserFeedback` tablosundaki müşteri mesajlarının tamamı: tarih, kategori, platform, mesaj metni (iletişim bilgisi çıkarılmış).

**S11. Geliş kaynağı.** `InstallSource` / `InstallReferrer` dağılımı ve kaynağa göre D1 dönüş.

## Rapor
`raporlar/2026-11-15_neden_kalmiyorlar.md`:
1. En üstte beş satır: kayıp en çok nerede, hangi davranış dönüşle birlikte görülüyor, hangi hipotez desteklendi, hangisi çürüdü, neyi bilemiyoruz.
2. Her soru için tablo ve iki cümlelik okuma; veri noktası sayısı ve "hipotez" etiketi.
3. Kullanılan sorgular ek olarak (`MigrationScripts/` altına yalnız okuma betiği olarak da kaydedilebilir).
4. "İtirazlar" (Nassim Talip): hayatta kalan yanlılığı, küçük sayılar, test hesabı sızıntısı.
5. Kod ya da içerik değişikliği önerme; yalnız bulgu. Sonra dur.
