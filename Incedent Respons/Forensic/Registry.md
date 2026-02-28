
## **Registry Hive Dosyaları**

C:\Windows\System32\config
•	SYSTEM: Sürücü, hizmet, sistem bileşeni ayarları
•	SOFTWARE: Kurulu yazılımlar ve yapılandırmaları
•	SAM: Yerel kullanıcı hesapları ve parola hash’leri
•	SECURITY: Güvenlik politikaları, erişim izinleri
•	DEFAULT: Yeni kullanıcı hesabı oluşturulurken kullanılan varsayılan şablon

## **Kullanıcıya Özel Hive Dosyaları**

**NTUSER.DAT**
C:\Users\bayra\NTUSER.DAT
Kullanıcının masaüstü, başlat menüsü, uygulama ayarları gibi kişisel bilgilerini tutar.

**UsrClass.dat**
C:\Users\bayra\AppData\Local\Microsoft\Windows\UsrClass.dat
Kullanıcıya özel uygulama ve arayüz ayarlarını saklar.

**Amcache Hive**
C:\Windows\AppCompat\Programs\Amcache.hve
Windows, sistem performansını artırmak ve kurulu uygulamaları izlemek için bu hive dosyasını kullanır. Yeni kurulan veya güncellenen yazılımlar hakkındaki bilgiler burada saklanır — bu da adli analizde zaman çizelgesi oluşturmak için değerlidir.


## 1) **SYSTEM Hive – Control Sets**
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet   (bellekte olur)

SYSTEM\ControlSet001
SYSTEM\ControlSet002
* Bozuk sürücü, malware tarafından yapılan servis değişikliği, yanlış driver yüklemesi gibi olaylarda sistem davranışını anlamak için kullanılır.

## 2) **SOFTWARE Hive – Sistem & OS Bilgileri**
SOFTWARE\Microsoft\Windows NT\CurrentVersion

 **İçerdiği kritik bilgiler:**
- Windows sürümü
- Build numarası
- Edition (Home / Pro / Enterprise…)
- Mimari (x64/x86)
- Kurulum tarihi
- RegisteredOwner & Organization

----

## 3) **Network Artifacts (NetworkList Key)**
SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList
![[Pasted image 20251116175100.png]]

### `Paylaşılan ağ klasörleri`
SYSTEM\CurrentControlSet\Services\LanmanServer\Shares
•	Burada sistemdeki açık ağ paylaşımları listelenir.

### `TCP/IP yapılandırması`
SYSTEM\CurrentControlSet\Services\Tcpip\Parameters
SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces
•	Bu anahtarlar ağ arayüzleri ve TCP/IP konfigürasyonunu içerir (IP adresleri, DNS, ağ maskesi vb.).
![[Pasted image 20251116194256.png]]

## Araçlar

### Registry Explorer
•	Load hive --> dışarı aktarılan dosylar izlenebilir.
•	Live system --> anlık olarak dosylar izlenebilir
SAM\Domains\Account\Users altında silinen kullanıcılar ve bilgileri görüntülebilir.
![[Pasted image 20251116212047.png]]


### Shellbags
Windows Gezgini ile hangi klasörleri açtığını ve nasıl görüntülediğini kaydeden küçük izlerdir. --> NTUSER.DAT ve UsrClass.dat 
•	Hangi klasöre baktın.
•	Klasörün yolu.
•	Son bakma zamanı.
•	Bazı durumda ZIP içindeki klasör isimleri.
•	Ağ paylaşımları ve takılan USB içindeki gezilen klasörler de çıkabilir.
•	Bir dosya silinse bile “o klasöre bakıldı” kanıtı kalır.
![[Pasted image 20251116212349.png]]

### Shimcache --> Hiç bir işe yaramaz yüz üstü bıraktı

**`AppCompatCacheParser.exe`** 
Silinmiş dosyaların varlığını kanıtlayabilir
![[Pasted image 20251116212456.png]]

AppCompatCacheParser.exe --csv "C:\Desktop" --csvf dede.csv --> -**f kullanılmadığı için direkt sistemden alır**

AppCompatCacheParser.exe -f "C:\Users\bayra\Desktop\C___NONAME [NTFS]\[root]\Windows\System32\config\SYSTEM" --csv "C:\Desktop" --csvf denem.csv --> **direkt olarak SYSTEM yolu verilmek istenirse bu şekilde**

Elde edilen .csv dosyası **`timelineExplorer.exe` ile açılabilir.**
![[Pasted image 20251116212555.png]] **-f :** SYSTEM kovanı için yol.

 **--csv :** Çıktı dosyasının kaydedileceği tam yolu tırnak işaretleri ile belirtmeliyiz.

**--csvf :** Çıktı dosyasına isim verin.


### Amcache --> silinen dosyaları bulabilirsin
**`C:\Windows\AppCompat\Programlar\Amcache.hve`**
**registryExplorer.exe veya AmcacheParser görüntülenebilir.**

