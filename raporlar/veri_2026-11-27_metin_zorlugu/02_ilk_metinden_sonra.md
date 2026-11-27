# 2. İlk metinden sonra: ikinci metne başlama ve geri gelme

**Kaynak:** canlı veritabanı, salt okuma, 27 Kasım 2026 15:45; yalnız müşteri hesapları.

## Nasıl sayıldı
- **İlk metin:** müşterinin en erken açılmış okuma kaydı (300 müşterinin okuma kaydı var).
- **İkinci metne başlama:** başka bir metin için de okuma kaydı açılmış olması (ne zaman olduğuna bakılmadı).
- **Geri gelme:** ilk metni açtığı günden sonraki 1. günde, tam 7. günde ve "7. gün ya da sonrası"nda uygulamadan en az bir olay gelmesi. Payda, o güne ulaşmış (süresi dolmuş) müşteriler. Günler Türkiye saatiyle.

## Sonuç
| | İlk metni bitiren | İlk metni bitirmeyen |
|---|---|---|
| Müşteri | 219 | 81 |
| İkinci metne başlayan | 120 (**%55**) | 21 (**%26**) |
| Ertesi gün gelen | 67 / 210 (%32) | 8 / 80 (%10) |
| Tam 7. günde gelen | 19 / 172 (%11) | 1 / 64 (%2) |
| 7. gün ya da sonrasında gelen | 41 / 172 (%24) | 7 / 64 (%11) |

- İlk metni bitiren, ikinci metne iki kat sık başlıyor ve ertesi gün üç kat sık geri geliyor.
- **Bu bir neden-sonuç kanıtı değil:** ilk metni bitirenler zaten daha istekli olanlar olabilir. Ama yön dört ölçüde de aynı.
- İlk metni bitirmeyen 81 kişinin 60'ı bir daha hiçbir metin açmamış.

## İlk metin hangisiydi (en az 5 kişi)
| Kimlik | Metin | İlk metni bu olan | Bitiren | Bitirip ikinciye geçen | Bitirmeyip ikinciye geçen | 7. gün ya da sonrasında gelen |
|---|---|---|---|---|---|---|
| 916 | Two Cups | 105 | 81 (%77) | 48 | 4 | 18 / 88 |
| 1023 | Rabbit Island | 94 | 70 (%74) | 39 | 6 | 12 / 72 |
| 120 | Why Penguins Can't Fly | 61 | 40 (%66) | 17 | 7 | 14 / 61 |
| 1024 | The Village That Whistles | 11 | 5 | 4 | 3 | 2 / 6 |
| 1083 | Thirty-One Mornings | 9 | 4 | 2 | 1 | 1 / 4 |
| 124 | First Ramadan in London | 7 | 6 | 4 | 0 | – |

- Müşterilerin %87'sinin ilk metni üç metinden biri: Two Cups, Rabbit Island, Why Penguins Can't Fly. Metin kalitesi incelemesinde önce bu üçüne bakmak en çok kişiyi kapsar.
- **Why Penguins Can't Fly** ilk metin olarak en düşük bitirme oranına sahip (%66) ve bitirenlerin ikinciye geçme oranı da en düşük (17/40; Two Cups'ta 48/81). Bu metin görevdeki üç başlangıç metni arasında değil; 1.0.2'de başlangıç metniydi.
- 1024, 1083 ve 124 için sayılar küçük; yüzde yazılmadı.
