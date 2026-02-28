**/var/log==/auth.log== (veya /var/log/==secure==)**  
Kullanıcı oturumları, sudo kullanımı, SSH giriş denemeleri

- failed|failure|invalid|authentication error → Başarısız giriş denemeleri
- accepted|success|session opened → Başarılı girişler

grep -a -E 'failed|failure|invalid|authentication error' /var/log/auth.log
grep -a -E 'accepted|success|session opened' /var/log/auth.log 

- **sudo** → Yetkili komut kullanımı
- **root** → Root kullanıcı aktiviteleri
- **sshd** → SSH daemon olayları

---

**/var/log/==syslog== veya /var/log/==messages==**  
Genel sistem olayları, servis başlatma, kapanma, hata uyarıları

- **error|fail|denied** → Hatalar veya engellemeler
- **systemd|service** → Servis başlatma/kapanma kayıtları
- **kernel**: → Donanım veya sürücü olayları

---

**/var/log/==dmesg==**  
Kernel mesajları, donanım sürücüleri

- usb|eth|sda|disk → Donanım tanıma / bağlantı sorunları
- fail|error|timeout → Donanım arızası belirtileri

---

**/var/log/audit/==audit.log==**  
Dosya erişimleri, sistem çağrıları, yetki denetimleri

- USER_AUTH|USER_CMD|USER_LOGIN → Kullanıcı aktiviteleri
- AVC denied → SELinux engellemeleri
- exe= → Hangi komut çalıştırılmış

---

**/var/log/==ufw.log== veya /var/log/==iptables.log==**  
Firewall trafiği

- DPT=22 → SSH bağlantı girişimleri
- DENIED|DROP → Engellenen trafiği tespit et
- SRC=, DST= → Kaynak ve hedef IP adresleri

---

**/var/log/nginx/==access.log== veya /var/log/apache2/==access.log==**  
Web istekleri (HTTP logları)

- status 404 → Kayıp sayfalar
- status 403 → Yetkisiz erişim girişimleri
- POST → Veri gönderimi (şüpheli olabilir)
- User-Agent → Script veya bot tabanlı istekler

---

**/var/log/nginx/==error.log== veya /var/log/apache2/==error.log==**  
Web sunucusu hataları

- segfault|permission denied|timeout → Erişim, hata veya çökme kayıtları

---

**/var/log/==cron.log==**  
Zamanlanmış görevler

- bash|curl|wget → Beklenmeyen komut çalıştırmaları
- CRON altında yeni kullanıcı veya şüpheli görevler

---

**/var/log/==wtmp==, /var/log/==btmp==, /var/log/==lastlog==**  
Kullanıcı giriş/çıkış geçmişi

- last → Giriş/çıkış listesi
- lastb → Başarısız giriş denemeleri
- lastlog → Her kullanıcının son girişi

