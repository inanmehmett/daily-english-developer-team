# Ekip toplantısı: profil resmi (ve yolculuk rozetleri kararı)

**Tarih:** 22 Kasım 2026, 00:05 · Tek geçiş; üyeler kurgusaldır.
**Mehmet (21 Kas 23:56):** "Yolculuklar tespit edilip rozetler tasarlanacak. Bir de profil resmi meselesi. Bunu bu sürümde halletmek istiyorum. Ekip toplantı yapsın ve bu konuyu karara bağlayalım."
**Dayanak (koddan ve canlı veriden; yeni varsayım yok):** `2026-11-21_profil_ve_sahiplenme_mevcut_durum.md`, `2026-11-21_sahiplenme_verisi.md`.

## 1. Bilinenler
| Olgu | Kaynak |
|---|---|
| Profil resmi var: galeriden seç, fotoğraf çek. **Yalnız üyede.** Misafirde kamera düğmesi gizli; deneyen misafir kayıt ekranına gidiyor | kod |
| Müşterilerin %89'u misafir (324/365) | canlı veri |
| **Uygulamadan resim yükleyen müşteri: 0.** Resmi olan 7 kişinin resmi Google hesabından geliyor. 41 üyeden de yükleyen yok | canlı veri |
| Hazır karakter / avatar seçimi yok | kod |
| Resmi başkasına gösterecek tek yer liderlik tablosu; kapalı | kod |
| Misafirden üyeliğe geçenlerin %71'i ilk gün geçiyor; sonra neredeyse hiç | canlı veri |
| Kendi bir şey ekleyenler 7. günde daha çok dönüyor (%24 ile %11); çoğu okumadan geliyor, az veri | canlı veri |

**Sorunun adı (ekip):** kullanıcıların %89'unun kendine ait bir yüzü olamıyor; olabilen %11 de fotoğraf yüklemiyor. Bugünkü yol (yalnız fotoğraf, yalnız üye) kimseye yaramıyor.

## 2. Tartışma (kısa)
- **Don (UX):** 41 üyeden 0 yükleme iki şeyden biri: ya kimse fotoğrafını bir okuma uygulamasına koymak istemiyor ya da yükleme çalışmıyor. İkincisi dışlanmadan karar eksik kalır; editör üye hesapla gerçek telefonda baştan sona denemeli. Fotoğraf izin ister, emek ister, karşılığında kimse görmez. Tek dokunuşla seçilen hazır resim misafire de açılabilir.
- **Dieter (UI):** hazır resimler uygulamanın çizim diliyle aynı olmalı (rütbe rozetleri kodla çiziliyor; aynı yöntem, dosya yok). Az ve iyi: 12 resim. Rütbe rozetleriyle karışmamalı: rozet madalya, profil resmi karakter.
- **Nate (büyüme):** fotoğrafı misafire açmak kayıt nedenini azaltır; tersine, "kendi fotoğrafın" üyeliğin somut bir karşılığı olabilir. Bugün fotoğraf düğmesinden kayıt ekranına gideni sayamıyoruz; ölçü eklenmeli.
- **Charles (öğrenme):** onboarding uzamasın. Seçim ilk hikâyeden önce istenirse okumayı geciktirir.
- **Paul (ses):** "avatar" demeyelim; "profil resmi". Karakter adları Türkçe ve sade.
- **Risk (hepsi):** misafire fotoğraf yüklemeyi açmak: liderlik tablosu dönerse denetimsiz fotoğraflar herkese görünür; atılıp bırakılan misafir hesaplar için depolama. Hazır resimde iki risk de yok.

