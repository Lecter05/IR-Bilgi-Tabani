jobs > arka planda çalışan uygulamaları gösterir
ps > Çalışan süreçleri listelemek 
ps aux > Tüm süreçleri ayrıntılı olarak göstermek 
Pstree > proses dal şekilinde.
top > aktif prosesleri incelenir.


ls -la /proc/<PID> --> süreç hakkında kim çalıştırıyor, izinler, hangi dosyalara bağlı
ls -la /proc/<PID>/exe --> süreç tarafından çalıştırılan  exe'ye işaret eden symbolic linki gösterir.
ls -la /proc/<PID>/fd --> o süreçin “neyi tutup sesizce sakladığını” gösteren en hızlı delil kaynağı.