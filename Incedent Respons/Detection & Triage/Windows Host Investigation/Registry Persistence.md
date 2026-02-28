## Run & RunOnce Keys
Bu anahtarların içine eklenen değerler, kullanıcı oturum açtığında veya sistem başladığında otomatik olarak program çalıştırır.

HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunOnce
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnce

`RunOnce` anahtarları yalnızca **bir kez** çalışacak komutları içerir.


## Explorer Shell Folders
Bu anahtarlar, Windows’un “Başlangıç” (Startup) klasörüne benzer şekilde oturum açıldığında otomatik başlayan öğeleri yönetir.

HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\UserShellFolders
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\ShellFolders
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ShellFolders
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\UserShellFolders
Kullanıcı bazlı kalıcılık noktaları içerir (`AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup` gibi).


## RunServices & RunServicesOnce
Kötü amaçlı yazılım bunları değiştirerek arka planda servis olarak çalışabilir.

HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunServices
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunServices
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunServicesOnce
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunServicesOnce


## Policies\Explorer\Run (Group Policy)
Kurumsal ortamlarda yöneticiler **Group Policy** ile hangi programların otomatik başlayacağını belirler.  Bu ayarlar da registry’de aşağıdaki anahtarlarda bulunur.

HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run






