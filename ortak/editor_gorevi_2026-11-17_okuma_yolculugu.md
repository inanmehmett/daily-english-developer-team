# Editör görevi – "Okuma Yolculuğun" sayfası işe yarıyor mu (canlı veri, yalnız okuma)

**Tarih:** 17 Kasım 2026 · **Rol:** Nate Gümüş; itiraz Nassim Talip. Kurallar `ortak/editor_gorevi_2026-11-15_neden_kalmiyorlar.md` ile aynı: yalnız müşteri hesapları, pay/payda, 20 altı "az veri", kişisel veri yok, bağıntı ≠ neden, öneri yok.

## Koddan bilinen (Flutter `d5e4343`)
- Sayfa: `lib/features/career/presentation/pages/career_page.dart` (`/career`), başlık "Okuma Yolculuğun". XP'den türeyen rütbe haritası, düğümler, "~N günde" tahmini.
- Girişler ve `source` değeri: ana sayfa kişi kartı (`profile_card`), ana sayfa yolculuk şeridi (`target_card`), profil sayfası (`profile_page`), rütbe atlama kutlaması (`celebration`).
- Olaylar (`UserEvents`): `screen_view` + payload ekran adı `career_journey` ve `source`; `user_action` → `level_up_map_opened` (kutlamadan sonra harita animasyonu), `career_node_tap`; `conversion` → `paywall_impression` (`trigger` = `journey_chest` ya da `level_journey`).

## Sorular
1. **Erişim:** Kaç müşteri sayfayı en az bir kez açtı (toplam müşteriye oranı)? Kişi başı açılış dağılımı (1, 2–3, 4+). Kaynağa göre açılışlar.
2. **Kendiliğinden mi geliyor:** Kutlama dışı (`profile_card`, `target_card`, `profile_page`) açılışların payı. İkinci kez kendi isteğiyle açan kaç kişi?
3. **Sayfada ne yapılıyor:** `career_node_tap` sayısı ve kişi; sayfada kalma süresi (bir sonraki olaya kadar geçen süre, ortanca).
4. **Sonrasında ne oluyor:** Sayfadan sonraki 10 dakikada ilk olay: okuma başlatma, ana sayfa, paywall, uygulamadan çıkış (başka olay yok). Sayfayı açmayan benzer anlardaki kullanıcılarla karşılaştır (ör. ana sayfaya dönüşten sonraki ilk olay).
5. **Dönüşle ilişkisi (seçim yanlılığına dikkat):** Açanların ve açmayanların D1/D7 dönüşü, **ama aynı etkinlik düzeyinde**: yalnız ilk gün en az bir metin bitirenler içinde karşılaştır. Ham karşılaştırmayı tek başına verme.
6. **Kutlama sonrası harita:** `level_up_map_opened` kaç kişi; o oturumda okumaya devam eden oranı, kutlamanın haritaya gitmediği durumla karşılaştırılabiliyorsa.
7. **Gelir yüzeyi:** `journey_chest` ve `level_journey` paywall gösterimleri → satın almaya basma → tamamlama.

## Rapor
`raporlar/2026-11-17_okuma_yolculugu_verisi.md`: en üstte beş satır (kaç kişi görüyor, kendiliğinden dönen var mı, sonrasında okumaya yöneltiyor mu, dönüşle ilişkisi ne, gelir katkısı); her soru için tablo; itirazlar. Sonra dur.
