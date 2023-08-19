
![inmage](https://github.com/ibrahimdoss/Docker/blob/main/Images/b1.png)

**Ciddi veriler ile uğraşırken prod ortamlarında veri saklamak icin kullanacağımız tek yöntem volume’lerdir.**

**Kendi dev ortamımız, test ortamı vs gibi durumlarda container dısında baska veri saklama yöntemi de Bind Mounts’dır.**

![inmage](https://github.com/ibrahimdoss/Docker/blob/main/Images/b2.png)

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/b3.png)

**docker container run -d -p 80:80 --name ilkweb nginx** = nginx image’ndan container olusturduk, dosyayı bulamadığı icin docker hub internet üzerinden bulup indirme islemi yaparak bu islemi gerceklestirdi.

Bu image’dan bir container yarattık.(nginx image)

**docker exec -it 6d02 sh** = containere bağlandık. ( **6d02 image id’nin ilk dördü**)

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/b4.png)

**docker container run -d -p 80:80 -v** 

**C:\Docker\DockerApps\AdanZyeDocker\kisim3\bolum28\websitesi:/usr/share/nginx/html nginx** = Burada normal bağlanma islemlerini yapıyor -v’den sonra bizim görmek istediğimiz dosya yolunu veriyoruz. Sonrasında : bırakıp hangi dosyanın yerine görmek istiyorsak onu ekliyoruz.**( /usr/share/nginx/html) bunu da nginx’ imagendan olustursun diye en sona nginx ekliyoruz ve olusturuyor.**

**Artık o ilk olusturduğumuz container üzerinden actığımız zaman (C:\Docker\DockerApps\AdanZyeDocker\kisim3\bolum28) buradaki dosya yolu açılacaktır.**
