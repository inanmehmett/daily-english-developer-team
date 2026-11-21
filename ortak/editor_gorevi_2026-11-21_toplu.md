# Editör görevi: 21 Kasım toplu iş

**Veren:** ekip (Mehmet "editöre verelim" dedi, 21 Kas 12:09). **Dayanak:** `raporlar/2026-11-21_sadik_kullanicilar_ekip_karari.md`, `ortak/guncel_is_listesi.md`.
**Sıra önemli.** 1.0.4'ü geciktirecek hiçbir şey yok: A ve B sürüm yolunda, C–E sürümü beklemez ve derleme 50'ye girmez.
**Dokunulmaz:** canlıya yazma, PR birleştirme, üretime yayın, mağaza gönderimi yalnız Mehmet'in açık sözüyle.

## A. Sunucu PR #15 (yayından önce)
1. "Geri dön" bildirimi üç cevapsız susturma kuralının **dışında** kalsın (deneme bitiş uyarısı gibi).
2. "Geri dön" son etkinlikten 3, 7, 14 gün sonra **öbür türlerin önünde** gitsin; o gün başka tür gitmesin. 30. gün kalsın.
3. Bırakmış kişiye (3 cevapsız) kelime tekrarı ve günün quizi gitmez; bu zaten var, değişmesin.
4. Tam test koşusunu tekrarla (düzeltmeden sonra yalnız kısmi koşulmuştu). Sonucu yaz.
5. Yayınlama. Hazır olunca Mehmet'e "PR 15 hazır" de.
"Geri dön" metinlerini Paul yazacak; şimdilik mevcut metin kalır.

## B. Açılışta kendiliğinden satın alma ekranı (yalnız inceleme, sonra en küçük düzeltme)
Sadık kullanıcı raporunda 1 numaraya uygulama açılır açılmaz, bir şeye dokunmadan satın alma ekranı çıkmış (sürüm 1.0.2).
1. 1.0.4 kodunda, kullanıcı bir şeye dokunmadan açılışta teklif açan bir yol var mı? Hangi kural, hangi koşul?
2. Varsa: onboarding sonu teklifi dışında hepsi kapansın (tek anahtar yeter). Karar: satış anı bitişte ve kullanıcının dokunduğu kilitte; kapıda değil.
3. Yoksa yalnız "yok" yaz, hangi dosyalara baktığını ekle.
Derleme 50'ye girer.

## C. Dizilerin ilk bölümü (yalnız sayı, canlıya yazma yok)
Kaç dizi var; her birinin ilk bölümü hangi seviyede, kaç kelime, merak cümlesi dolu mu. İlk bölümler ücretsiz olursa seviye başına ücretsiz metin sayısı ne olur (bugün A1 9, A2 8, B1 5, B2 2). Karışık seviyeli beş derleme (Game Day, Passport, Signal, Spotlight, Wild) ayrı gösterilsin.

## D. Ad ve açıklama dökümü (bekleyen)
`ortak/editor_gorevi_2026-11-21_seviye_quiz_guncelleme_verisi.md`, bölüm 5. Çıktı: `raporlar/veri_2026-11-21/adlar_ve_aciklamalar.csv`.

## E. Kariyer sayfası okunabilirlik taslağı (kod değil, görüntü; derleme 50'ye girmez)
Mehmet'in ekran görüntüsü (277 XP, Çaylak kazanılmış) üzerinden Dieter ve Don'un bulguları. Ayrı dalda, gerçek ekranda, **aynı kullanıcı durumuyla** (277 XP) görüntü üret. Rütbe adları ve rozet çizimleri değişmez.

**Her iki seçenekte ortak:**
1. **Yol kenardan kenara.** Yol bir rozetin kenarından çıkar, sıradaki rozetin kenarında biter; hiçbir nokta rozetin üstünden ya da altından geçmez (Mehmet).
2. **Yol dolar.** Geçilen kısım dolu ve renkli, kalan kısım noktalı. Kullanıcının bulunduğu yerde küçük bir işaret (bayrak buraya taşınabilir). 277 XP, Çaylak (200) ile Meraklı (900) arasında yolun %11'i.
3. **Sıradaki rütbe öne çıkar.** Meraklı yarı renkli, çevresinde dolan halka, altında "Sıradaki: Meraklı". Uzak rütbeler daha küçük ve soluk, **kilitsiz**.
4. **Alt şerit tek cümle.** İlerleme çubuğu ve "Meraklı'ya yaklaşık 5 günlük okuma kaldı". "~" ve ok yok. Kalan XP 60'ın altındaysa `ortak/uygulamanin_sesi.md` tablosundaki cümle.
5. **Üst kenar.** En üstteki rozet durum çubuğunun altında kesilmesin; geri düğmesi rozetle çakışmasın.
6. **Arka plan sakinleşsin.** Üçgen dağlar yolla karışmasın (daha soluk ya da kaldırılmış; hangisi temizse).
7. **Kayıt kartı.** Başlık "İlerlemeni güvene al", alt satır "Kayıt ol; rütben ve ilerlemen cihaz değişse de seninle kalsın." Kart yolu kapatmayacak yükseklikte.

