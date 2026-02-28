KDC’den bir Kerberos kimlik doğrulama bileti TGT istendiğinde kaydedilir. **4768** Ancak bu günlük kimlik doğrulamalar içinde istenir. Buda saldırı avını zorlaştırır.

**Tıcket Encryption Type: 0x12**(AES) ise sorun yok demektir.
**Pre-Authentication Type**: **0**'dan farklı ise
**Tıcket Encryption Type: 0x17**(RC4) --> saldırı
**Pre-Authentication Type: 0**

**Kontrol** Security
Event id 4768
Tıcket Encryption Type: 0x17
Pre-Authentication Type: 0


# AD saldırılarında Eventler
-----

**==4776==** **NTLM Kimlik Bilgisi Doğrulama (Credential Validation).** DC, NTLM protokolü üzerinden bir hesabın kimliğini doğruladığında.

**NTLM Saldırıları ve Pivot Noktası.** Saldırganın ele geçirdiği hash'i/parolayı **ilk test ettiği anı** gösterir.

----

**==4768==** **Kerberos TGT Talebi (TGT Request).** Bir kullanıcı, ilk Kerberos bileti olan TGT'yi DC'den talep ettiğinde.

**AS-REPRoasting.** Bazı kullanıcı hesaplarının parolasız TGT aldığı durumları yakalamak için kritik.

----

**==4769==** **Kerberos Servis Bileti Talebi (Service Ticket Request).** Kullanıcı, bir sunucuya/hizmete erişim bileti (TGS) istediğinde.

**Golden/Silver Ticket İmzası ve Yanal Hareket.** Saldırganın sahte biletle ağda ilerlemeye çalıştığı anı gösterir. `Ticket Encryption Type` alanına bakılır.

-----

**==4740==** **Hesap Kilitleme (Account Locked Out).** Bir hesap, başarısız denemeler sonucu kilitlendiğinde.

**Brute Force Saldırısının Etkisi.** Saldırganın başarısız denemeler sonucu masum kullanıcıları kilitlediğini gösterir.

----

**==4672==** **Süper Ayrıcalıklı Oturum Açma (Admin Logon).** Yönetici ayrıcalığı gerektiren bir oturum açıldığında.

**Ayrıcalık Yükseltme.** Bir hesabın yönetici yetkisiyle oturum açtığını gösterir; yönetici hesaplarının ne zaman kullanıldığını takip etmek için kritiktir.

-----

**==4662==** **AD Nesnesi Erişimi.** Bir AD nesnesinin (kullanıcı, grup, OU) izinleri değiştirildiğinde.

**Kalıcılık (Persistence) ve Geri Kapı (Backdoor).** Saldırganın kalıcılık sağlamak için izinleri değiştirmesi.

-----

**==5136==** **Dizin Hizmeti Nesnesi Değişikliği (Directory Service Object Modified).** AD içinde bir nesnenin (kullanıcı parolası, grup üyeliği) değiştirilmesi.

**Yetki Değişikliği ve Kalıcılık.** Saldırganın kendi hesabını bir yönetici grubuna eklemesi veya başka bir hesabın parolasını sıfırlaması.

------
