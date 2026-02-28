IIS Web Sunucusu
Log kayıtları IIS web sunucusunda  C:\inetpub\logs\LogFiles\W3SVC1

grep -Ei '(%27|--|\bunion\b|\bselect\b|\bfrom\b|\bor\b|@|version|char|varchar|exec)' /var/log/apache2/access.log

zgrep -Ei '(%27|--|\bunion\b|\bselect\b|\bfrom\b|\bor\b|@|version|char|varchar|exec)' /var/log/apache2/access.log*

komutların arasındaki sorun Access.log.1


