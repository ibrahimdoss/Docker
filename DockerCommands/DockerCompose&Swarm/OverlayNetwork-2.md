![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image69.png)

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image70.png)

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image71.png)

Artık ortamda swarm olduğu zaman swarmı kapsayan tüm isler manager node üzerinde yapılmalı. Worker üzerinde islem yapmaz çünkü managerlar etcd ye bağlı workerların etcdye bağlantısı yok.

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image72.png)

Overlay network created.

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image73.png)

Over-net networkün özellikleri.

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image74.png)

Yukarıda servis olusturma.
Name kısmında servisin adı.
Network kısmında olusturduğumuz networkün adı. -p ile gelenleri 80 portuna yönlendir ve replica ile 3 tane task  olusturmasını istedik. Hangi imajdan cekeceğini belirttik(ozgurozturknet/web)

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image75.png)

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image76.png)

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image77.png)

Db servisinin containerı nerede bakmak icin 

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image78.png)

Bi servis olusturulduğu zaman o servisin ismiyle bi tane VIP yaratılır ve servisin ismi servis name ile eslesir. Bir nevi load balancer diyebiliriz.