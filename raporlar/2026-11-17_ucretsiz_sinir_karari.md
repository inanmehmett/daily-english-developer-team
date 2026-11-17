# Ücretsiz sınır – ekip kararı (Mehmet onayına)

**Tarih:** 17 Kasım 2026 · Tek geçiş; üyeler kurgusaldır. **Dayanak:** `raporlar/2026-11-17_ucretsiz_sinirlar_verisi.md` (268 müşteri; alıcı/tamamlamayan 14 kişi → hipotez).

## Veri ne diyor
- Üç sınırdan ikisi fiilen yok: okuma sayacı hiç çalışmıyor; çeviri hakkı yalnız sözlükte olmayan kelime ve önbellekte olmayan cümlede düşüyor (son gün ortanca 3, 25'e ulaşan 1 kişi).
- Defter: 7 günlük sınırsız dönemden yararlananlar gidiyor; 15'i geçen 17 kişiden 2'si 7. günden sonra döndü. Sınırsız hafta, kalmayan kullanıcıya hediye.
- Kilit tek gerçek temas: 69 kişi kilide dokundu (dizi bölümü 44 kişi / 241 dokunuş), ama kilitli önizlemede "Premium"a basan 5 kişi.
- Onboarding paywall'u "Günlük 3 okuma limiti kalkar" diyor; böyle bir sınır yok. Okuma sonrası pencere "1 okuma hakkın kaldı" yazabilir. İkisi de yanlış söz (README madde 9).

## Üyeler
- **Sean:** Kullanan kullanıcı ilk günlerde bir duvar görmeli. En temiz duvar: her dokunuş sayılsın.
- **Paul:** Her dokunuş sayılırsa 25'te ilk metnini sınıra çarpmadan bitirenler %73 (A1 %84, A2 %55); 20'de %65, 15'te %49. İlk metni bitirmek tutmanın anahtarı (D1: 3/58'e karşı 19/53). 25'in altına inmeyelim.
- **Nate:** 25 sayılınca 174 dokunan kişinin 74'ü en az bir gün sınıra çarpardı: gerçek bir satış anı. Sınıra çarpma olayları (çeviri, defter, kilit) mutlaka kaydedilsin; bugün hiçbiri kaydedilmiyor.
- **Don:** Sınıra çarpan ekran dürüst ve tek eylemli: "Bugünkü 25 kelimen bitti. Yarın yenilenir — Premium'la sınırsız." Metni okumaya devam edebilir; yalnız dokunma kapanır.
- **Dieter:** Kilitli önizlemede 156 açılışa 7 basış: teklif zayıf. Kilitli içerik ekranı Premium'un ne açtığını açıkça göstersin.
- **Nassim:** İki sınırı birden daraltıyoruz; etkiler ayrışmaz. Kabul edilebilir çünkü bugün sınır hiç yok ve satış sıfır; ama değişiklik tarihi kayda geçsin, 2 hafta sonra hem satış hem ertesi gün dönüşü okunur. Dönüş belirgin düşerse önce dokunma sınırı gevşetilir.

## Karar önerisi
1. **Çeviri:** Kelime ve cümle, her dokunuş günde 25 haktan düşer (sözlük/önbellek ayrımı kalkar). Sayı aynı, sayma değişir.
2. **Defter:** "İlk 7 gün sınırsız" kalkar; ilk günden toplam 15 kelime.
3. **Okuma:** Çalışmayan okuma sayacı ve ona bağlı ekranlar kaldırılır. Okumayı yalnız kilit + günlük açılış sınırlar.
4. **Yanlış sözler düzeltilir:** onboarding paywall'undaki "Günlük 3 okuma limiti kalkar" ve okuma sonrası "1 okuma hakkın kaldı".
5. **Sınır ekranları:** çeviri ve defter sınırı dolunca dürüst, tek eylemli teklif (paywall tetikleyicisi `limitReached`).
6. **Kilitli içerik teklifi** güçlendirilir (Dieter + Don tasarımı, ayrı iş).
7. **Ölçüm:** `limit_reached` olayı (tür: çeviri/defter/kilit), sunucu ve istemci.
8. **Paywall:** SE 3 ve büyük yazıda seçili planın görünmemesi düzeltilir (engelleyici).
9. **Geri alma kuralı:** değişiklik yayından 2 hafta sonra okunur; ertesi gün dönüş belirgin düşerse önce dokunma sınırı gevşetilir.

Mevcut kullanıcılar: yeni kurallar herkese yayın gününden itibaren uygulanır; daha önce 15'ten fazla kaydedilmiş kelime silinmez, yalnız yeni kayıt kapanır.
