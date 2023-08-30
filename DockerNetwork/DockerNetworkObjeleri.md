![image](https://github.com/ibrahimdoss/Docker/blob/main/DockerNetwork/NetworkImages/net1.png)

Docker kurulumuyla birlikte 3 adet network objesi geliyor.(bridge,host,none).

Bridge, hem bu driverın adı hem de dockerın default olarak olusturdugu ilk networke aynı isim veriliyor.

Yeni bir container olusturup hangi networke bağlanacağını belirtmezsek otomatik olarak bridge networküne bağlanır.

Host driver ile olusturulmus host network ise buna bağlayacağımız containerlar sanki bu makine üstned calısacak process gibi calısır.

None ise bağlayacağımız containerların hicbir sekilde auth yapısını kullanmaması sağlar.

![image](https://github.com/ibrahimdoss/Docker/blob/main/DockerNetwork/NetworkImages/a2.png)

yukarıda network objesinin tüm özelliklerini listeledik.

Inspecti diğer objelerde de kullanabiliriz. Objelerin detaylı özelliklerini inspect ile öğrenebiliriz.

![image](https://github.com/ibrahimdoss/Docker/blob/main/DockerNetwork/NetworkImages/a3.png)

Birden fazla ağdan tek birleşik ağ yaratmaya yarıyor.(bridge)

Bridge dediğimiz sey host üstünde yani o makine üstünde bir tane VM docker0 yaratır ona da 172 ile baslayan ip adresini verir.

Yeni bir docker container yaratırız ve hangi networke bağlanacağını belirtmezsek o zaman o container bridge networküne bağlanır.

Containerın paketleri teslim edeceği yer olarak da docker0 interfacenin adresini verir. Bu container dıs dünya ile haberleseceği zaman paketi buraya teslim eder daha sonra paket bu bridge ile ana hesap networküne aktarılıp ve nereye gidecekse gider.

Containerı kapatıp ama bağlantıyı kapatmamak icin ctrl+PveQ yapmak yeterli.

![image](https://github.com/ibrahimdoss/Docker/blob/main/DockerNetwork/NetworkImages/a4.png)

Ifconfig ile ip adresine vs bakabiliriz.

**Host**;

Buna bağlı containerler hicbir network izolasyonu yoktur, calıstıkları sistemin ağ yapısını aynen kullanırlar. 

**None**

![image](https://github.com/ibrahimdoss/Docker/blob/main/DockerNetwork/NetworkImages/a5.png)

Sadece loopback adaptor var, baska bir ethernet veya network bağlantısı yok. Herhangi bir yere bağlanamıyor, erisemiyor.

Bir container olusturup onu herhangi bir network bağlantısı olmasını istemezsek onu none networke bağlarız ve onun icinden herhangi bir network alısverisi olmayacak ve ulasamayacaktır.
