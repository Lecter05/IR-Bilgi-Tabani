 Active (running): Servis arka planda çalışıyor.
•  Active (exited): Servis başarıyla çalıştırılmış ama sürekli izlenecek bir daemon yok. Yani çalışmasını tamamlamış.
•  Active (waiting): Servis çalışıyor ama belirli bir olayı/tetiklemeyi bekliyor.
•  Inactive: Servis şu anda çalışmıyor.
•  Enabled: Servis sistem açılışında (boot sırasında) otomatik olarak başlayacak şekilde ayarlanmış.
•  Disabled: Servis sistem açılışında başlamayacak, elle başlatılmadıkça devreye girmeyecek


* systemctl list-units --type=service
cihazdaki tüm servisleri incelemeye yarar.
* service --status-all 
tüm servislerin durumunu kontrol etmeye yarar.
* service ufw staus
servis kontrol komutu

*********** *********** *********** *********** *********** ***********

·         **cat /lib/systemd/system/cron.service** --> Şüpheli Service araştırması

·         **cat /etc/systemd/system/reverse.service** --> ExecStart= <kötü amaçlı kod>

Yapılandırma dosyasında özellikle dikkat etmemiz gereken bölümler "service" bölümündedir. Bu bölümün "ExecStart" yönergesi, hizmet etkinleştirildiğinde çalıştırılacak komutları ve programları içerir. Saldırganlar, "**ExecStart" yönergesine kendi kötü amaçlı komutlarını girebilir** ve bu komutlar arka planda çalışabilir.

·         **stat /lib/systemd/system/cron.service**

Sistem yapılandırma **dosyasının ne zaman düzenlendiğini** "stat" komutuyla tespit edebiliriz. Saldırganın bir hizmeti değiştirdiğinden veya yeni bir hizmet oluşturduğundan şüpheleniyorsanız, yapılandırma dosyasıyla ilgili bilgileri inceleyebilirsiniz.

·         **journalctl -u ssh**

Hizmet kayıtlarını görüntülemek için journalctl aracını kullanabiliriz. "-u" parametresini kullanarak ve birimin adını girerek belirli bir hizmetle ilgili günlükleri görüntüleyebilirsiniz.

·         **journalctl --since "2021-11-03" --until "2021-11-04 23:59" | grep enable | grep .service**

Indicator olarak --> **"enable"**

![[Pasted image 20251106164551.png]]
