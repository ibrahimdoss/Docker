# Docker Settings

![Docker Settings](https://github.com/ibrahimdoss/Docker/blob/main/Images/st1.png)

**Start Docker Desktop when you log in** = bu isaretlendiği zaman bilgisayar acıldığın zaman docker otomatik başlatılacak.

Expose Daemon TLS (2.kısım) = TLS ile daemonu expose et.

**Use the WSL 2 based engine** = WSL 2 ‘ ile windows üzerinde dockerı calıstırıyoruz.

**Send Usage Statistics** = Docker ile alakalı istatistiği dockera gönderip göndermemeyi sectiğimiz kısım.

![Docker Settings](https://github.com/ibrahimdoss/Docker/blob/main/Images/st2.png)

Docker Desktop bu makinenin üzerine bi VM olusturup onun üzerine docker engine yüklüyor. Burada da oVM ne kadar CPUs, Memory, Swap ne kadarlık alan ayırmasını izin vermis oluyoruz. Yukarıdaki image’de gözükmeme sebebi WSL 2 kullanıldıgı icin. Eger ayrı bir VM olusturup docker engine kullansaydık burada görülecek kısım asagıdaki görseldeki gibi.

![Docker Settings](https://github.com/ibrahimdoss/Docker/blob/main/Images/st3.png)

**File Sharing** kısmı bind mounts’ları kullanabilmek icin izin veriyoruz.

**PROXIES** = direkt internete değil de bir proxy üzerinden bağlanıyorsak buraya proxy ayarlarını giriyoruz.

NETWORK = burada dockerın kullanabileceği subnetleri belirliyoruz. Manuel DNS configurasyonda yapılabilir. Böylece Docker Engine internete cıkarken sistemin yerine bu DNS’i kullanıyor.

![Docker Settings](https://github.com/ibrahimdoss/Docker/blob/main/Images/st4.png)

Docker engine kısmında ise Docker Daemon üzerinde yapabileceğimiz ayarlar kısmı.

Kubernetes üzerinde gelistirme yapmak istiyorsak bu sisteme single-node bir cluster olusturup kullanabiliyoruz. Onun ayarları.

![Docker Settings](https://github.com/ibrahimdoss/Docker/blob/main/Images/st5.png)