sistemde çalışan programları ve bunların tam olarak ne zaman çalıştırıldığını belirlemek, bir yazılımın sisteme ne zaman yüklendiğini ve kurulum dosyalarının konumunu belirlemek.
•	Uygulama yolu
•	dosya meta verileri (açıklama, yayıncı adı), 
•	zaman damgaları (Oluşturma, değiştirme ve silme) 
•	dosyanın SHA-1 karmaları gibi bilgileri tutan anahtar-değer çiftlerini içerir.
•	“InventoryApplicationFile” anahtarı, dosya silinmiş olsa bile sistemde çalıştırılan yürütülebilir dosyalar hakkında ayrıntılı bilgileri saklar.
![[Pasted image 20251116212952.png]]


Amcache ve Shimcache Arasındaki Fark 
Amcache, shimcache'in aksine, yürütmenin daha güvenilir bir kanıtı olarak kabul edilebilir. Amcache, ilk yürütme zaman damgası, silme zaman damgası (bir dosya silindiyse), yürütülebilir dosyaların karma değerleri vb. gibi ek verileri depolar. Ayrıca, herhangi bir yayımcı adı olmayan şüpheli ve güvenilmeyen dosyaları bulmamıza yardımcı olabilecek uygulama yayımcı adını da depolar. Bir yürütülebilir dosya oluştururken yayımcı adı eklemek zor olmasa da, metasploit ve empire gibi çoğu kötü amaçlı yazılım oluşturucu, aşamalandırıcılar oluştururken herhangi bir meta veriye sahip değildir.
C:\Windows\AppCompat\Programlar\recentfilecache.bcf  Windows 7 ve eski sürümler için konum.

Cmd yönetici olarak açıp komut çalıştırılabilir.
AmcacheParser.exe -f "C:\Windows\AppCompat\Programs\Amcache.hve" --csv  "C:\Users\bayra\Desktop" --csvf dede.csv
•	Sonrasında TimelineExplorer.exe ile csv dosyası görüntülenebilir.
•	-f <.hve uzantısı> 
•	--csv <kaydedileceği yer>
•	--csvf <kaydedileceği isim>
BUNA BAKILMASI KIYMETLİDİR --> UnassociatedFileEntries.csv
İKİNCİ DURAK --> DriveBinaries.csv
### **Recent Files**

Windows'ta son kullandığımız uygulamalara erişmemizi sağlayan bir özelliktir.

**C:\Users\bayra\AppData\Roaming\Microsoft\Windows\Recent**
**NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs**
![[Pasted image 20251116213318.png]]
Herhangi bir kimlik avı varım buradan kontrol edilibilri. .txt .docx .xml gibi dosyalar en son nezaman kullanıldı. Görüntülebilir.


### **Dialogue Boxes MRU**
Windows’un son açılan veya kaydedilen dosyaları hatırladığı bir adli veri kaynağı. Dosya yükleme (upload), belge açma veya program kurma aktivitelerini doğrulamak için kullanılır.
![[Pasted image 20251116213344.png]]

NTUSER.DAT dosyasında bulunur.
NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\
OpenSavePidlMRU → Dosya seçme veya kaydetme penceresinde açılan ya da yüklenen dosyaların yollarını kaydeder.
LastVisitedPidlMRU → Son ziyaret edilen klasörleri tutar.


FTK Imager.exe → My Computer\Desktop\LALA klasörünü açmış.
chrome.exe → Downloads klasörünü açmış.
DB Browser for SQLite.exe → Shared Documents Folder\User Data\Default\Network içinde işlem
![[Pasted image 20251116213437.png]]

**NTUSER.DAT** içinden **UserAssist** kısmında bir uygulama ne kadar süre açık kalmış kontrol edilebilir.
**Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\**



-----
Ekstra Hazır bilgiler

* Bilgisayarın adı(name) --> ComputerName (SYSTEM)
* En Son kapanma(shutdown) --> ShutdownTime (SYSTEM)
* Makinenin Kullandığı time zone(bölge) --> TimeZoneInformation (SYSTEM)
* default gateway(DG) --> defaultgateway (SYSTEM)
* DefaultGatewayMac --> DefaultGatewayMac (SOFTWARE)
* Kullanıcı en son ne zaman login olmuş(last login) --> SAM\Domains\Account\Users (SAM)
* Kullanıcı kaç defa girmiş(logins) --> SAM\Domains\Account\Users (SAM)
* İşletim sistemini ne olduğunu öğrenme(OS) --> Microsoft\Windows NT\CurrentVersion (SOFTWAR)
* Sürüm Tespiti (ProductName)--> Microsoft\Windows NT\CurrentVersion > CurrentBuildNumber(sw)
* En son yüklenen uygulama --> Microsoft\Windows\CurrentVersion\Uninstall (SOFTWARE)
