# Editör görevi – ücretsiz sınırların uygulanması

**Tarih:** 17 Kasım 2026 · **Dayanak:** `raporlar/2026-11-17_ucretsiz_sinir_karari.md` · **Durum:** Mehmet onayından sonra başla.
Sunucu + Flutter. Canlı veritabanına yazma yok. Testler geçmeli; sürüm ve sunucu yayını kararı Mehmet'te.

1. **Çeviri sayımı:** `TranslateWord` (ve cümle çevirisi) her istekte, sözlük/önbellek sonucundan bağımsız, ücretsiz kullanıcının günlük hakkından 1 düşsün. Sınır 25 (değişmez). **İstisna (18 Kas düzeltmesi):** başlangıç yolculuğunun 4 durağında (seviyenin `IsStarterPack` metinleri) yapılan dokunuşlar haktan düşmez; sınır diğer bütün metinlerde işler. Sınır doluysa 402 + `limit_reached` kaydı.
2. **Defter:** `FreeUnlimitedWordDays` ilk 7 gün sınırsız kuralı kalksın; ilk günden toplam 15. Mevcut kayıtlar silinmez.
3. **Okuma sayacı:** Çağrılmayan okuma sayacı (`useReadingQuota`, `UseReadingQuotaOnCompletionAsync`, `use-reading-quota`, `freemium-status` okuma alanları) ve "günlük okuma hakkın bitti" sayfası kaldırılsın ya da devre dışı bırakılsın. Erişim kuralı (`CanAccessReadingTextAsync`) aynen kalır.
4. **Yanlış metinler:** Onboarding paywall'undaki "Günlük 3 okuma limiti kalkar" satırı ve okuma sonrası "X okuma hakkın kaldı" ifadesi kaldırılsın; Premium maddeleri gerçek sınırlarla yazılsın (sınırsız çeviri, sınırsız defter, tüm metinler, Premium sesler).
5. **Sınır ekranı:** Çeviri sınırı dolunca balon yerine kısa sayfa: "Bugünkü 25 kelimen bitti. Yarın yenilenir." + tek ana düğme "Premium'la sınırsız" + kapat. Defter için aynı yapı. Paywall tetikleyicisi `limitReached` (alt tür çeviri/defter). Okumaya devam edebilir.
6. **Ölçüm:** `limit_reached` olayı (tür: `translation`, `vocabulary`, `locked_content`) istemcide; sunucuda 402 dönerken AuditLog.
7. **Paywall düzeni:** SE 3 ve büyük yazı boyutunda seçili plan kartı ve düğme ilk açılışta birlikte görünsün (Dieter engelleyicisi).

Rapor: `raporlar/2026-11-1X_ucretsiz_sinir_uygulama.md` – ne değişti, testler, ekran görüntüleri (sınır ekranı, SE 3 paywall).
