### **SRUM**

C:\Windows\System32\SRU\SRUDB.dat

==**`SrumECmd.exe`**==
SrumECmd.exe -f "SRUDB.dat yolu" -r "SOFTWARE registry yolu" --csv "çıktı klasörü"

-f → SRUM veri tabanı (SRUDB.dat)
-r → SOFTWARE hive (kullanıcı & uygulama isimlerini çözer)
--csv → Çıktı klasörü


**SRUM Application Resource Usage**
Bir uygulama çalıştırıldığında diskte olmasa bile burada iz bırakır:
- Kullanıcı adı
- Çalıştırılan dosyanın tam yolu
- Silinmiş kötü amaçlı bir .exe’nin _çalıştırıldığını kanıtlarsın_


**SRUM Network Usage**
Bir uygulamanın ne kadar ağ trafiği yaptığını görmek.
- Process adı (ör: notepad.exe)
- User Name
- Bytes Sent / Bytes Received
- Interface (Ethernet / Wi-Fi)
- Zaman damgası


-----
### **Recycle Bin Artifacts**

C:\$Recycle.Bin\{Kullanıcı-SID}\$I######

- **$Ixxxxxx** → Metadata (silme bilgisi)
- **$Rxxxxxx** → Asıl dosyanın içeriği

==**`RBCmd.exe`**==
RBCmd.exe -d "C:\$Recycle.Bin" --csv "C:\Users\bayra\Desktop\results"

- `-d` → Recycle Bin dizini
- `--csv` → Çıktı klasörü


**$I ne içeriği**
- **Orijinal dosya adı**
- **Silinmeden önceki tam yol**
- **Dosya boyutu**
- **Silinme tarih ve zamanı**

----
### **Windows Search Index**

C:\ProgramData\Microsoft\Search\Data\Applications

==**`sidr.exe`**==
Sonlandır --> net stop wsearch
sidr.exe "C:\ProgramData\Microsoft\Search\Data\Applications" -f csv -o "C:\Users\bayra\Desktop\results"
Başlat -->net start wsearch

File_Report
- Dosya adı
- Orijinal yol
Internet_History_Report
* Silinmiş browser history geri kazanımı, şüpheli site erişimlerinin tespiti.
Activity_History_Report
- Hangi uygulamayı
- Hangi dosyayı
- Ne zaman açtığını


----

### **RDP Cache**

**C:\Users\bayra\AppData\Local\Microsoft\Terminal Server Client\Cache**

==**`bmc-tools.py`**==
**python bmc-tools.py -s "C:\Users\bayra\AppData\Local\Microsoft\Terminal Server Client\Cache" -d c:\Users\bayra\Desktop\results -b**

saldırganın RDP oturumu sırasında hangi ekranları gördüğünü ve hangi sistemlere bağlandığını görsel kanıt olarak ortaya koyar. **collage** dosyaları tüm resimleri birleşilmiş halini gösterir.

----

### **Thumbnail Cache**

**C:\Users\bayra\AppData\Local\Microsoft\Windows\Explorer**
==**`thumbcache_viewer`**==

silinmiş olsa bile dosyaların küçük önizleme görüntülerini koruyarak sistemde bir zamanlar var olduklarını kanıtlayan güçlü adli bulgudur. Kullanıcı bir dosyayı silse bile, o dosyanın küçük resmi **önbellekte kalır.**

----

MFTcmd
* MFTECmd.exe -f C:\$MFT --csv C:\output
MFTExplorer
* Biraz zaman alır ancak genelde sonuç verir.qdis

----

C:\Windows\Prefetch klasörü komut en son ne zaman yürütüldü. 
PECmd.exe -f WHOAMI.EXE-67383F62.pf
Last run: 2024-10-05 15:01:28