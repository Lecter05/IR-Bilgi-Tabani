·         **BelkaSoft Live RAM Capturer**

Direkt Capture memory imaj alınır.

-----

·         **FTK Imager**

Capture Memory > Destination Path (bellek görüntüsünü depolamak istediğin yol)

**Physical Drive**: Diski komple alır, silinmiş veriler de kurtarılabilir. 500 GB’lık diskin tamamını (300 GB kullanılan + 200 GB boş) alırsın. Silinmiş veriler geri getirilebilir.

**Image File**: Önceden alınmış imaj dosyasını açar.

**Logical Drive (C:):** Sadece kullanılan dosyaları alı. sadece 300 GB’lık ayrılmış ve kullanılan kısmı alırsın. Unallocated (200 GB boş alan) yoktur.

**Folder Contents:** sadece seçtiğin klasör.

File > Image Mounting denilerek imaj incelenebilir.

-----

·         **KAPE**

**Hızlıca** hiveları, Anahtarları, logları ve daha birçok şeyi almaya yarar.

**Target Collection (hedef toplama):** Hangi dosya ve klasörlerin toplanacağını belirleyen kurallar seti. Yani “şu klasörü al, şu log dosyasını kopyala” gibi.

**Module Execution (modül çalıştırma):** Belirlenen programların çalıştırılması. Bu programlar, toplanan dosyalar üzerinde analiz yapabilir ya da sistemden canlı olarak başka bilgiler çekebilir.

**Target** → hangi dosyaları toplasın. Target = Topla
**Module** → bu dosyaları nasıl işlesin. Module = İşle
![[Pasted image 20251108222811.png]]**Target Source:** Nereden veri toplanacak?

**Target Destination:** Toplanan veriler nereye kaydedilecek?

**Flush:** Hedef klasördeki eski verileri siler.

**Add %d / %m:** Dosya adlarına tarih ekler, hangi gün toplandığını anlamak için faydalı.

**Target:** Listeden istediğin hedefi işaretle.

**Process VSCs:** Volume Shadow Copy (gölge kopyalar) da toplansın mı?

**Container:** Sonuçları paketle → ZIP seçersen bütün veriler sıkıştırılmış halde çıkar

-----

**REDLİNE**

### **Disk Sekmesi (Disk Tab)**

**File Enumeration**

- Include Active Files (Raw Only)
    
- Parse NTFS INDX Buffers (Raw Only)
    
- Analyze Entropy
    
- Enumerate Imports
    
- Verify Digital Signatures
    
- MD5
    
- Include Deleted Files (Raw Only)
    
- Enumerate Exports
    
- Strings
    
- Include Files
    

**Disk Enumeration**

- Disks
    

---

### **System Sekmesi (System Tab)**

**System Information**

- Machine and OS Information
    
- Registry Hive Enumeration
    
- User Accounts
    
- Analyze Prefetch
    

---


### **Network Sekmesi (Network Tab)**

**Network Information**

- Port Enumeration
    
- DNS Tables
    

**Browser History**

- Form History
    
- URL History

### **Other Sekmesi (Other Tab)**

**Services**

- MD5
    

**Tasks**

- MD5
    

**Common Persistence Mechanisms**

- Analyze Entropy









----
### Sonrası

- Ardından ‘**RunRedlineAudit.bat**’ dosyası yönetici olarak açılır. Çalıştıracağımız ve verileri sistemden alıp sınıflandıracak olan ana betiktir.
•	Cmd ekranın kapanana kadar beklenmeli sonrasında veriler Sessions klasörüne gelicektir.
•	İşleme tamamlandıktan sonra AnalysisSession1 klasörüne gidip ‘AnalysisSession1.mans’ uzantılı dosyayı redline.exe ile çalıştırılması gerekmekte.

•	İkinci seçeneği, yani “Harici bir soruşturma ipucuna dayalı olarak bir ana bilgisayarı inceliyorum” seçeneğini seçeceğiz.
•	Eğer tarayıcı adli bilişimiyle ilgileniyor olsaydık, üçüncü seçeneği seçerdik.
Benzer şekilde, bilinen saldırı göstergelerini (IOC) kullanarak tehdit avı yapıyor olsaydık, son seçeneği tercih ederdik.
•	İlk seçenek ise, kurum FireEye Endpoint Threat Prevention Platform (HX) kullanıyorsa faydalıdır; bu durumda tüm süreç çok daha hızlı ve otomatik olur.

![[Pasted image 20251109153340.png]]
Sol taraftan istenilene şeyler seçilip arama yapılabilir.

### Redline İmaj Analizi

·         winlog --> Elindeki Event İDleri kullanarak ilk bilgileri edin.

·         File download History --> Neler indirmiş ayrıntılı incele

·         prosses port --> süpheli dizinlerdeki şüpheli remote ip adreslerini ve diğer ip adreslerini incele

·         registry --> buna dair bilgileri not aldın hepsini dene

·         tasks --> genel olarak creat tarihlerine bak

·         File download History --> ne indirmiş ayrıntılı incele

·         port --> süpheli dizinlerdeki şüpheli remote ip adreslerini ve diğer ip adreslerini incele

-          Beklenmeyen yerden çalışan EXE/DLL %AppData%, %LocalAppData%, %ProgramData%, %Temp%, Recycle.Bin, C:\Users\<user>\Downloads

-          Sahte System32 (system32)

-          Parent Name / Parent PID

-          Hashler (kontrol edilemek için)





