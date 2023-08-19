**Linux Container** = uygulamaları izole birer process olarak çalıştırmaktır.

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/a12.png)

Yukarıdaki örnekte önce fiziksel sunucumuza bir tane linux sistem kurduk.

Sonra java kurulumu yaptık.

Sonra gerekli library vs kurulumu yaptık.

En son ise uygulamamızı ekledik.

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/a13.png)

Yukarıda işletim sistemi çekirdeğini çıkardık.

Sonra tüm bu dosyaları bir paket haline getirip depolayalım. **Buna ise Docker Image yaratmış olduk. Temelde Image dediğimiz şey budur.**

**IMAGE** = Bir uygulamanın ve onun içinde çalışması gereken tüm ek libraryler ve diğer öğelerin paketlenmiş haline **docker ımage** deriz. 

**İçinde Kernel çekirdek yoktur.** Çünkü containerlar üstünde koştukları işletim sisteminin kernelini kullanırlar. Dolayısıyla bir docker imagende kernel’a ihtiyaç yoktur.

**İmportant** : Eğer bu Docker Image’nı erişebileceğimiz bir yerde depolarsak, Docker Engine yüklü herhangi bir PC’de bu image indirir ve bu image den istediğimiz kadar container olusturabiliriz.


**Container**;

**Container: Yaratmıs olduğumuz image’n bir nevi çalışır halidir.**

Image bir şablondur, onu yaratır ve depolarız. Daha sonra bu şablondan istediğimiz kadar container yaratır ve çalıştırırız. 

**Image** sadece **okunabilir** bir ana **şablondur**.

**Container** ise bu **şablondan** **oluşturulmuş** çalışan bir **kopyadır**.

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/a14.png)