**İki seçenek:**
- **E1, kapısız:** yalnız yukarıdakiler.
- **E2, eşikli:** sıradaki rütbenin (Meraklı) yolun bağlandığı kenarında küçük bir temsili kapı/eşik işareti; kilidin yerini alır. Uzak rütbelerde kapı da kilit de yok.

**Görüntüler** (`raporlar/ekran_2026-11-21/`): bugünkü hâl, E1, E2 yan yana tek pano; SE 3 ve büyük yazıda E1 ve E2 birer kare; bir de eşikler 20 / 350 / 1.000 olsaydı aynı kullanıcı (Meraklı'ya 73 XP) nasıl görünürdü, tek kare (yerelde, sunucu değeri değişmeden).
Ölçerek yaz: sıradaki rütbe adının zeminle karşıtlığı, alt şerit yazı boyu, en küçük dokunma alanı.
Karar Mehmet'in; onay olmadan ana dala girmez.

## F. Güncelleyen eski kullanıcı ne görecek? (sürüm yolunda, B'den sonra; derleme 50 adayında)
Sadık 17 kişinin 16'sı eski sürümde; 1.0.4 asıl onlara lazım. Yeni kullanıcı akışı sınandı, **güncelleyen kullanıcı sınanmadı.**
1. Eski sürümde okuma geçmişi olan bir hesapla (başlangıç hikâyelerini bitirmiş, birkaç günlük metin okumuş, onboarding'i eskiden tamamlamış) 1.0.4'ü aç. Ana sayfada yolculuk kartı çıkıyor mu, "sıradaki hikâye" dolu mu, "Senin Yolculuğun" sayfası boş mu kalıyor?
2. Başlangıç yolculuğunu zaten bitirmiş kişide sıradaki ne? Boş kart ya da yalnız kilitli metin çıkıyorsa bu sürümü durduran bir bulgudur; raporla, çözümü ekip söyler.
3. Bu kişiye onboarding sonu teklifi ya da başka bir tanıtım yeniden çıkıyor mu? Çıkmamalı.
4. Günlük hakkını kullanmış kişide ana sayfa "yarın açılacak"ı ve Premium kapısını gösteriyor mu?
Yerelde, canlı verinin kopyasıyla ya da elle kurulmuş hesapla; canlıda hesap açma yok. Üç durumun ekran görüntüsü.

## G. Ölçüm var mı? (yalnız doğrulama)
Sürümden sonra şunları sayabilecek miyiz: yolculuk kartı gösterildi / dokunuldu; uygulama açıldı ama metin açılmadı oturumu; "Yarın hatırlat" seçildi; bitiş ekranında Premium kapısına dokunuldu. Eksik olan varsa adını yaz; küçükse derleme 50'ye ekle, büyükse yalnız raporla.

## H. Metin (derleme 50)
Ayar sunucuya yazılamazsa çıkan uyarı: "Ayarın bu telefonda kayıtlı, ama sunucuya ulaşamadık. Birazdan yeniden dener misin?" (Paul; eski: "Ayarlar telefonda kaydedildi ama sunucuya ulaşılamadı. Biraz sonra yeniden kaydet.")

## I. Sahiplenme verisi (salt okuma; sürümü beklemez, en sona)
Mehmet (21 Kas 12:23): "Profil resmi yükleyen hiç kullanıcı yok sanırım. Kullanıcı hesabını, karakterini sahiplensin istiyoruz." Karar için sayılar:
1. Müşterilerin kaçı misafir, kaçı üye (e-posta / Apple / Google)? Misafir profil resmi yükleyebiliyor mu, adını değiştirebiliyor mu?
2. Profil resmi yükleyen kaç kişi? Adını girmiş kaç kişi (onboarding'de ve sonradan)? Ad nerelerde kullanılıyor?
3. Profil sayfasını açan müşteri oranı; "Üye ol" çağrısına dokunan ve üyeliği tamamlayan.
4. Kullanıcının **kendi eklediği** her şey: defter kelimesi, favori, yer imi, hedef, bildirim saati. Her biri için: kaç müşteri en az bir tane eklemiş; ekleyenlerle eklemeyenlerin 7. günde dönme oranı (az veri notuyla).
5. Defter sınırı (15): sınıra çarpan kaç müşteri var, çarptıktan sonra kaçı satın alma ekranını gördü, kaçı satın al'a bastı, kaçı ertesi gün döndü?
6. Profil ekranının bugünkü hâli, misafir ve üye için birer görüntü; kullanıcının değiştirebildiği her alanın listesi.
Çıktı: `raporlar/2026-11-21_sahiplenme_verisi.md`.

## Rapor
`raporlar/2026-11-21_editor_toplu_is.md`: A–I için ne yapıldı, ne yapılamadı, Mehmet'ten ne bekleniyor.
