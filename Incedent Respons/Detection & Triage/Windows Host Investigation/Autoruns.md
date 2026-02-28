## Scheduled
**Scheduled Tasks:** kısmında kırmızı bir şekilde **(Not Verified)** yani sertifikası olmayan uygulamalara yoğunlaşılmalı. Geriye kalan dosyalar açılarak incelenebilir.


**Deleted Tasks**

Event Viewer > Applications and Services Logs > TaskScheduler > Operational
Loglar > Uygulama ve Hizmet Günlükleri > Windows > TaskScheduler > Çalışıyor
Bu kısımdan TaskScheduler loglarına erişilebilir.

* Olay Kimliği 4698: Zamanlanmış bir görev oluşturuldu
* Olay Kimliği 4702: Zamanlanmış bir görev güncellendi
![[Pasted image 20251102102540.png]]


## Services(Hizmetler)
Event ID 4697 (A service was installed in the system)(Sisteme bir servis kuruldu)
•	Saldırgan, sisteme kendi zararlı yazılımını çalıştıracak bir servis ekleyebilir.( Chrome Update gibi masum görünebilir.)
•	Var olan bir servisin çalıştırdığı dosya/komut değiştirilebilir. Böylece yasal görünen bir servis aslında saldırganın zararlı kodunu çalıştırmaya başlar.
•	Saldırgan sadece kendi servislerini çalıştırmaz, aynı zamanda koruma amaçlı çalışan servisleri (Windows Defender, Firewall gibi) durdurur.



## Explorer
zamandan tasarruf etmek istiyorsak, **önce “Description” (Açıklama) ve “Publisher” (Yayıncı)** bölümlerinde **boş** olan kayıtları incelemeye başlayabiliriz.

bir kayıt defteri değeri değiştirildiğinde "EventID **4657**" kaydı oluşturulur.
![[Pasted image 20251102104248.png]]
![[Pasted image 20251102104114.png]]

Programda’ gözükmediği için bazen bu klasörlerde elle aramak gerekebiliyor.
• C:\Users\[Username]\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup
• C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp


