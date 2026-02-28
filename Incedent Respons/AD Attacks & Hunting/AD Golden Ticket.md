**Detection**
Tespiti çok zordur. Sysmon loglarında "mimikatz" kurulumu aranmalı

**4769**
* Subject Account Domain kısımı boşsa ve istek krbtgt'ye yapılıyorsa
* Logon Type: 3 zira saldırı ağ içerisinden yapılır.
* bilet ömrü klist ile kontrol edilmeli

**4624**
güvenlik kimliği ve hesap adı birbiriyle ilişkili olmalıdır. yani kullanıcı yöneticisinin güvenlik kimliği yönetici olmalıdır

------

Mimikatz ile sahte TGT oluşturur, yani elinde zaten bir TGT vardır. NTLM'i(4776) by-pass eder.
TGT kullanarak servis bileti ister --> 4769 (Servis Bileti İsteği) biletin kullanıldığında oluşur.

bu aşamada dikkat edilecek şey bu kullanıcı TGT isteği(4768) yapmış mu buna bakılır.
* 0x17
* bilet süresi
* 4769 VAR + 4768 YOK ise = GOLDEN TICKET ŞÜPHESİ.
* Logon Type 3
* `Account Name` veya `Logon ID`

----
* Kısa özet
4768 --> TGT isteği
4769 --> TGT'si var olup TGS isteği (servis isteği)
golden ticket amacı TGT ele geçirmektir. Normalde TGS isteği yapan birisi TGT isteği de yapmış olması lazım yapmadıysa TGT ele geçirmiş demektir.
Sonrasında Şüpheli TGS isteği yapan kullanıcı 4624 ile Giriş yaptı mı incelenebilir. 




https://www.thehacker.recipes/ad/movement/ bu siteyi incele

