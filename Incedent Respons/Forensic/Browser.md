Search history – Arama geçmişi
Visited Websites – Ziyaret edilen web siteleri
Downloads – İndirilen dosyalar
Cookies – Çerezler
Cache – Önbellek
Bookmarks – Yer imleri
Favicons – Site simgeleri
Sessions – Oturumlar
Form history – Form geçmişi
Thumbnails – Küçük önizleme resimleri
Extensions – Eklentiler

### Search History
C:\Users\bayra\AppData\Local\Google\Chrome\User Data\Default\History
“keyword_search_term" tablosunun altındadır. History adlı SQLite veritabanında saklanır. Kullanılan tüm arama terimleri görütülebilir.

### Visited Websites (girilen siteler)
C:\Users\bayra\AppData\Local\Google\Chrome\User Data\Default\History
VİSİT tablosunun görüntülebilir. History adlı SQLite veritabanında saklanır.

### **Downloads**
C:\Users\bayra\AppData\Local\Google\Chrome\User Data\Default\History
**downloads_url_chains** ve **downloads** tablolarında görüntülebilir. **History** adlı SQLite veritabanında saklanır.


Cookies (çerezler)
Google AppData\Local\Google\Chrome\User Data\Default\Network\Cookies 
Firefox \AppData\Roaming\Mozilla\Firefox\Profiles\[rastgele klasör adı]\cookies.sqlite
Edge AppData\Local\Microsoft\Edge\User Data\Default\Network\Cookies
Opera AppData\Roaming\Opera Software\Opera Stable\Network\Cookies 


### Cache
ziyaret edilen sayfalar ve görseller gibi verilerin geçici depolanır, web geçmişini yeniden oluşturmayı, kullanıcının sıkça ziyaret ettiği siteler gibi kanıtlar ortaya çıkarılabilir.
Google → AppData\Local\Google\Chrome\User Data\Default\Network\Cookies
Firefox → AppData\Roaming\Mozilla\Firefox\Profiles\[rastgele klasör adı]\cookies.sqlite
Edge → AppData\Local\Microsoft\Edge\User Data\Default\Network\Cookies
Opera → AppData\Roaming\Opera Software\Opera Stable\Network\Cookies

### **Bookmarks (Yer imleri)**
Chrome → \AppData\Local\Google\Chrome\User Data\Default\History  
Edge → \AppData\Local\Microsoft\Edge\User Data\Default\History  
Opera → \AppData\Roaming\Opera Software\Opera Stable\History  
Firefox → \AppData\Roaming\Mozilla\Firefox\Profiles\[randomfoldername]\places.sqlite
![[Pasted image 20251116214227.png]]

### **Extensions (Uzantılar)**
Chrome → \AppData\Local\Google\Chrome\User Data\Default\Extensions\{randomfoldername}\*
Edge → \AppData\Local\Microsoft\Edge\User Data\Default\Extensions\{randomfoldername}\*
Opera → \AppData\Roaming\Opera Software\Opera Stable\Extensions\{randomfoldername}\*
Firefox → \AppData\Roaming\Mozilla\Firefox\Profiles\[randomfoldername]\extensions\*






### favicons
C:\Users\bayra\AppData\Local\Google\Chrome\User Data\Default\ **favicons**
**favicons** tablosu, tarayıcı geçmişi silinse bile **ziyaret edilen bazı sitelerin izlerini** tutabilir.  
Bu tablo, **favicon’u (site simgesi)** alınan web sitelerini listeler.


#### Top Sites
C:\Users\bayra\AppData\Local\Google\Chrome\User Data\Default\Top Sites
kullanıcının tarayıcı alışkanlıklarını ve öncelikli olarak ziyaret ettiği siteleri gösteren önemli bir kanıt kaynağıdır.

### Web data
Geçmiş silinse bile kullanıcı bilgileri kaydettiği hassas veriler burada kalır.
**autofill, autofill_profile_addresses, credit_cards**


### Uzantılar (Extensions)

C:\Users\bayra\AppData\Local\Google\Chrome\User Data\Default\Extensions

**İdm, reklam ad block gibi şeyler. Aranacak kelimeler** ** --> extension name veya iconlardan tahmin et**

Browser Extension nasıl araştırılır. 
•	öncelikle sana bir FinanceEYEfeeder.crx uzantılı dosya verlir bunu zip yapıp sonra unzip yapabilirsin veya (https://crxextractor.com/) bu sitede direk alabilirsin içerisindeki dosyaları.
•	tarayıcı uzantısı risk analiz aracı, içerisindeki URL' leri tespiti ve kapsamı gözlemlenebilir --> crxcavator.io veya ExtAnalysis


### Araçlar

strings64.exe -a "C:\Users\bayra\AppData\Local\Google\Chrome\User Data\Default\Sessions\Session_13407757608505190" > "C:\Users\bayra\Desktop\tekke.txt"
- O anda açık sekmeler
- Açık olan sitelerdeki bazı veriler (bence gereksiz gibi son ihtimal bunlara bakılmalı)

**hindsight**
Tüm browser artefaktlarını tek timeline’a döker
SQL tabanlı arama yapabilir


