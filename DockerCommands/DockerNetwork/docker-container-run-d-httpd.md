Öncelikle, docker container run -d httpd komutuyla detach modda bir container yaratıp çalıştıralım:

image -1 


Ardından **docker network inspect bridge** komutunu çalıştırırsak, çıktı olarak biraz önce yarattığımız container'ın bu bridge'e default olarak bağlandığını ve MAC adresi, IP adresi gibi bilgilerini görürüz:

image -2


Bir container'a **docker exec -it containerID sh** komutu ile bağlanalım içeride **ifconfig** komutunu çalıştıralım. Burada gördüğümüz IP adresi biraz önce bridge'i inspect'lediğimizde gördüğümüz IP ile aynıdır:

image -3


Şimdi "host" objesine geçelim. Daha önce de dediğimiz gibi, host objesine bağlı container'ların hiç bir network izolasyonu yoktur ve çalıştıkları sistemin ağ altyapısını aynen kullanırlar.

**docker container run -it --name deneme1 --net host httpd sh** komutu ile, network'ü bridge değil de host olan bir container yaratıp bağlanalım. Burada da **ifconfig** komutunu çalıştırdığımızda container'ın IP adresinin host makine ile aynı olduğunu görebiliriz. Yani bu şekilde network izolasyonunu ortadan kaldırmış oluruz:

Görmüş olduk ki, bridge network'ü sayesinde container, üzerinde çalıştığı host'un adaptörlerini direkt kullanmaz. Ayrı bir sanal ağda çalışır. Host network'ünde ise container, üzerinde çalıştığı sistemin ağ altyapısını direkt kullanır, arada herhangi bir izolasyon yoktur.

Şimdi "none" objesine bakalım. **docker container run -it --name deneme --net host httpd sh** komutu ile none network objesine sahip bir container yaratıp içine bağlanalım. Burada **ifconfig** komutunu çalıştırdığımızda sadece **"Loopback"** olduğunu görürüz. Yani başka herhangi bir network bağlantısı yoktur:

image -4