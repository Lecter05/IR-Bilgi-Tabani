"error.log" dosyası, sunucunun istekleri işlerken karşılaştığı hataları içerir.
Aşağıdaki ekran görüntüsü, istemcinin "/test" dizinine gitmeye çalışmasının başarısız olduğunu göstermektedir.

![[Pasted image 20251102111839.png]]
 
SQL Injection saldırısı Kayıtları incelemesi 
•	var/log/apache2
•	cat access.log
•	cat access.log | grep -E “%27|--|union|select|from|or|@|version|char|varchar|exec
•	cat access.log | grep 200  başarılı döndürülen sonuçları listelemek için
•	cat access.log | grep 192.168.2.232 | grep admin/index.php  panel erişim kontrolü
