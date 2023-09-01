![img](https://github.com/ibrahimdoss/Docker/blob/f222c926a2f681e5f78d1d01b8d6b7b49558cf04/Images/Compose&Swarm/image-28.png)

Burada öncekine nazaran image yazan yerde build var tanımlarken build yazıp bosluk bırakıp . koyuyoruz. Bu su demek oluyor ;
Docker-compose yml dosyası ile bi servis olustururken o servisin imajını da dockerfile kullanarak olustur ve bu servisi de bu imajı kullanarak ayağa kaldır demek.

![img](https://github.com/ibrahimdoss/Docker/blob/f222c926a2f681e5f78d1d01b8d6b7b49558cf04/Images/Compose&Swarm/image-29.png)

Yukarıda build : . komutu burayı calıstırıyor.
Bunu burada yapmak zorunda değiliz. Dockerfile ile imaj yaratıp sonra compose da calıstırılabilir.
Test ortamlarında vs CI/CD sistemlerinde bu sekilde kullanılabilir.
Compose ya gelistirme ya da test sistemlerinde testleri olustururken kullanılıyor.
