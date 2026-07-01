# TBA-BOT Sürüm Notları

## v1.1 — 2 Temmuz 2026

### Düzeltmeler
- **Common mahzen modu kilitlenmesi giderildi:** Bot, dış sayaç API'si (chest-counter) düşük değer bildirdiğinde sonsuza dek bekliyordu. Launcher'a "Kaynak kontrolünü atla" seçeneği eklendi (varsayılan açık, `--dr=1`). Kaynak kontrolü açık bırakılsa bile artık en fazla 30 dakika bekler, sonra çalışmaya devam eder (fail-open).
- **Pencere karışıklığı düzeltildi:** Bot, "Total Battle" ararken kendi launcher penceresini ("Total Battle Automation") yakalayıp onu taşıyabiliyordu. Artık kendi pencerelerini dışlıyor ve birebir "Total Battle" başlıklı oyun penceresini önceliyor.
- **Thread yarışı giderildi:** Arka plandaki "Help All" tıklayıcısı ana botla aynı hedef koordinatını paylaşıyordu; bot nadiren yanlış yere tıklayabiliyor ve rastgele çökme riski taşıyordu. Arka plan işi artık kendi bağımsız ekran tarayıcısını kullanıyor ve pencere açmadan tıklıyor.
- **Özel mahzen aramasında sonsuz döngü:** `find_special` aranan mahzeni bulamazsa sonsuza dek kaydırıyordu; 90 saniye zaman aşımı eklendi.
- **Limit iptali hatası:** 15 dakikalık güvenlik yeniden başlatması, `--limit` ile verilen kapanış kararını iptal ediyordu; artık korunuyor.
- **Citadel boş ordu hatası:** Asker doldurma başarısız olursa tur iptal ediliyor; bot artık boş orduyla saldırı denemiyor.
- Küçük düzeltmeler: `show_click_marker` NameError, `--speedups` parametresinin sayı olarak işlenmesi, argüman açıklamaları.

### Kurulum (TBA_Setup_v1.1.exe)
- **Eksik paketler eklendi:** `pytesseract`, `imutils`, `mss` kurulum listesinde yoktu; temiz kurulumda bot `ModuleNotFoundError` ile açılmıyordu. Üç paket de eklendi (hem sihirbaz hem `install_packages.bat`).
- **İlerleme çubuğu düzeltildi:** Çubuk artık kaba atlamalar yerine akıcı ilerliyor: Python indirmesi yüzdeyle, paketler tek tek ("Installing package 3/8: ...") gösteriliyor.
- Kurulum sihirbazı başlığında sürüm numarası gösteriliyor.

### Adlandırma
- Bot klasörü `tba-main_2025-11-13` → `tba-bot` olarak yeniden adlandırıldı.
- Kurulum dosyası sürümlü adlandırıldı: `TBA_Setup_v1.1.exe`.

## v1.0 — 24 Haziran 2026
- İlk paketlenmiş sürüm: crypt (common/rare/epic), citadel, help click, attack centered, troops scriptleri; Tkinter launcher; tek dosyalık kurulum sihirbazı (`TBA_Setup.exe`).
