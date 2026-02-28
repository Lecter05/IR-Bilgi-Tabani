**krbtgt** varsayılan olarak oluşturulan bir hesaptır. Tek görevi **KDC** servisi için için çalışan bir servis hesabıdır. **Kısaca KDC servisinin çalışmasını sağlayan hesaptır.**
Saldırgan bu krbtgt hesabını ele geçirip istediği neredeyse domain admin yetkisine sahip olur.

Kerberos servis hesabının NTLM özetine ihtiyacı olacaktır. Mimikatz gibi araçlar, lsass.exe dosyasından NTLM özetlerini almamıza yardımcı olabilir.
* **lsadump::lsa /inject /name:krbtgt**
![[Pasted image 20251031112207.png]]
Resimdeki işaretli kısımlar şunlardır;
* SID
- RID(kullanıcı kimliği)
- NTLM karması
Altın bileti hazırlarken tüm bunlara ihtiyacımız olacak.

**kerberos::golden /User:Administrator /domain:CYBERCONSULTING.org /sid:S-1-5-21-2612289411-4282575245-2512524665 /id:502 /krbtgt:2e3d7350dd8210ebe7f03ce2147d8786 /ptt**
![[Pasted image 20251031112346.png]]
krbtgt alanında NTLM karması, domain alanında ise domain adı sağlanır. '/ptt' anahtarı, bileti hafızamıza ekler ve saldırgan artık Active Directory'deki tüm izinlere sahip ve tıpkı bir domain admin hesabı gibi çalışan krbtgt hizmetinin ayrıcalıklarına sahip olur. Saldırganlar ayrıca bileti ileride kullanmak üzere dosyaya kaydedebilir. Artık saldırganlar ortamdaki herhangi bir bilgisayarla, hatta etki alanı denetleyicileriyle bile etkileşime girebilir ve sistem ayrıcalıklarına sahip bir kabuk elde edebilirler.
![[Pasted image 20251031112459.png]]

C$” paylaşımına bağlanarak yetkilerini doğruladığı
![[Pasted image 20251031112545.png]]




