Docker Volume Container Dısı Veri Saklama

Docker Volume’sler container, image gibi docker objesidir.

Bunları container ve image’lar gibi yaratıyoruz.

Docker Volume yarattıktan sonra o containera  x klasörü volume yazabiliyoruz.

**docker volume create ilkvolume** = volume olusturma komutu.

**docker volume inspect ilkvolume** = ilk volume detaylarını görüyoruz.

Yarattığımız dosya fiziksel olarak mountPoint üzerinde kalıyor.

**docker container run -it -v ilkvolume:uygulama alpine sh;**

docker run ile container olusturduk,

-it ile interactive bağlantı actık,

-v voluma bağlamak istediğimizi belirttik sonrasına voluma adını yazdık.

: ekleyip sonradan bu volume container icinde hangi klasöre bağlamak istiyorsak onu yazıyoruz(uygulama)

Sonra **alpine** image’ndan yararlanıyoruz ve **sh** ile de **shell** aç diyoruz.

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/c1.png)

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/c2.png)

Yukarıda volume olusturduk sonra bilgileri listeledik. 

**Touch abc.txt ile dosya ekledik**

**Echo ile dosyaya bir sey ekleyip cat ile onu gösterdik.**

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/c3.png)

Yukarıda olusturduğumuz volume’sildik ve yeni bir tane olusturduk en altta.

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/c4.png)

**Yukarıda yeni bir volume olusturduk ve daha önce yazdığımız dosya ve icindeki yazı yeni volumeda da geldi. Volume bize bunu sağlıyor dosyaları container dısında tutmamızı sağlıyor.**

**Bir volume birden fazla containera aynı anda bağlayabiliyoruz.**

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/c5.png)

**Yukarıda touch ile yeni dosya ekledik ve volume’dan cıktık yeni bir volume olusturuyoruz.**

**İlk basta bulamadı onu da centos image’nı bulamadı, docker hub’dan bulup cekiyor ve buna bağladı.**

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/c6.png)

**yukarıda yine ücüncüdosyayı touch ile ekleyip echo ile yazı ekleyip cat ile okuduk buna baska container acsak da bunlara erisim sağlıyoruz.**