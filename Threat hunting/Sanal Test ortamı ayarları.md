------
## Windows Update

services.msc > Windows Update > Disabled

gpedit.msc > Computer Configuration > Administrative Templates > Windows Components > Windows Update > Manage end-user experience > Configure Automatic Updates > Disable

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WaaSMedicSvc > **Start** > çift tıkla ve veriyi **4** yap

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\wuauserv > **Start** > çift tıkla ve veriyi **4** yap

------
## 4688
secpol.msc > Advanced Audit Policy Configuration > System Audit Policies - Local Group Policy Object > Detailed Tracking > Audit Process Creation) > Success ve Failure işaretle

------
## Commandline
cmd > reg add "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System\Audit" /v ProcessCreationIncludeCmdLine_Enabled /t REG_DWORD /d 1 /f 

------
## Defender
gpedit.msc > Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus > Real-time Protection --> Turn off real-time protection (Enabled-DİKKAT!)

Microsoft Defender Antivirus --> Turn off Microsoft Defender Antivirus (Enabled-DİKKAT)

* olmazsa bunları dene

msconfig > Boot > Safe boot > Network

Autoruns64.exe > Hide Windows Entries  bu tiki kaldır > Services > WinDefend başındaki tiki kaldır. 

msconfig > Boot > Safe boot tiki kaldır.

------
## Logon/Logoff

**Advanced Audit Policy Configuration** > **System Audit Policies - Local Group Policy Object**
**Failure**/Success > ikisini işaretle

------
## Windows Firewall
cmd yönetici > netsh advfirewall set allprofiles state off

------

Wiew > Dosya uzantıları göster
Wiew > Gizli dosyaları göster

------

gpupdate /force

------

Snapshoot al

------

GEREKLİ Uygulamalar
* winrar
* 7z
* npp
* sumatraPDF
* git
* autrouns
* everythink






