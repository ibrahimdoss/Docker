![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image53.png)

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image54.png)

Swarm ayrı bi arac olarak gelmiyor. Docker swarm engine ile birlikte geliyor. Docker engine icindeki bi nokta sadece. Aktif etmek yeterli oluyor.
Swarm kurmak için : Sunucuların birbirileriyle hızlı ağ bağlantısı ile birlikte olmalı. Ms seviyesinde.

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image55.png)

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image56.png)


İlk sunucu da docker swarm init komutu calıstırıp docker swarmı aktif ediyoruz. Bu sistem artık docker swarm manager oluyor. Artık ortamda cluster ve bu clusterı da yönetecek olan makine de  bu. Bu artık tüm docker ortmaını yönetecek. Yapılmasını istenileni artık bu makineye söyleyeceğiz.

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image57.png)

Diğer sunucularda da aktif edeceğiz ve bunlara ortamda docker swarm cluster mevcut git ona kayıt ol. Yani bu sunucular gidip docker swarm clustera worker node olarak bağlanacaklar.
Workerlar managerdan gelecek talimatları bekliyorlar.

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image58.png)

Manager komutu alıyor, workerlara bakıyor müsait olana emiri veriyor ve workerlarda emiri dinleyerek yaratıyor. Her worker node islemi tamamladığın da managera bildiriyor.
Managerin amacı bizim söylediğimiz isi worker nodelarla iletisim kurup onlara söylemek.
Clusterı sürekli gözleyerek, söylediğimiz seyin olup olmadığını kontrol ediyor. 
Diyelim ki sonuncu sunucu da bi arıza cıktı makine kapandı. Managerdan 5 tane istemistik ama dört tane var, manager bunu fark ediyor ve  eksik durumu fark edip istenilen durumu sağlamaya calısıyor. Bunu da müsait olan worker nodelara bi tane daha container olusturuyor ve sonucta yine 5 tane nginx container olmus oluyor ve gözlemeye devam ediyor.