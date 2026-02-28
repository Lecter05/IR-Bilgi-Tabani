**Active Directory (AD)**

büyük ağlarda kullanıcı, bilgisayar ve kaynak yönetimi için geliştirdiği merkezi bir dizin servisidir.

AD’nin kimlik doğrulama (authentication) temelinde **Kerberos protokolü** vardır. **bilet (ticket)** mantığıyla çalışır ve UDP 88 portunu kullanır.

**Temel Terimler**

- **KDC (Key Distribution Center):** Kerberos’un merkezidir. (bilet dağıtım merkezi)
- İki alt bileşeni vardır:
	 -**AS (Authentication Service):** Kullanıcıya ilk bilet (TGT) verir.
	 -**TGS (Ticket Granting Service):** Kullanıcıya, erişmek istediği servis için hizmet bileti (Service Ticket) verir.

- **TGT (Ticket Granting Ticket):** Kullanıcıya KDC tarafından verilen kimlik bileti. Bu biletle diğer hizmet biletleri istenir.
- **SPN (Service Principal Name):** Bir servis hesabına atanan benzersiz isimdir. Servisleri kimlik doğrulamada tanımlamak için kullanılır.

**Örnek: Dosya Paylaşımına Erişim Akışı**

1. Kullanıcı dosya paylaşımına erişmek ister → KDC’den kimlik doğrulama ister.
2. KDC, kullanıcıyı tanıyorsa ona bir **TGT** ve **session key** gönderir.
3. Kullanıcı, dosya paylaşımı hizmetine erişmek için **TGS**’ye TGT’yi gönderir.
4. KDC (TGS kısmı) hizmet bileti (**Service Ticket**) üretir ve kullanıcıya yollar.
5. Kullanıcı bu bileti dosya paylaşım sunucusuna gönderir.
6. Sunucu bileti doğrular ve kullanıcıya erişim izni verir.