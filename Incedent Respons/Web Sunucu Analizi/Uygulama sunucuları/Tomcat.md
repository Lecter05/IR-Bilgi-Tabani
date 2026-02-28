çift kez kodlanmış .. (%252e%252e) kullanarak dizin atlama yapılmış. Bu, mod_jk ve Tomcat’in URL decode sırasındaki boşluğu kullanarak /manager/html gibi yönetim sayfalarına gizli erişim sağlar.
İndidaktör olarak kullanılabilir. %252e%252e
![[Pasted image 20251102142245.png]]•	cat access.log | grep manager/html | grep 200
•	cat access.log | grep 192.168.68.1 | grep 200
