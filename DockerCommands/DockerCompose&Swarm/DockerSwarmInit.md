https://labs.play-with-docker.com/?stack=https://raw.githubusercontent.com/docker-library/docs/f6c9b596064e2eed9c3b6ac75bea606cb6d94099/mongo/stack.yml


örnek olarak ;

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image59.png)

Yukarıda 4 tane sunucu olusturduk.
24 sunucuda swarmi init edeceğiz.
Yukarıdaki komutta swarm init diyerek 24 icinde yeni bir swarm olusturuyoruz. Advertise ip adresi olarak da 24 olan ip adresini veriyoruz. İp girmemize gerek yok ama birden fazla networke bağlıysa farklı farklı ip ler olacğaı icin burada ip yi vererek bunu belirlemiş olduk.

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image60.png)

Docker swarm olustu. Ve 24’ü manager olarak atadı.

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image61.png)

Yukarıdaki komutlarla manager olusturmak veya worker olusturmak istediklerimizin komutlarını isteyip görebiliyoruz.

![img](https://github.com/ibrahimdoss/Docker/blob/3e34c009736834bef2865148d57a4bad49a63496/Images/Compose&Swarm/image62.png)


Yukarıda container olusturma komnutu var.
Test adında bi servis olustur kac tane olduğunu replicanın yanında belirtiyoruz. 5 tane olacağını belirttik. -p yani publish port ile portundan publish edilecek. Hangi imajdan alacak en son onu belirtiyoruz(nginx)

