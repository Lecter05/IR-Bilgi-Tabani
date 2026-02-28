**Process** Hacker **admin** olarak açılmazsa komutlar ve dosyalar görükmez.

Spesifik aramalar yapılabilir, gerek Parent PID gerekse bir proses adı örnek olarak aranan bir .bat 
dosyası veya sadece bir powershell işlemi aranabilir. Dikkat edilmesi gereken husus, o prosesi hangi Parent PID başlatmış buna bakılmalı.

Eğer aklında bir dosya varsa bişeyleri bilerek araştırıyorsan arama yapılabilir. Aksi durumda bakarak bir anomali araman gerekiyor buda Parent PID önemli kılıyor zira işlemi açıp kendisini kapatıp silmiş olabilir.


==**TOKEN**==

**Neye bakılır**

- Process token (kimin yetkisiyle çalışıyor): User, LocalSystem, SeDebugPrivilege var mı?

==**Şüpheli işaretler**==

- Normal uygulama SYSTEM yetkisiyle çalışıyorsa (ör. kullanıcı uygulaması ama SYSTEM).
- SeDebugPrivilege veya benzeri yüksek ayrıcalıklar.

==**MEMORY**==

**Neye bakılır**

- RWX bölgeleri genelde shellcode/eksploit, mapped belleklerde farklı dosyalar inject edilmiş olabilir.

**MODULES – Kontrol Noktaları**

- ==**DLL Yolu**==

- Şüpheli: C:\Users\...\AppData\Roaming\, Temp gibi beklenmedik dizinler.
- Normal: Sistem dizinleri (C:\Windows\System32\ vb.).

- ==**Dijital İmza**==

- **Verified** → Genelde güvenli.
- **Unverified / Unknown Publisher / İmzasız** → Şüpheli, incelenmeli.