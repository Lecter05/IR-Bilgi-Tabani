
Cron, crontab isimli yapılandırma dosyası yardımıyla zamanlanan zamanda işleri (cron işlerini) yürüten araçtır. **Crontab = Scheduled Tasks**

·         **cat /etc/crontab**   --> gereksiz

zamanlama + hangi kullanıcı ile çalışacağı da belirtilir.

·         **cat /etc/cron.d/*** --> gereksiz**

crontab dosyalarını listelemek için kullanılabilir.

·         **cat /var/spool/cron/crontabs/*** --> Tüm kullanıcıların çıktısını verir.

Her kullanıcının kendi crontab dosyası vardır, Tüm kullanıcılara ait tüm cron işlerini listelemek için bu komutu kullanılabilir.

·         **cat /var/log/syslog | grep CRON**

Syslog'dan cron çalıştırmaları listelenebilir.

·         **journalctl -u cron**

·         **journalctl -u cron --since "2021-05-07 00:00" --until "2021-05-07 23:59"**

**“ --since** ” ve “ **--until** ” parametrelerini kullanarak saldırı zaman diliminde listelenebilir.

Saldırganın eklediği/değiştirdiği cron işlerini sil veya düzelt.

Kendi crontab’ini düzenle: crontab -e

Başka bir kullanıcının crontab’ini düzenle: sudo crontab -u KULLANICI -e

Root için

sudo crontab -u root -e   # root'un cron satırlarını düzenle ve şüphelileri sil