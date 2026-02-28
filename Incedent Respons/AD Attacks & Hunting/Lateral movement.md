https://web.archive.org/web/20240915011512/https://hackmag.com/security/lateral-guide/

**Lateral Movement**

**Strateji Notu:** Saldırgan ağ içerisinde aktif olarak ilerlediğinden ve sistemlere erişim sağlamaya devam ettiğinden, olası kanıt kayıpları göze alınarak sürecin en başına RAM/İmaj alma değil; EDR bağlantısını koparmadan yapılacak **SİSTEM VE HESAP İZOLASYONU** konulmuştur.

**Triage:**

• Olayı/Vakayı Ticket olarak aç.

• Bildirimi yapan kaynağı (SIEM, EDR alerti, Kullanıcı, Threat Hunt) kaydet.

• Tespit edilen ilk şüpheli kaynağı (IP/Hostname) ve kullanılan kullanıcı hesabını belirle.

**İzolasyon ve Önleme (ÖNCELİKLİ ADIM):**

• Etkilenen sistemleri EDR üzerinden ağdan izole et _(Dikkat: EDR'ın kendi yönetim sunucusuyla haberleşebilmesi için gerekli portların/istisnaların izolasyon kuralında açık olduğundan emin ol)_.

• EDR izolasyonu çalışmazsa veya EDR servisi durdurulmuşsa (Defense Evasion), switch portunu kapat veya sistemi karantina VLAN'ına al.

• Ele geçirildiği (veya Pass-the-Hash/Ticket ile kullanıldığı) düşünülen kullanıcı ve servis hesaplarını kilitle (Disable), parolalarını sıfırla.

• Etkilenen hesapların aktif Azure AD / MFA oturumlarını (Token'larını) sonlandır.

• Gerekirse ağ genelinde yanal hareket portlarına (SMB/445, RDP/3389, WinRM/5985-5986, WMI/135) giden trafiği geçici olarak kısıtla veya blokla.

**Volatil Veri Toplama ve Kanıt:**

• Sistemi KESİNLİKLE YENİDEN BAŞLATMA VE KAPATMA (Şifreleme anahtarları veya dosyasız/fileless zararlılar RAM'den silinmesin).

• İzole edilmiş sistemden EDR "Live Response" konsolu veya güvenli lokal araçlar ile RAM Dump al.

• Olay müdahale veri paketini (Triage data: Event Logs, Prefetch, MFT, ShimCache, AmCache, Autoruns) topla.

• Gerekli görülen ve fiziksel müdahale gerektiren durumlarda disk imajı al.

**Teknik Analizi ve Kapsam Belirleme:**

• Toplanan Windows Güvenlik loglarını yanal hareket izleri için tara (Örn: Event ID 4624 Network Logon, 4672 Admin Logon, 5140/5145 Network Share, 7045 New Service Installed).

• Saldırganın kullandığı aracı ve tekniği (PsExec, PowerShell Remoting, WMI, RDP Hijacking, Cobalt Strike) tespit et.

• Sıçrama yapılan diğer sistemleri haritalandır ve o sistemleri de anında "İzolasyon" adımına dahil et.

• İlk giriş noktasını ("Patient Zero") belirle.

**Eradikasyon ve Kurtarma:**

• Yanal hareket esnasında bırakılan zararlı dosyaları (Payload, script vb.) sil.

• Saldırganın kalıcılık (Persistence) sağlamak için oluşturduğu zamanlanmış görevleri (Scheduled Tasks), yeni servisleri veya eklediği local admin hesaplarını kaldır.

• Sistem güvenliğinden şüphe duyuluyorsa (veya Rootkit/tam ele geçirilme şüphesi varsa) makineyi temiz bir imajdan (Gold Image) yeniden kur.

• Temizlendiği doğrulanan sistemlerin izolasyonunu kaldır ve ağa dahil et.

**IOC Yönetimi:**

• Tespiti yapılan tüm zararlı IP, Domain ve Hash'leri EDR, Firewall ve Web Proxy üzerinde Blacklist'e ekle.

• Saldırganın yanal hareket için kullandığı komut satırı davranışlarını (LOLBAS komutları vb.) SIEM sistemine tespit kuralı (Rule/Alert) olarak tanımla.