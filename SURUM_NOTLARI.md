# TBA-BOT Sürüm Notları

## v1.3 — 2 Temmuz 2026

### Düzeltme
- **Çift "Keşfet" butonu hatası:** Keşif ekranında iki Keşfet butonu göründüğünde bot bazen yanlış olana (soldakine) tıklıyordu. Artık tüm eşleşmeler bulunuyor ve her zaman en sağdaki tıklanıyor.

### Arayüz
- **Launcher yeniden tasarlandı:** İnce-uzun dikey düzen, DEF Unity logosu, gece laciverti + mor + altın tema, belirgin (altın çerçeveli) giriş alanları, altta genişleyen log, 📌 "Üstte tut" seçeneği.
- **Canlı istatistikler genişletildi:** Durum, Tur (toplam), Başarılı, Hata (toplam), Başarı yüzdesi ve Süre.
- **Dil paketi (TR / EN / FR):** Sağ üstteki seçiciden anında dil değişimi; seçim hatırlanır (`launcher_config.json`). Bot logları İngilizce kalır, yalnızca arayüz çevrilir.
- **Siyah log penceresi (overlay) launcher'dan başlatılınca gizli:** tüm veriler launcher ekranında; scriptler elle çalıştırılırsa overlay görünür kalır.
- **Konsol pencereleri kaldırıldı:** `calistir_*.bat` silindi; bot tamamen penceresiz çalışır.
- **Log akışı düzeltildi:** pythonw boru tamponlaması yüzünden launcher'a veri akmaması giderildi (`-u` + flush + dosya tail emniyet ağı).

### Kurulum (TBA_Setup_v1.3.exe)
- Kurulum sihirbazı DEF Unity temasına geçirildi: logo, ikon (tba_icon.ico) ve launcher ile aynı renkler.
- Oyun penceresi konumlandırması uyarlanabilir: her ekran çözünürlüğünde oyun solda, launcher sağda örtüşmeden durur.

## v1.2 — 2 Temmuz 2026

### Performans
- **Tıklamalar hızlandı:** Her tıklamada 0.2 sn süren kırmızı işaret penceresi kaldırıldı; bot artık doğrudan tıklıyor. İşaretleri görmek istersen `TBA_DEBUG_CLICKS=1` ortam değişkeniyle debug modu açılabilir.

### Güvenilirlik
- **"March bitti" çift doğrulama:** Bot artık tek bir kaçırılmış kareye bakarak "birlikler döndü" demiyor; art arda iki ayrı kontrol gerekiyor. Popup/animasyon kaynaklı erken tur bitirme hataları giderildi.
- **Gerçek oyun yeniden başlatma:** 10 ardışık hata olursa bot oyunu tamamen kapatıp resmi launcher üzerinden yeniden açıyor (PLAY'e basıp mağaza popup'ını kapatarak). Önceden sadece ESC basıyordu ve donmuş oyunu kurtaramıyordu. 15 dakikalık periyodik tazeleme eskisi gibi yumuşak (ESC) kalıyor.

### Yeni özellik
- **Çoklu monitör desteği:** Bot, oyun penceresi hangi monitördeyse onu izliyor ve tıklamaları doğru monitöre gönderiyor. Oyun ikinci monitördeyken pencere artık ana ekrana çekilmiyor. (Arka plan Help All tıklayıcısı dahil.)
- **Log temizliği:** `log/` klasöründeki 30 günden eski kayıtlar açılışta otomatik siliniyor.
- **Launcher canlı istatistik paneli:** Durum (görevde/bekliyor/döndü...), tur sayısı, hata sayısı ve geçen süre artık launcher ekranında canlı gösteriliyor; log satırları çift basılmıyor.
- **Konsol pencereleri kaldırıldı:** Siyah komut satırı açan eski `calistir_epic.bat` / `calistir_log.bat` silindi — bot yalnızca launcher üzerinden, arka planda penceresiz çalışıyor.
- **Launcher yeniden tasarlandı:** İnce-uzun dikey düzen, DEF Unity logosu, gece laciverti + mor + altın tema, belirgin giriş alanları, altta genişleyen log.
- **Canlı istatistikler genişletildi:** Tur (toplam), Başarılı, Hata (toplam) ve Başarı yüzdesi.
- **Dil paketi (TR / EN / FR):** Sağ üstteki seçiciden anında dil değişimi; seçim hatırlanır (`launcher_config.json`). Bot logları İngilizce kalır, yalnızca arayüz çevrilir.
- **Siyah log penceresi (overlay) gizlendi:** Launcher'dan başlatılan botlarda ekranın köşesindeki siyah log penceresi artık açılmıyor; loglar ve Stop launcher ekranında. Script elle çalıştırılırsa overlay eskisi gibi görünür.

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
