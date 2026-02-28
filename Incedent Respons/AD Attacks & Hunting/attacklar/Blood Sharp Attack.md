LDAP 
dizindeki (Active Directory) kullanıcı, bilgisayar, grup ve izin bilgilerini sorgulayan protokol.

saldırgan ne yapar;
saldırı hedef makinede bir kullanıcıdan SharpHound çalıştırılır. sonrasında oluşturulan .zip dosyasını saldırgan kendisine atıp orada BloodHound ile görüntüleyebilir.
LDAP sayesinde saldırgan;
•	Kullanıcı adları, hangi makinelerde oturum açıldığı, grup üyelikleri, ACLler, hizmet hesapları gibi verileri toplar.
•	Bu verilerle ağın haritasını çıkarır.
•	Haritadan en kısa ayrıcalık yükseltme yollarını bulur

**SharpHound**: hedef ortamda çalıştırılan toplayıcı. LDAP, SMB, RPC vs. kullanıp ham verileri toplar.
**BloodHound**: toplanan veriyi görselleştirir istismar yöntemleri önerir. kısaca Otomatik olarak zayıf noktaları ve yükselme yollarını bulur.
![[Pasted image 20251031110203.png]]