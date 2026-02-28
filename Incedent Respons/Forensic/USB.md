
### USBSTOR
HKLM\SYSTEM\CurrentControlSet\Enum\USBSTOR
Sisteme hangi USB’ler takıldı, marka/model, bağlanma-çıkarılma zamanı.

**Gösterdiği bilgiler:**

- **FriendlyName** → USB’nin görünen adı (ör. Kingston DT 16GB)
- **ContainerID** → Cihaza özgü benzersiz ID
- __Properties → {83da_}_*
    - `0066` → _İlk bağlanma zamanı_
    - `0067` → _Çıkarılma zamanı_


### USB
HKLM\SYSTEM\CurrentControlSet\Enum\USB
Bu anahtar, USB portları aracılığıyla bağlanan tüm cihazlar hakkında bilgi içerir (klavyeler, adaptörler)

**DeviceDesc** kısmından cihazın ne olduğu tanımlanabilir. kesin tespit için;
**HardwarelD** : Data USB\VID_**1532**&PID_**008A**&REV_0200&MI_01 USB\VID_1532&PID_008A&MI_01
**Vendor ID** ile cihazlar listelenir **PID** ile cihazın ne olduğu net bulunabilir.
**https://devicehunt.com/** --> bu siteden kontrol et.


## **USB Event Logs**
Application and Services Logs” -> Microsoft -> Windows > Partition > **Diagnostic**

### Kernel-PnP
Application and Services Logs” -> Microsoft -> Windows > **Device Configuration**

400  --> Bir cihazın ilk kez hangi kullanıcı tarafından sisteme bağlandığını gösterir. (ilk algılama)
410 --> **sistemde aktif hale geldiği** zamanı gösterir. (cihaz aktif hale geldi)

### NTFS
Application and Services Logs” -> Microsoft -> Windows > **Ntfs** **142-145** event id **false** ara harici disk demek. Daha önce tespit edilen USB bağlanma zamanı aratılır ve hangi sürücü harfi atanmış tespit edilbilir.

USB’ye hangi sürücü harfini (örneğin E:, F:, G:) atadığını bulmaya yarar.



## Araçlar

### **Shellbags ile Klasör Erişim Analizi**
Shellbags ile Explorer ile en son erişilen dizinler görüntülenebilir.

**UsrClass.dat** hive ile çalışır.

Şüpheli USB’nin sürücü harfi tespit edildikten sonra o disk **elle** ziyaret edilmiş mi bunlar incelenebilir.


### **Jumplists ile Klasör Erişim Analizi**
**C:\Users\bayra\Desktop\Acquisition\C\Users\LetsDefend\AppData\Roaming\Microsoft\Windows\Recent\AutomaticDestinations** -->  klasörlerin hepsi seçilmeli.
**C:\Users\bayra\Desktop\Acquisition\C\Users\LetsDefend\AppData\Roaming\Microsoft\Windows\Recent\CustomDestinations**


AutomaticDestinations → “Ne zaman hangi dosya açıldı?”
CustomDestinations → “Kullanıcı hangi dosyaları özellikle sabitledi veya sık kullandı?”
kullanıcılara son erişilen uygulama dosyalarına ve sık kullanılan görevlere hızlı erişim sağlamayı amaçlar. 
![[Pasted image 20251117161713.png]]
**Windows Gezgini** (Windows Explorer (Windows 8.1)) üzerinden erişilen dosyaları gösterir.
### **USB Parsers Tools**

Bu araç, tüm bilgileri otomatik olarak ayrıştırır ve analiz için düzenli bir şekilde sunar. Gerekli dosya yolları  verilerek USB forensic için dosyaları çıkartabilir.