Normal şartlarda, Domain Controller'lar (DC) veritabanlarını güncel tutmak için birbirleriyle konuşurlar (Replikasyon)
- **Saldırı Mantığı:** Saldırgan, ele geçirdiği bir yetkili hesabı kullanarak Domain Controller'a şöyle der: _"Merhaba, ben de bir Domain Controller'ım. Bana veritabanındaki şifreleri (hashleri) gönder, senkronize olalım."_
- **Sonuç:** DC bu isteği kabul ederse, saldırgan **KRBTGT** hesabı dahil tüm kullanıcıların şifre özetlerini (hash) ele geçirir.

Tespiti Event ID 4662

