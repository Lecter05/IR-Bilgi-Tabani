**Web Shell Keşfi**

* ***grep -Rn "system *(" /var/www**
var/www dizini altında sistem fonksiyonunu çağıran tüm dosyalar taranır.

-  **grep -RPn "(passthru|shell_exec|system|phpinfo|base64_decode|chmod|mkdir|fopen|fclose|readfile|php_uname|eval) *\(" /var/www**

saldırılarda farklı fonksiyonlar kullanılabilir bu yüzden bu komut daha garantidir