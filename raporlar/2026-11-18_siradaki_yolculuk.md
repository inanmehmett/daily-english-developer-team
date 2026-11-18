# Başlangıç bitince: sıradaki yolculuk nasıl gelir?

> **18 Kas 17:40:** "Başka yolculuk seç" kaldırıldı; kilitte tek hikâye önerilir. Geçerli karar: `raporlar/2026-11-18_ilerleme_hissi_toplantisi.md`, D bölümü.


**Tarih:** 18 Kasım 2026, 16:10 · Tek geçiş; üyeler kurgusaldır. **Soran:** Mehmet ("4 hikâyelik seri güzel; bitince sıradaki yolculukları nasıl görecek, bir sonraki nasıl gelecek?")

## Mehmet'in editöre verdiği talimatlar (kayıt)
1. Onboarding'deki parmak izi %20 küçülür.
2. İlk teklifte ikinci yol yalnız **"Ücretsiz başla"** (ilk gün zaten 2 hikâye açık; "günde bir" yazmaması daha doğru).
3. Kariyer sayfasında "Çaylak Okur" bu sürümde kalabilir.
4. Ana sayfadaki "Senin yolculuğun" kartında sıradaki hikâyeye dokununca önce **kapak sayfası** açılır, okumaya oradan geçilir. (Nate: karttan kapak sayfasına, kapak sayfasından okumaya geçiş ayrı olaylarla ölçülür; kapak adımında kayıp büyükse yeniden bakılır. Onboarding'den ilk hikâyeye geçiş doğrudan kalır.)

## Bugün kodda ne var
- 3 başlangıç yolculuğu (4'er hikâye) ve 3 seviye yolculuğu: New in Town (A1, 10), Coffee Shop (A2, 12), Dünya Şehirleri (B1, 10). Bir yolculuk bitince sıradaki **kendiliğinden atanıyor**.
- 4. hikâye bitince: ilerleme kartı + 7 gün deneme teklifi.
- Seviye yolculuklarının ilk 2 hikâyesi ücretsiz, 3. kilitli.
- **Eksikler:** (a) kullanıcı sıradaki yolculuğun ne olduğunu bitiş anında görmüyor; (b) ücretsiz kullanıcı 3. hikâyede kilide varınca yolculuk kartı orada kalıyor; (c) üç seviye yolculuğundan sonrası tanımsız.

## Karar
**Kullanıcı sıradaki yolculuğu üç yerde görür:**
1. **4. hikâyenin bitişinde (ilerleme kartı):** "Başlangıcı bitirdin: 4 hikâye, {n} kelime, {n} gün" → altında **sıradaki yolculuğun kapağı, adı, hikâye sayısı ve merak cümlesi** ("Sıradaki yolculuğun: Coffee Shop Stories · 12 hikâye"). İki kapı: "7 gün ücretsiz: hepsini beklemeden oku" / "Yarın ilk hikâyeyle devam et".
2. **Ana sayfa kartı** yeni yolculuğa geçer: "Coffee Shop Stories · 0/12 · Sıradaki: The Empty Chair".
3. **Yolculuk sayfasında** yolun sonunda sıradaki yolculuk görünür (birleşik sayfa sürümü).

**Sıradaki yolculuğu kim seçer:** Ekip sıralar, kullanıcı karar vermek zorunda kalmaz; sıradaki kendiliğinden gelir. İsteyen için ilerleme kartında ve yolculuk sayfasında küçük bir "Başka yolculuk seç" bağlantısı: seviyesindeki diğer yolculuklar kapaklarıyla.

**Ücretsiz kullanıcı kilide varınca (3. hikâye) çıkmaz sokak olmaz:**
- Sürüm 1: kilitli hikâyede iki kapı: "Premium'la devam et" / "Bugünün ücretsiz hikâyesini seç" (bugünkü günlük açma havuzu). Yolculuk kartı kilitli hikâyeyi ve Premium yolunu göstermeye devam eder.
- Sürüm 2: ikinci kapı "Başka bir yolculuğa başla" olur: sıradaki yolculuğun ilk 2 hikâyesi ücretsiz. Böylece ücretsiz kullanıcının her gün okuyacağı bir hikâyesi, bizim de her yolculuğun 3. hikâyesinde yeni bir satış anımız olur; yarım kalan yolculuklar Premium'un değerini görünür kılar.

**Yolculuk zinciri (Paul, içerik işi):** Katalogdaki 287 metinden her seviye için sıralı yolculuk listesi çıkarılır (diziler, tematik gruplar); B2 ve üstü dâhil. Hedef: her seviyede en az 5 yolculuk. Yeni içerik geldikçe zincire eklenir. Bu liste Sürüm 2'den önce hazır olur.

## İtirazlar
- **Nassim:** Kullanıcıların 4. hikâyeye varıp varmadığını henüz bilmiyoruz; zincirin uzunluğu Sürüm 1 verisinden sonra önem kazanır. Sürüm 1'e yalnız 1. madde (ilerleme kartında sıradaki yolculuk) ve kilitte ikinci kapı girsin.
- **Don:** "Başka yolculuk seç" küçük bir bağlantı olarak kalmalı; ana eylem her zaman sıradaki hikâye.
