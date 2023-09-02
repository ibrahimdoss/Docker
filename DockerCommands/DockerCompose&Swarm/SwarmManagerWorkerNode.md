![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image78.png)

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image79.png)


![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image80.png)

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image78.png)


https://raft.github.io/
https://www.youtube.com/watch?v=RHDP_KCrjUc

swarm init dediğimiz de manager oluyor da etcd’ye(key-value deposu yani veritabanı) bağlanıyor ve burada key-value esleniği seklinde veri tutabiliriz. Cluster ile ilgili tüm veriyi bi yerde tutması gerekir.
Swarm tüm bu kaydetme isleri icin etcd’yi kullanır.

Burada swarm managerin worker nodelarla trafiğini ve iliski durumu icin tüm bilgileri sifrelenmis sekilde saklar.
Swarm 2 adet random token yaratır. 1 tanesi manager eklemek icin, 1 tanesi de worker node eklemek icin. Bunlar sayesinde manager ve worker ekleyebiliriz.
Manager node eklemek icin tokeni alıp manager node ekleriz. Worker node eklemek icin de tokeni alıp worker node ekleriz.