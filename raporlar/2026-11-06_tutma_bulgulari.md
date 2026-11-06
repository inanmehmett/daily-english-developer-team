# Tutma (retention) — push_opened ve bildirim kodu, gerçek durum tespiti

**Tarih:** 6 Kasım 2026 · **Hazırlayan:** Kent Bekçi + Nate Gümüş · **Sebep:** Büyüme planının 2. önceliği.

## Büyük bulgu: push_opened zaten kodlanmış — açık madde yanlış tanımlanmış

Haftalardır "push_opened ölçümü hâlâ kurulmadı" diye en üst öncelikte tutulan madde **yanlış bilgiye dayanıyormuş.** Mac'teki gerçek kodu okudum (Flutter + .NET backend), kod zaten tam zincirin iki ucunu da kurmuş:

- **Backend** (`DataAccess/DbModels/PushNotificationLog.cs`): Her gönderilen bildirim bir `Id` ile loglanıyor, bu `Id` bildirim yüküne (`notification_id` anahtarıyla) ekleniyor. Dosyanın kendi yorumu: *"uygulama dokunuşta bu kimlikle push_opened olayı yollar"* — yani bu altyapı tam olarak bunun için tasarlanmış.
- **Flutter** (`lib/core/services/fcm_service.dart`, `handleMessageTap`): Kullanıcı bildirime dokununca `notification_id`'yi okuyup `_analytics.trackPushOpened(...)` çağırıyor; bu da Firebase Analytics'e `push_opened` event'i olarak gönderiliyor (`lib/core/analytics/analytics_service.dart`, `pushOpenedEvent = 'push_opened'`).

**Yani istemci tarafı tamamen çalışır durumda görünüyor.**

## Gerçek sorun: Firebase Analytics'te hiç veri yok

Firebase konsoluna (Mehmet'in hesabıyla, mevcut tarayıcı oturumu) girip kontrol ettim: **son 28 günde hem Android hem iOS uygulamasında toplam olay sayısı 0, toplam kullanıcı 0** — yalnızca `push_opened` değil, `screen_view`, `session_start` gibi en temel otomatik olaylar da dahil **hiçbir Analytics verisi gelmiyor.**

**Bu, push_opened'a özel bir eksiklik değil — Firebase Analytics'in üretimde hiç veri toplamıyor olması, daha büyük bir sorun.** Olası nedenler (doğrulanmadı, varsayım değil açık liste):
- Analytics koleksiyonu uygulama tarafında kapalı/devre dışı olabilir.
- iOS'ta App Tracking Transparency / consent ayarı toplamayı engelliyor olabilir.
- Flutter'daki Firebase yapılandırması (google-services.json / GoogleService-Info.plist) bu konsoldaki projeyle eşleşmiyor olabilir (yanlış proje/app ID).
- Veri işleme gecikmesi (GA4'te genelde saatler içinde görünür, ama 28 günde hâlâ 0 olması bunu zayıf bir ihtimal yapıyor).

**Bu bir ihtiyaç tanımı değil, bir hata ayıklama (debug) işi** — ekip bunu "ne kodlanmalı" olarak tarif edemez, çünkü kod zaten yazılmış; birinin (Mehmet ya da editördeki asistan) uygulamayı çalıştırıp Firebase'in debug modunda (`adb shell setprop debug.firebase.analytics.app <paket>` ya da Xcode'da `-FIRDebugEnabled`) olayların gerçekten gönderilip gönderilmediğini canlı izlemesi gerekiyor.

## Güncellenmiş durum
- ~~push_opened ölçümü hâlâ kurulmadı~~ → **yanlış tanımlanmıştı. Kod var, veri akmıyor. Yeni madde: Firebase Analytics veri akışı neden sıfır, debug edilmeli.**
- Akşam seri bildirimi kodu (`UsesEveningHour`) — git geçmişinde zaten **committed** (`1c31040 feat(notifications): let users choose the streak reminder hour`), varsayıldığı gibi "uncommitted" değil. Derlenip derlenmediğini bu ortamda doğrulamaya çalıştım (ayrıntı aşağıda) — kesin sonuç alınamadı, ortam kısıtı.

## Derleme doğrulama denemesi — sonuç: ortam kısıtı, kod hatası değil
.NET backend kodunu bu bulut ortamına taşıyıp (`dotnet build`) gerçekten derlemeyi denedim:
- Proje **.NET 9** hedefliyormuş (ortamda kurulu olan 8.0 SDK yetersiz kaldı); .NET 10 SDK kurup geriye dönük hedeflemeyi denedim.
- Paket geri yükleme (NuGet restore) adımında **api.nuget.org bu ortamın ağ izin listesinde değil** (yalnızca npm/pip/crates/Go proxy gibi standart kayıt defterleri izinli) — bağlantı 403 ile reddedildi.
- **Sonuç: bu ortamda .NET backend'i gerçekten derleyip test edemiyorum** — bu, kodun kendisiyle ilgili bir sorun değil, yapısal bir ağ kısıtı. Daha önce "erişimin olması lazım" derken verdiğim söz kısmen tutmuyor: SDK kurabiliyorum ama paket indiremiyorum, yani gerçek bir .NET derleme doğrulaması burada mümkün değil. Mehmet'in kendi Mac'inde (`dotnet build` çalıştırarak) bunu doğrulaması gerekiyor — 2 dakikalık bir iş.

## Sıradaki somut adım
1. **Mehmet veya editördeki asistan:** Mac'te `dotnet build` çalıştırıp akşam bildirimi kodunun (zaten commit'li) hatasız derlendiğini doğrulasın — 2 dakikalık iş, ekip bunu buradan yapamıyor.
2. **Firebase Analytics debug:** Uygulamayı debug modunda çalıştırıp (yukarıdaki komutlarla) `push_opened` ve temel olayların gerçekten Firebase'e ulaşıp ulaşmadığı kontrol edilsin. Ulaşmıyorsa yapılandırma (google-services.json/GoogleService-Info.plist eşleşmesi, ATT izni) gözden geçirilsin.
3. Veri akmaya başlayınca Nate Gümüş haftalık raporuna "gönderilen bildirim / açılan bildirim" oranı eklenir.

## İtirazlar
- **Nassim Talip:** "Kod zaten var" demek "özellik çalışıyor" anlamına gelmez — kod yazılmış olması test edilmiş/doğrulanmış olması değildir. Bu rapor bunu zaten ayırt ediyor (kod var ≠ veri akıyor), ama ekip ileride "X zaten kodlanmış" bulgusunu "X çalışıyor" ile karıştırmamalı.