## 3. Kararlar (derleme 50)
| # | Karar |
|---|---|
| P1 | **Herkes (misafir dahil) hazır 6 profil resminden birini seçebilir (önce 12'ydi; bkz. bölüm 5).** Tek dokunuş, izin yok, kayıt yok. Resimler kodla çizilir, rütbe rozetlerinin çizim diliyle; okuma dünyasından karakterler (ör. baykuş, kedi, tilki, kaplumbağa, kitap kurdu, çay bardağı, fener, pusula…). Son listeyi Dieter çizimleri görünce onaylar |
| P2 | **Fotoğraf yükleme üyede kalır.** Misafirde seçim sayfasının son karesi "Kendi fotoğrafını ekle": dokununca bugünkü "hesabını koru" ekranı açılır; kayıttan sonra fotoğraf seçimine döner |
| P3 | **Giriş yeri:** profil sayfasında resme dokunmak seçim sayfasını açar (misafirde de; bugünkü gizli kamera düğmesinin yerine herkes için küçük kalem işareti). Onboarding'e adım eklenmez |
| P4 | **Bir kez hatırlatma:** kullanıcı ilk hikâyesini bitirdikten sonraki ilk profil açılışında resmin çevresinde tek seferlik hafif bir vurgu ve "Bir profil resmi seç" satırı. Pencere açılmaz, bildirim gitmez |
| P5 | **Seçilmemişse** bugünkü görünüm kalır (baş harf). Kendiliğinden rastgele resim atanmaz |
| P6 | **Resim göründüğü her yerde aynı:** profil, ana sayfa kişi kartı (bugün resim gösteriyorsa), liderlik tablosu (dönerse). Premium tacı resmin üstünde kalır |
| P7 | **Saklama:** seçim sunucuda tutulur (cihaz değişince ve üyeliğe geçince kaybolmaz). **1.0.2 kullanıcısı bozulmamalı:** eski sürüm bu değeri resim adresi sanıp kırık resim gösterecekse ayrı alanda tutulur |
| P8 | **Ölçü:** seçim sayfası açıldı, resim seçildi (hangisi), "Kendi fotoğrafını ekle"ye basıldı, oradan kayıt tamamlandı, fotoğraf yüklendi. İki hafta sonra bakılacak: seçenlerin oranı ve 7. gün dönüşü (hipotez; az veri) |
| P9 | **Önce doğrulama:** editör üye hesapla gerçek telefonda fotoğraf yüklemeyi baştan sona dener (iOS ve Android). Bozuksa düzeltme bu sürüme girer |
| P10 | **Bu sürümde yok:** karakter için kazanılan eşya (altyapı yok), misafire fotoğraf yükleme, liderlik tablosunun açılması |

## 4. Yolculuk rozetleri (Mehmet: "yolculuklar tespit edilip rozetler tasarlanacak")
- Karar kesin: **her yolculuğa bir rozet**, yolculuk bitince verilir; ara rozet yok; rozet bir şey açmaz.
- Sıra: (1) editör canlıdaki yolculukları döker (bugün 6: üç başlangıç, New in Town, Coffee Shop Stories, World Cities; ad, seviye, durak sayısı, ücretsiz durak sayısı) ve S10–S12'yi cevaplar; (2) Paul rozet adlarını ve tek cümlelik metinlerini yazar (ses kuralı: Türkçe, büyük harf ve "LEGEND" yok); (3) Dieter her rozetin çizim tarifini verir (yolculuğun temasından: şehir, kafe, dünya şehirleri), editör kodla çizer; (4) rozet yolculuk sayfasında yolun sonunda durur; (5) görüntüler ekibe gelir.
- Derleme 50'ye **girmez** (sunucu ve çizim işi; profil resmi bu sürümün işi). Sıradaki sürüm.

## 5. Düzeltme (Mehmet 00:03: "12 fazla değil mi?") – 6 resim
Mehmet haklı; ekip 12'yi 6'ya indirdi. Gerekçe: (1) resimler dışarıdan gelmiyor, editör kodla çiziyor; 12 çizim bu sürümü geciktirir ve kaliteyi düşürür; (2) 6 resim SE 3'te kaydırmadan tek bakışta görünür (iki sıra, üçer); (3) az seçenek hızlı seçilir. Çok seçilirse sonraki sürümde eklenir (P8 hangisinin seçildiğini ölçüyor).
**Kaynak:** hazır paket ya da üretilmiş görsel kullanılmaz (lisans ve çizim dili uyumsuzluğu); rütbe rozetleri gibi kodla, vektör çizilir; dosya eklenmez, her boyutta net.
**Tasarım (Dieter):** tek kalıp, altı karakter. Düz renkli daire zemin (uygulamanın paletinden altı ayrı renk); ortada yalnız baş, önden; iki-üç düz renk, kalın yuvarlak hatlar, gölge ve ayrıntı yok; 32 pt'de (ana sayfa) de tanınır olmalı. Karakterler: baykuş, kedi, tilki, kaplumbağa, ayı, tavşan. Gözlük, kitap gibi eşya yok (sonraki sürümlerde kazanılan eşyaya yer kalsın). Rütbe rozetleriyle karışmaması için madalya biçimi, kurdele ve altın rengi kullanılmaz. Premium tacı resmin üstünde durduğu için karakterlerin tepesi sade.
