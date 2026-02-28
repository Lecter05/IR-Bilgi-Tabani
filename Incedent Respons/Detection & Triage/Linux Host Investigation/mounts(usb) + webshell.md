dmesg | grep mount > disk/USB bağlama, network mount hatalar
findmnt > sistemi şu anki mount ağacı şeklinde gösterir
df -aTh > tüm dosya sistemlerinin disk kullanımını gösterir.


## webshell

* /var/www veya /tmp
* find / -type f \( -iname \*.php -o -iname \*.php7 -o -iname \*.sh -o -iname \*.elf \)
webshell genelde burada aranır 

* find /tmp -newermt "2025-08-25" ! -newermt "2025-10-25"
belirtilen tarihler arasında **değiştirilmiş** dosyaları listeler

* find /tmp -user www-data
`www-data` (web servis) kullanıcısının `/tmp`'de değiştirdiği dosyaları listeler.
