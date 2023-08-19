## DOCKER

**Docker, uygulama geliştirmek, dağıtmak ve çalıştırmak için oluşturulan açık bir platformdur.**

**Docker, uygulamalarınızı altyapınızdan bağımsız kılmanızı sağlar, böylece yazılım üretim ve dağıtım sürecinizi hızlandırabilirsiniz.**

**Docker ile altyapınızı, uygulamalarınızı yönettiğiniz gibi yönetebilirsiniz.**

**Docker’ın hızlı nakliye, test etme ve kodu dağıtma metodolojilerinden yararlanarak, kod yazma ile üretimde çalıştırma arasındaki gecikmeyi önemli ölçüde azaltabilirsiniz.**


## Docker Engine 

Docker firması açık platformu yaratan ve ortaya çıkaran firmanın adıdır.

Bu platformun altında birçok çözüm sunulur ve bunların en temelinde Docker Engine bulunur.

**Docker Engine Docker platformunun kalbi diyebiliriz.**

**Docker Engine linux veya windows bir sistem üzerine kurduğumuz server-client mimarisinde bir uygulamadır.**

3 temel componenti vardır:

•	**Docker Daemon**
•	**Docker Rest API**
•	**Docker CLI**

**Docker Engine ‘n temelini olusturan Docker Daemon’lar container, image, network, data volumes docker objelerini yaratmayı ve yönetmeyi sağlar.**

Yani bunu bir linux sisteme kurar bunun üzerinde container kurup çalıştırabiliriz.

Bu Daemon Rest API ile dış dünyaya görüşebilir. (**Docker Rest API**) 

Diğer programlar Docker Daemon ile Rest API ile aracılığıyla konusur ve ona ne yapması gerektiğini söyler. 

Rest API’nin en önemli kullanıcısı da **Docker CLI**’dır.

Yani Docker CLI docker komut satır arayüzüdür.

Bir Docker Engine kurduğumuz zaman o makinede hem Docker Daemon yani Docker Server hem de Docker CLI yani Docker Client uygulaması kurulur.

Bu Client uygulamasını kendi pc’mize kurarak örneğin cloud’da kurduğumuz bir Docker Engine bağlanıp kendi bilgisayarımızdan o Docker Daemon’I yönetebiliriz. Yani bunlar birbirinden ayrı uygulamalardır.

**ÖZETLE**;

**Docker Engine container, image ve  onların tamamlayıcı objeleri olan network ve volumes objeler olusturup, yönetmemizi sağlayan Docker Daemon ve o Daemon ile iletisim kurmamızı sağlayan Rest API ve Docker CLI’dan olusan ürüne verilen isimdir.**

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/b5.png)