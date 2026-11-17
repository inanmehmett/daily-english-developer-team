# Editör görevi – Katalog dökümü (yolculuk adayları için), canlı veri, yalnız okuma

**Tarih:** 17 Kasım 2026 · **Rol:** Paul Ulus (içerik) + Nate Gümüş (veri). Kurallar önceki canlı veri görevleriyle aynı.

## Neden
Mehmet zaman sınırı olmayan, bitirilebilir okuma yolculukları (seriler) kurmak istiyor: şehirler, kültür, klasikler vb. Göç dosyalarından (`MigrationScripts/`) bir taslak liste çıktı ama canlıdaki durum (etkin mi, seviye, kelime sayısı) bilinmiyor. Mehmet Roma için 4 parça hatırlıyor; betiklerde 3 görünüyor.

## İstenen
1. **Tam katalog tablosu** (etkin metinler; etkin olmayanlar ayrı listede): id, slug, başlık, Türkçe başlık, kategori, seviye, kelime sayısı, bölüm sayısı, `SeriesId` / sezon / bölüm no, `IsStarterPack`, `IsDailyUnlock`, ücretsiz mi, `NextHook` dolu mu.
2. **Okunma:** her metin için müşteri okur sayısı, bitiren sayısı, 50 kelimede bakış ortancası (müşteri, 29 Eki'den beri).
3. **Gruplama:** slug önekine ve kategoriye göre gruplar (ör. `rome-*`, şehir belgeselleri, `legends-*`, `survival-*`, `passport-*`, `wild-*`, `literature-*`, `culture-*`, `daily-life-*`, `travel-*`, `famous-people-*`, Sherlock, `Series` tablosundaki diziler); her grubun seviye dağılımı (A1/A2/B1/B2+) ve metin sayısı.
4. **Roma:** "Rome" ya da "Roma" geçen bütün metinler (etkin/etkin değil).
5. **Seviye başına toplam:** her seviyede kaç etkin metin, kaçı ücretsiz, kaçı bir gruba/diziye ait.

## Rapor
`raporlar/2026-11-17_katalog_dokumu.md`: en üstte her seviye için "kaç metin, hangi gruplar" özeti; gruplar tablosu; tam katalog ek olarak (CSV de olur: `raporlar/2026-11-17_katalog.csv`). Öneri yok. Sonra dur.
