* Kullanıcı A bir sunucuya (B) kimlik doğrulaması yapmak istiyor.

* Saldırgan C, A ile B arasına girip A’dan gelen NTLM istemini yakalar.

* C bu istemi B’ye iletir. B, A yerine C’den gelen isteği doğrular çünkü NTLM relay mekanizması bunu engellemez.

* Sonuç: Saldırgan, A rolünde B’ye erişir.

Kısaca;
Saldırgan istemcinin NTLM İsteğini yakalar, hedefe iletir, dönen yanıtı kullanarak orijinal istemciyi taklit eder. Nmap ile SMB imzalaması devre dışı bırakılmış uç noktaları keşfeder.


**nmap --script=smb2-security-mode.nse -p445 192.168.230.0/24**
![[Pasted image 20251031113143.png]]
Burada, smb imzalamayı kontrol eden ve tüm ağı (aktif dizini çalıştıran) tarayan Nmap'in yerleşik bir betiği kullanılıyor.

Burada, SMB imzalamasının kullanıcı iş istasyonları için etkinleştirildiğini, ancak zorunlu olmadığını görüyoruz; bu da bir ZORUNLULUK olmadığı için saldırımızın yine de çalışabileceği anlamına geliyor. Etki alanı denetleyicisi için imzalama etkin ve zorunlu. Bunların hem iş istasyonu hem de Windows sunucusu için varsayılan ayarlar olduğunu unutmamak önemlidir.
![[Pasted image 20251031114720.png]]
Kullanıcı (Jon Snow) yanlış bir dosya paylaşım yolu girer (`\\192.168.230.100\Sare`). DNS çözümleyemeyince sistem **LLMNR**’yi kullanır.  
Saldırgan **Responder** aracıyla sahte LLMNR sunucusu kurar ve kullanıcının **NTLM hash**’ini ele geçirir.  
Ardından **ntlmrelayx** aracıyla bu hash’i hedef makineye (SMB signing kapalı olan Workstation-01) ileterek kimlik doğrulaması yapar ve makineden hash’leri çeker.


"Responder" adında, aracı görevi gören ve Active Directory ortamlarındaki ağ saldırılarının çoğunda kullanılabilen bir araç var. **Şimdi, bir saldırganın dahili ağda aktif bir dinleyicisi olacak.**
![[Pasted image 20251031115546.png]]

**python3 ntlmrelayx.py -tf target.txt -smb2support**
Buradaki target.txt dosyası, saldırganın hedef almak istediği uç noktanın IP adresini içerir.
![[Pasted image 20251031115626.png]]

Kullanıcı jonsnow, WORKSTATION-02’den hatalı bir dosya paylaşım yolu girdiğini varsayalım.
Bu yol erişilmeye çalışıldığında mevcut olmadığı için yukarıda açıklandığı gibi NTLM relay saldırısı tetiklenir.

![[Pasted image 20251031115833.png]]
ntlmrelayx çıktısında WORKSTATION-01’e ait hash’ler dökülür. Saldırganın başlangıçta erişimi sadece WORKSTATION-02 (192.168.230.133) idi; ancak NTLM relay sayesinde artık tamamen farklı bir makineye — WORKSTATION-01 (192.168.230.134) — erişim sağlamış olur. Saldırganlar bundan sonra lateral hareket yapabilir veya yetki yükseltme denemelerine girişebilir.






















