### Canlı Dosya bazlı tarama
.\hayabusa-3.7.0-win-x64.exe csv-timeline --no-wizard --file "HEDEF_LOG_DOSYASININ_YOLU" --output tek_dosya_analizi.csv --min-level medium

### Offline Dosya bazlı tarama
.\hayabusa-3.7.0-win-x64.exe csv-timeline --no-wizard --file "C:\Analiz\Evidence\Security.evtx" --output offline_tek_dosya.csv --min-level medium

### Canlı tüm dosyaları tarama (Otomatik C:\Windows... gider)
.\hayabusa-3.7.0-win-x64.exe csv-timeline --no-wizard --live-analysis --output canli_tum_sistem.csv --min-level medium

### Offline tüm dosyaları tarama
.\hayabusa-3.7.0-win-x64.exe csv-timeline --no-wizard --directory "C:\Logs_Klasoru" --output offline_tum_klasor.csv --profile standard --min-level medium

----
==**`Araştırma Kısmı`**==
## Timeline Gözelemleme
**`Medium - High - Critical - Emergency Sıralaması yap`**
Rule Title --> sırala
Details --> incele
	- Parent --> Hangi uygulama
	- Proc --> neye sebep olmuş



**`Oturum Açma Özeti`**
.\hayabusa-3.7.0-win-x64.exe logon-summary --file "Security.evtx" --output logon_ozeti.csv
