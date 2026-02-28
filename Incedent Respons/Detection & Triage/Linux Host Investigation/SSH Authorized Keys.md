
"~/.ssh/authorized_keys" dosyasına anahtarı yazar. Böylece kullanıcı, kullanıcı adı-şifre çiftini kullanmadan sunucuya erişebilir.


•	find / -name 'authorized_keys'
bu komut ile tüm authorized keysler tespit edilebilir.

Örnek vaka:
root@ip-172-31-0-12:/var/spool/cron/crontabs# find / -name 'authorized_keys'
/home/helpdesk/.ssh/authorized_keys
/home/ubuntu/.ssh/authorized_keys
/root/.ssh/authorized_keys
bu kısımda ubuntu ve helpdesk kullanıcısı için SSH Auth Key eklenmiş.




•	.bashrc
•	.bash_profile 

.bashrc ve .bash_profile dosyaları bir kullanıcı kabuğu açıldığında otomatik çalıştırılan betiklerdir.Saldırganlar buraya ters-shell (reverse shell) veya arka kapı başlatan komutlar ekleyerek kalıcılık sağlarlar. Gizli giriş yolu bırakılmamış olduğundan emin olunmalı.
