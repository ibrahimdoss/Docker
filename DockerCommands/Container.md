Öncelikle docker container run komutu, docker container create ve docker container start komutunun birleşimidir.

Her image'da, o image'dan bir container create ettiğimiz zaman default çalışması için ayarlanmış bir uygulama vardır. Container, bu uygulama çalıştığı sürece ayakta kalır. Uygulama çalışmayı bıraktığında container da kapatılır.

Peki image'ın içinde sadece tek bir uygulama mı var? Hayır bir Docker image'ının içinde birden fazla uygulama olabilir. Sadece tek bir uygulama içermelidir gibi bir kural yok. Fakat Docker, container start edildiğinde default çalışması için yalnız tek bir uygulamanın ayarlanmasına izin verir. Bunun hangi uygulama olacağını container yaratılırken belirtebiliriz.

**Desc-2**

Container ?

Uygulamaları aynı sistem üzerinde birbirlerinden izole şekilde çalıştırmaya container diyoruz.
Basit olarak isolation. ( izolasyon) Diyebiliriz.

![Container](https://github.com/ibrahimdoss/Docker/blob/main/Images/container.PNG)

