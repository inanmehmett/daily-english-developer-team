# Toplantı: "bus stop" ayrı mı, birlikte mi gösterilmeli

**Tarih:** 16 Kasım 2026 · Tek geçiş; üyeler kurgusaldır. Amaç yalnız çeviri kalitesi.
**Koddan bilinen:** Sunucu bir kalıp eşlerse uygulama dokunulan kelimenin vurgusunu kalıbın tamamına genişletiyor ve balonda kalıbın anlamını gösteriyor (`word_translation_result.dart`, `advanced_reader_page.dart` `_applyServerPhraseSpan`). Çok kelimeli kökler balonda "kalıp fiil" etiketi alıyor (`advanced_reader_page.dart` ~4276). **Doğrulanmadı:** "bus stop" cümlesinde "stop"a dokununca bugün balonda ne çıktığı.

## Tur
- **Paul (içerik):** Birlikte. Okur nesneyi öğrenmeli: "bus stop = otobüs durağı". Tek tek gösterilirse "stop"a dokunan büyük olasılıkla fiil olan "durmak"ı görür; "durak"ı tahmin etmek okura kalır. Birlikte gösterim "stop" isim olarak "durak" anlamını da öğretir.
- **Nassim (şüpheci):** Birlikte, ama yanlış alarm riski büyük. "The bus stops here" (otobüs burada durur) ve "the bus stopped" cümlelerinde "bus stop" eşleşirse okur yanlış bir bütün ezberler. Eşleşme yalnız "stop" isim olarak geçtiğinde olmalı.
- **Kent (geliştirme):** Tür etiketleyici zaten var; kalıp eşleşmesine "son kelime isim" şartı eklemek küçük iş. Sınama kümesine "bus stops / bus stopped / at the bus stop" cümleleri konur.
- **Dieter (arayüz):** Tek balon, iki kelime birlikte vurgulu. Ama bugün çok kelimeli her kök "kalıp fiil" etiketi alıyor; "bus stop" fiil değil. Birleşik isimler eklenecekse etiket türe göre olmalı ("birleşik isim") ya da hiç gösterilmemeli. Yanlış etiket de yanlış öğretir.
- **Don (UX):** "bus"a da "stop"a da dokunulsa aynı balon çıkmalı; okur hangi kelimeye dokunduğunu düşünmek zorunda kalmamalı. Deftere ekle denince "bus stop" kaydedilmeli, tek "stop" değil.
- **Nate (veri):** Kararın dayanağı gerçek balon. Önce bugün "stop" (ve benzer birleşik isimlerin parçaları) balonda ne gösteriyor, uygulamanın gerçek isteğiyle ölçülsün; parçalar doğru gösteriyorsa (birthday party → parti) eklemenin kazancı küçük.

## Karar
1. **"bus stop" birlikte gösterilir**: iki kelime tek vurgu, balonda "otobüs durağı"; "bus"a da "stop"a da dokunulunca aynı balon.
2. **Şart:** eşleşme yalnız son kelime isim olarak geçtiğinde ("at the bus stop" evet; "the bus stops here", "the bus stopped" hayır). Bu cümleler sınama kümesine girer.
3. **Etiket:** birleşik isim "kalıp fiil" diye etiketlenmez; türe göre etiket ya da etiketsiz.
4. **Defter:** "bus stop" bütün olarak kaydedilir.
5. **Kapsam ölçütü:** birleşik isim, parçalardan biri balonda yanlış anlam gösteriyorsa eklenir; parçalar doğru gösteriyorsa eklenmez. Karar listeden değil, gerçek balon ölçümünden verilir.
6. **Önce ölçüm:** editör aday birleşik isimlerde parçaların bugünkü balonunu ölçüp listeyi getirir.

## Şerh
- **Paul:** Parçalar doğru gösterse bile yaygın birleşik isimlerin (sıklık listesinden) birlikte gösterilmesini istiyor; okur için "bir nesne" bilgisi değerli. Karar Mehmet'in.
