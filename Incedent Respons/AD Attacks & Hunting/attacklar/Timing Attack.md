**Ağda bir SPN bulunur. (**Bir servis hesabına atanan benzersiz isim**) o hizmet için TGS bileti ister.**

Dahili ağa sızan saldırgan **Powerview.ps1** adında betik çalıştırır. Bu betik sayesinde betikteki bir **cmdlet** modülünü kullandı ve “**Get-NetUser**” komutunu çalıştırdı. Sistem yöneticilerinin parolalarını açıklama alanına not ettiği için “**Description**” kısmında parola görüntüleniyor.
![[Pasted image 20251031110000.png]]
Eğer burada parola yoksa Rubeus aracı ile kerberoastable hizmet hesaplarının hash’lerini döker. Sonra saldırgan bu hash’i kopyalayıp kendi makinesinde kırabilir. **.\Rubeus.exe kerberoast**
