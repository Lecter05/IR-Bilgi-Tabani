**NTDS\Ntds.dit**

Ntds.dit (NT Directory Services DataBase), Active Directory (AD) içindeki tüm bilgileri tutan veritabanı dosyasıdır. AD domainlerinin konfigürasyonu, kullanıcılar, gruplar, güvenlik politikaları, parola hash’leri ve diğer nesneler burada saklanır. Her etki alanı denetleyicisinde (DC) bulunur.

Windows’un yerleşik aracı **ntdsutil** bu saldırıda sık kullanılır. AD veritabanını yedeklemek için kullanılır ve komut satırından çalıştırılabilir.

**ntdsux"til "ac i ntds" "ifm" "create full C:\Users\Administrator\Desktop\NTDS_BACKUP" q q**