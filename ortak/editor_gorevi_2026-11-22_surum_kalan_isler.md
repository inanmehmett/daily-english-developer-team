# Editöre: bu sürümde kalan işler (1.0.4, derleme 50) – tam yetkiyle

**Tarih:** 22 Kasım 2026, 02:40 · **Kimden:** ekip · **Kime:** editör
**Mehmet (02:28):** "Bu sürümde ne işler kaldıysa listele. Rapor hâlinde editöre verelim. Full yetki ile tüm işleri halletsin. Sonraki sürüm işlerini sonra düşünürüz."

Bu dosya tek başına okunur ve bu sürüm için **tek görev kaynağıdır.** Önceki görev ve notlardaki (`editor_gorevi_2026-11-21_aksam.md`, `editor_notu_2026-11-22_gece.md`) bu sürüme ait açık işler buraya taşındı; orada olup burada olmayan iş bu sürümde yapılmaz.

## Yetki
Mehmet'in sözü, **bu dosyadaki işler için** şunları kapsar; ayrıca sormadan yap:
- sunucu PR'larını açmak, tam test turu temizse birleştirmek ve yayınlamak;
- canlı veriye bu dosyada yazılı betikleri, önce yedek alarak çalıştırmak;
- derleme 50'yi çıkarmak, TestFlight'a ve Play dahili teste yüklemek.
Kapsam dışı (Mehmet'in kendi işi): mağazaya gönderim, gerçek parayla satın alma denemeleri, fiyat, silme.
Sınırlar: bu dosyada yazmayan işi yapma. Tam test turu temiz değilse yayınlama. Bir adım canlıda beklenmedik bir şey gösterirse dur, geri al (yedekten ya da önceki sürüme) ve raporla. İzin katmanın bir adımı reddederse o adımı atla, öbürleriyle devam et ve raporun en başına Mehmet'in çalıştıracağı tek komutu yaz.
Karar gerektiren şey çıkarsa Mehmet'e sorma: en az riskli yolu seç, ne seçtiğini raporda yaz; ekip sonradan bakar.

## Sıra
### 1. PR #18'i yayınla (hazır)
Belge testi ısınması. Charles onayladı (C1). Tam tur temizse birleştir ve yayınla; canlıda bir deneme hesabıyla ısınma sorularının seviyelerini doğrula (A1–A2 okurda B2 sorusu yok).

### 2. Sınav sistemi, sunucu (yeni PR; temizse yayınla)
Gerekçe: `raporlar/2026-11-22_sinav_sistemi_onerisi_charles.md`.
| # | İş |
|---|---|
| C3 | "Seviyeni yeniden ölç": sonuç, okurun geçtiği en yüksek parçanın seviyesini aşmaz. Üçüncü parçada 3/3 → sonuç o parçanın seviyesi |
| C4 | "Seviyeni belgele" profil seviyesini yalnız yükseltir. Belge yine kazanılan seviyeye verilir |
| C5 | Kelime taraması kelime bazında kaydedilir (kelime, bant, cevap) |
| C9 | Seviye ölçümle değişince: kullanıcı şimdiki yolculuğunda hiç hikâye bitirmediyse yeni seviyenin yolculuğu atanır; bitirdiyse yolculuk kalır, sıradaki yolculuk yeni seviyeden gelir |
| C7 için | Uygulamanın "ilk ölçüm" durumunu ayırt etmesi için gereken bilgi sunucuda yoksa (önceki seviye hiç seçilmemiş varsayılan mı) cevaba eklenir |
1.0.2 ve derleme 49 istemcileri bozulmamalı; testle göster.

### 3. Sınav sistemi, canlı veri (yedekli betik)
- **Dört yeni B1 parçası** eklenir: `raporlar/2026-11-22_sinav_sistemi_bu_surum.md` bölüm 4. Doğru şıkkın konumu karıştırılır; var olan mekanik denetimden geçmeli. **Önce ekle, sonra** B1 parçaları **38, 39, 40, 41**'i kapat (silme). 37 ve 42 kalır.
- **29 belge sorusunun kökü:** `raporlar/veri_2026-11-22/belge_sorulari_yeni_kokler.md` (şıklar aynı; dosyanın sonunda bir şık düzeltmesi).
- Tohum dosyaları da aynı hâle getirilir (sonraki yayın geri almasın).
- Doğrulama: canlıdan B1 için 6 etkin parça; 29 kökten üçünü rastgele oku.

### 4. Sınav sistemi, uygulama (`feat/journey-core`)
Metinler: `raporlar/2026-11-22_sinav_sistemi_bu_surum.md` bölüm 2 ve 3.
| # | İş |
|---|---|
| C6 | "Seviyeni belgele"de sorular tek tek gösterilir (ısınma dahil); cevaplar adım sonunda toplu gider; sunucu değişmez. İlerleme göstergesi sayı değil çizgi |
| C7 | Yeniden ölçme sonucu: altı durumun başlığı ve alt satırı, seviye cümleleri, tek ana düğme "Seviyene göre hikâye: {hikâye}" (sıradaki hikâyenin kapağı). "Seviyen düştü" hiçbir yerde yok |
| C8 | Belge sonucu: 100 üzerinden puan görünmez; "{seviye} seviyesinin başındasın / ortasındasın / sonuna yaklaştın". Belgede sayı yok. Profil seviyesi yükselmediyse ek satır (bölüm 3) |
Metinler çeviri dosyasına; İngilizce karşılıklarını sen yaz, ekip sonra bakar.

### 4b. Ana sayfa slaytı ve görüntüdeki düzeltmeler (22 Kas 14:45)
Tam talimat: **`ortak/editor_gorevi_2026-11-22_ana_sayfa_slayt.md`** (yedi madde: iki satır başlık kalır, Türkçe ad satırı, üst satıra seviye, tür adı, "Başka hikâyeler" başlığı, "3 günlük seri", ana sayfa açılış kaynağı ölçümü). Yarım gün.

### 5. Derleme 50 sürüşü
Daldaki her şey bu derlemede: ana sayfa yolculuk kartı, kariyer sayfası (yol rozet kenarında kesiliyor), günün quizi, yorum ekranı, yeniden ölçme `offer`, bildirimden kapak, kelime defteri açıklama ölçümü, "Seviyeni belgele" görünür, önceki düzeltmeler (T15, T17, T18, seslendirme, bildirim ve kart ölçümleri, ayar uyarısı, `d2228a73`) ve yukarıdaki 4.
- SE 3 + büyük yazı görüntüleri `raporlar/ekran_2026-11-22/` içine: kariyer (277 XP, %0, %92), ana sayfa (hak var / hak kullanılmış / ikinci yolculuk), yolculuk sayfası, yorum ekranı, günün quizi (sekme, soru, üç sonuç başlığı), iki seviye testi (ilk ekran, bir soru, sonuç durumları).
- **Kendi gözünle şunlara bak ve bozuksa düzelt:** kariyer yolunun rozetle birleştiği uç (boşluk ya da bindirme), yüzde etiketinin rozete ve ada binmemesi, büyük yazıda kayıt kartının rozeti örtmemesi, SE 3'te düğmelerin kaydırmadan görünmesi, hiçbir metnin kesilmemesi.
- "Geri dön" bildirimini bir test hesabına gerçekten gönder; dokununca hikâyenin kapağı açılıyor mu (soğuk açılışta da).
- Görüntüleri gönder, **ekibi bekleme:** kendi denetimin temizse derleme 50'yi TestFlight'a ve Play dahili teste yükle. Ekip görüntülere sonradan bakar; bulgu çıkarsa derleme 51.
- `ortak/surum_notlari_1.0.4.md` güncel mi, bak; değilse güncelle.

### 6. Mehmet'e bırakılanlar (raporun sonuna hazır liste olarak yaz)
Telefonda: Android'de gerçek satın alma, Google'da uygulama içinden iptal, gerçek promosyon koduyla Premium, yolculuk sayfası canlı sunucuyla. Mağazaya gönderim. Play Console'da eski kapalı test kanalını duraklatma.

## Bu sürümde YOK (dokunma)
Profil resmi ve hazır resimler · yolculuk rozetleri · hesap açma teşviki · ana sayfa sadeleşmesi taslağı · belge testinde kelime adımı (C10) · quizde "aynı türden çeldirici" · Ada metni (1023) · S10–S15 salt okuma raporları. Hepsi sonraki sürüm; Mehmet: "sonra düşünürüz."

## Rapor
`raporlar/2026-11-22_editor_surum_kalan_isler_raporu.md`. En başta: Mehmet'in çalıştırması gereken komut varsa o; sonra her madde için bitti / yapılmadı ve neden; kendi başına verdiğin kararlar; canlıda doğruladıkların. İş listesinin "Şu anki durum" tablosunu sen güncelle.
