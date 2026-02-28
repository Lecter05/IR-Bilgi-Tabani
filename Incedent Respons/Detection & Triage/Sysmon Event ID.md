### 🔑 Kimlik ve Proses İlişkili Eventler

- **Event ID 1 – ProcessCreate**  
    Yeni bir proses oluşturuldu. Komut satırı, parent proses, kullanıcı gibi bilgiler içerir. Saldırganın çalıştırdığı komutları ve proses zincirini görmek için kritik.
    
- **Event ID 5 – ProcessTerminate**  
    Bir proses sonlandırıldı. Zararlı proseslerin izini sürmede faydalı.
    
- **Event ID 7 – ImageLoad**  
    Bir proses içine DLL veya başka bir binary yüklendi. DLL injection tespitinde kullanılır.
    
- **Event ID 10 – ProcessAccess**  
    Bir prosesin başka bir prosese erişmesi (ör. LSASS). Credential dumping tespitinde kritik.
    
- **Event ID 8 – CreateRemoteThread**  
    Bir proseste başka bir proseste thread oluşturuldu. Process injection belirtisi.
    
- **Event ID 9 – RawAccessRead**  
    Ham disk veya cihaz seviyesinde okuma yapıldı. Adli analiz / disk kopyalama tespitinde önemli.
    

---

### 📡 Ağ İlişkili Eventler

- **Event ID 3 – NetworkConnect**  
    Bir proses tarafından açılan outbound/inbound ağ bağlantısı kaydedildi. C2 beaconing ve şüpheli bağlantılar için temel sinyal.
    
- **Event ID 22 – DNS Query**  
    DNS çözümleme isteği kaydedildi. Şüpheli dış DNS talepleri için kullanılır.
    

---

### 💾 Dosya ve Driver İlişkili Eventler

- **Event ID 11 – FileCreate**  
    Yeni bir dosya oluşturuldu. Dropper/payload bırakma tespitinde faydalı.
    
- **Event ID 2 – FileCreateTime**  
    Dosyanın oluşturulma/zaman bilgisinde değişiklik kaydedildi. Zaman damgası manipülasyonlarını tespit etmek için önemli.
    
- **Event ID 15 – FileCreateStreamHash**  
    Alternatif veri akışı (ADS) veya dosya stream’i oluşturuldu. Gizli veri saklama göstergesi.
    
- **Event ID 6 – DriverLoad**  
    Kernel sürücüsü yüklendi. Rootkit veya kötü amaçlı driver tespitinde kritik.
    
- **Event ID 23 – File Delete (archived)**  
    Dosya silme olayları (bazı durumlarda arşivlenmiş olarak). İz silme girişimlerini takip etmek için faydalı.
    

---

### 🧭 Kayıt Defteri (Registry) İlişkili Eventler

- **Event ID 12 – Registry Object Created/Deleted**  
    Kayıt defterine anahtar eklendi veya silindi. Persistence göstergesi.
    
- **Event ID 13 – Registry Value Set**  
    Kayıt defteri değeri değiştirildi/ayrıldı. Başlangıç/kalıcılık ayarları için önemli.
    
- **Event ID 14 – Registry Key Renamed**  
    Kayıt defteri anahtarı yeniden adlandırıldı. İzleri gizleme veya konfigürasyon değişikliklerinde takip edin.
    

---

### 🔌 IPC / Pipe ve Diğerleri

- **Event ID 17 – Pipe Created**  
    Yeni bir named pipe oluşturuldu. Yerel IPC başlatma göstergesi.
    
- **Event ID 18 – Pipe Connected**  
    Named pipe üzerinden bağlantı kuruldu. Prosesler arası iletişim veya lateral hareket izinde önemli.
    
- **Event ID 21 – WMI Event Filter**  
    WMI tabanlı filtre/abone oluşturma veya tetikleme. WMI ile kalıcılık/saldırı amaçlı kullanımında tetiklenir.
    

---

### ⚙️ Sysmon / Konfigürasyon & Servis

- **Event ID 4 – (n/a)**  
    Sysmon servis durumu değişikliği (filtrelenemez). Sistem seviyesinde kontrol amaçlı.
    
- **Event ID 16 – (n/a)**  
    Sysmon yapılandırması değiştirildi (filtrelenemez). İzleme kurallarında değişiklik—dikkat.







## Windows Sysmon kurulum sorunu

https://github.com/cisagov/LME/wiki/install-sysmon
bu dizine gidip
C:\Program Files\Splunk\etc\system\local 

inputs.conf adında bir dosya oluşturup. içerisine bunu ekle. ardından Server controls kısmından restart et.
[WinEventLog://Microsoft-Windows-Sysmon/Operational]
disabled = 0
renderXml = 1
index = main


Event Log Collections kısmında sysmon eklenmiş olarak gözükecektir.




------------------------------------------------------------
## Linux Sysmon kurulumu(ubuntu için farklı komutlar)
https://github.com/microsoft/SysmonForLinux/blob/main/INSTALL.md --> kurulum referansı
1. 
wget -q https://packages.microsoft.com/config/debian/12/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
sudo apt update

2. 
sudo apt install sysmonforlinux -y



3. 
wget https://raw.githubusercontent.com/SwiftOnSecurity/sysmon-config/master/sysmonconfig-export.xml


4. 
sudo sysmon -i sysmonconfig-export.xml


--------------

## Sysmon Loglarını gönderme

Universal Forwarder veya rsyslog ile sysmon loglarını splunk'a iletilmesi lazım.  alttaki adımlar rsyslog ile nasıl logları iletebileceğine dair ayrıntılı adımlardır. 


rsyslog ile sysmon loglarını göndermek

1. 
sudo apt update && sudo apt install rsyslog -y


2. 
sudo mkdir -p /var/spool/rsyslog
sudo chown root:adm /var/spool/rsyslog


3. 
sudo nano /etc/rsyslog.conf


4. 
* Modülleri yükle ve Hız Limitini (Rate-Limiting) Kapat ratelimit.interval="0" parametresi, Sysmon'un yoğun trafiğinde, Rsyslog'un paketleri çöpe atmasını engeller.

module(load="imuxsock")
module(load="imjournal" StateFile="imjournal.state" ratelimit.interval="0")

* Temiz Gönderim Şablonu (Clean Template): Logun başına Rsyslog'un eklediği tarih/host bilgilerini atar, sadece Sysmon'un saf XML mesajını gönderir.
$template CleanSysmon,"%msg%\n"

* Hedefe Yönlendirme: Tüm logları UDP portu üzerinden Splunk IP'sine, tanımladığımız şablonla gönderir.
*.* @192.168.32.128:514;CleanSysmon


5. 
sudo systemctl restart rsyslog
sudo systemctl status rsyslog



-----------

## Linux'a **Universal Forwarder** kurulum

1.
sudo dpkg -i splunkforwarder-10.2.0-d749cb17ea65-linux-amd64.deb
2.
sudo /opt/splunkforwarder/bin/splunk start --accept-license
3.
sudo /opt/splunkforwarder/bin/splunk add forward-server 192.168.32.128:9997
deneme
Deneme504
4.
sudo /opt/splunkforwarder/bin/splunk add monitor /var/log/syslog -sourcetype sysmon:linux
5.
sudo usermod -aG adm splunkfwd
sudo /opt/splunkforwarder/bin/splunk restart
6.
sudo /opt/splunkforwarder/bin/splunk status
kontrol


sudo nano /etc/rsyslog.conf içerisindeki ip adresini silmen lazım. 
sudo systemctl restart rsyslog



