# Okuma yolu – amaç, sınırlar ve karar testi

**Onay:** Mehmet, 17 Kasım 2026. Okuma yolu ve ona bağlı her karar bu dosyaya göre verilir. Bir öneri burada çizilen sınırlardan birini aşıyorsa ya öneri değişir ya da sınır Mehmet'in kararıyla değişir; sessizce aşılmaz.

## Amaç (sırasıyla)
1. **Kararsızlık yok.** Kullanıcı uygulamayı her açtığında ne yapacağını bilir; "şimdi ne yapayım" sorusu hiç doğmaz.
2. **Öğrenme.** Seviyesine uygun okur, kelimeyi döndüre döndüre pekiştirir, ilerlemesini gerçek veriyle görür.
3. **Satış.** Değeri yaşamış ve ilerlemesini görmüş kullanıcıya, doğru anda, kibarca Premium sunulur.

## Döngü
Bütün özellikler tek bir döngünün parçasıdır; her adımın sonunda tek bir sonraki adım gösterilir.

**Bugünün durağı (okuma) → kısa pekiştirme (baktığı kelimeler / metin sonu quiz) → bitiş ekranı: yolculuk ilerlemesi + sıradaki durak → (ücretsizde) yarın açılır / (Premium'da) devam → ertesi gün bildirim: durağın açıldı.**

Döngüde yeri olmayan özellik ana yolda görünmez: ya döngüye bağlanır ya ikincil yerde kalır ya kaldırılır.

## Sınırlar

**Karar yükü**
- Her ekranda tek ana eylem. Ana sayfanın ilk kartı daima "bugünün durağı".
- Kullanıcıya bırakılan kararlar yalnız ikisi: "bugün bunu değil" (sınırlı) ve "devam / yarın".
- Yolculuk ve seviye uygulama tarafından atanır; değiştirmek mümkün ama öne çıkmaz.
- Onboarding'e soru ya da ekran eklenmez.

**Özellikler**
- Yeni özellik eklemeden önce mevcut özellik döngüye bağlanır.
- Bir özellik döngüde bir adım değilse ana sayfada ve bitiş ekranında yer almaz.
- Her özelliğin varlık sebebi tek cümleyle söylenebilir ve ölçülür.

**Öğretim**
- Durak metni okurun seviyesine uyar: 50 kelimede bakış ve bitirme oranı izlenir; uymayan metin yoldan çıkar ya da yer değiştirir.
- Kelime anlamı değişiklikleri bozmama kapısından geçer.
- Pekiştirme okunan metinden gelir (o metinde bakılan kelimeler), dışarıdan değil.
- Gösterilen ilerleme yalnız gerçek veriden: biten durak, deftere eklenen kelime, okunan gün; "daha az kelimeye bakıyorsun" en az 5 metin sonra ve gerçekten düşüyorsa.

**Satış**
- Premium'a giden yol baştan itibaren her zaman görünür (şerit, kilitli içerik, profil); doğrudan almak isteyen beklemez. Gerekçe: dört gerçek satın almanın üçü kayıttan sonraki ilk 3 dakikada, Premium şeridi görüldükten hemen sonra oldu (`raporlar/2026-11-17_satin_alma_anlari.md`). Ekranı kesen teklifler ise değer gösterildikten sonra ve sayılıdır.
- Ücretsiz sınır: başlangıç yolculuğu 4 durak + her yolculuğun ilk 2 durağı; günde bir ücretsiz durak. Premium'da hepsi açık, bekleme yok.
- Ana teklif başlangıç yolculuğu bitince (7 gün ücretsiz deneme); ikinci teklif yolculukların 3. durağında.
- Günde en fazla bir teklif. Her teklifte ücretsiz yol görünür ("yarın devam").
- Sahte aciliyet, geri sayım, gizli vazgeç düğmesi yok (README madde 9).
- Ücretsiz sınır yalnız ölçümle değişir.

**Ölçüm**
- Ana sayı: ertesi gün bugünün durağını açan kullanıcı oranı.
- Gelir sayıları: deneme başlatma, denemeden ödemeye geçiş, satış anı başına gösterim → satın alma.
- Korkuluklar: durak bitirme oranı, iptal, kullanıcı şikâyeti. Biri bozulursa değişiklik geri alınır.
- Sayılar uygulamanın kendi kayıtlarından okunur.

## Karar testi (her öneri için beş soru)
1. Kullanıcıya yeni bir karar yüklüyor mu? (Yüklüyorsa reddedilir ya da karar uygulamaya alınır.)
2. Döngüde hangi adım? (Adım değilse ana yola girmez.)
3. Öğrenmeye neyle hizmet ediyor?
4. Satış varsa: değer önce mi gösteriliyor, kibar mı, ücretsiz yol görünür mü?
5. Nasıl ölçülecek ve hangi sayıda geri alınacak?
