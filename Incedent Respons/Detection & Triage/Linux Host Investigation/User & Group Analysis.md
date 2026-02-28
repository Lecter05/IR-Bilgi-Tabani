/etc/passwd > Her kullanıcı erişebilir.
/etc/shadow > Kök kullanıcı ve shadow  gurubundakiler erişebilir
/etc/group > Kök’a aittir herkes okuyabilir
/etc/sudoers >    

![[Pasted image 20251104211739.png]]
<user list> <host list> = (<operator list>) <tag list> <command list>

alice ALL=(ALL) NOPASSWD: /usr/bin/**systemctl**
alice her hostta systemctl komutunu parola sormadan çalıştırabilir (NOPASSWD sayesinde)

bob ALL=(root) /bin/kill
bob, root adına sadece /bin/kill çalıştırabilir (parola ister).


•	/var/run/utmp : Sistemin o anki durumunun, sistem önyükleme süresinin (uptime tarafından kullanılan süre), hangi terminallerde kullanıcı oturumlarının açıldığının, oturumların kapatıldığının, sistem olaylarının vb. tam bir muhasebesini tutar.
•	/var/log/wtmp : tarihsel bir utmp gibi davranır
•	/var/log/btmp : başarısız oturum açma girişimlerini kaydeder


