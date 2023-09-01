Resource : **https://yaml.org/**
**https://yaml-online-parser.appspot.com/**
**https://www.youtube.com/results?search_query=yaml+syntax**


## docker-compose file olustururken isimlendirme “docker-compose.yml or docker-compose.yaml” seklinde olmalıdır.

![image](https://github.com/ibrahimdoss/Docker/blob/77a9a541f16e25c011aad3a017ba6e88771540c0/Images/Compose&Swarm/image19.png)

Bu versiyon docker-compose dosyasının versiyonu değil. Bu yazılan versiyon docker-compose dosyasının kullanabileceğimiz özelliklerinin versiyonu. Bundan dolayı en güncel versiyonu kullanmak mantıklıdır.

![image](https://github.com/ibrahimdoss/Docker/blob/77a9a541f16e25c011aad3a017ba6e88771540c0/Images/Compose&Swarm/image20.png)

servisleri, volumeleri ve networkleri tanımladığımız kısım.
**Services** kısmında container tanımladığımız yer. 
**Container = service**
Diğerleri zaten aynı adı gibi işlemleri içeriyor.

![image](https://github.com/ibrahimdoss/Docker/blob/77a9a541f16e25c011aad3a017ba6e88771540c0/Images/Compose&Swarm/image21.png)


Veritabanı containerı tanımlama örneği.

Isim olarak veritabanı verdik.

Veritabanı containerının hangi imajdan olusması gerektiğini tanımlıyoruz(**image**: ile)

Sırasıyla veritabanı diye container olusturduk.

Bu servisi image : mysql:5.7 imajından olusacağını belirttik.

Bu container kapatılırsa her zaman başlatılmasını belirttik ve o containera verdiğimiz volumes takılacak.

Volume birden fazla eklenebilir.

![image](https://github.com/ibrahimdoss/Docker/blob/77a9a541f16e25c011aad3a017ba6e88771540c0/Images/Compose&Swarm/image22.png)

Yukarıda ise volume olusturduk verilerim adı altında.
Sonra environmentları tanımladık sırasıyla.

![image](https://github.com/ibrahimdoss/Docker/blob/77a9a541f16e25c011aad3a017ba6e88771540c0/Images/Compose&Swarm/image23.png)

-wpnet networküne veritabanı containerını bağlamış olduk.

![image](https://github.com/ibrahimdoss/Docker/blob/77a9a541f16e25c011aad3a017ba6e88771540c0/Images/Compose&Swarm/image24.png)

Containera bağladığımız networkü burada olusturuyoruz. Bridge network driver olacağını da belirtmiş olduk.

![image](https://github.com/ibrahimdoss/Docker/blob/77a9a541f16e25c011aad3a017ba6e88771540c0/Images/Compose&Swarm/image25.png)

Depends_on ile veritabanı containerı ile depend etmiş olduk. Yani veritabanı servisi ayağa kalkmadıkca wordpress servisi de ayağa kalkmayacak.

![image](https://github.com/ibrahimdoss/Docker/blob/77a9a541f16e25c011aad3a017ba6e88771540c0/Images/Compose&Swarm/image26.png)

Bu da tanımladığımız ikinci servis(container).
Ports: burada port verebiliyoruz.
Container_name: containera isim veriyoruz.
Image: hangi imajdan olusacagını belirtiyoruz.
Restart: container kapatıldıgında tekrar başlatılmasını belirtiyoruz.
Links: veritabanı containerı ile linkliyoruz.
Environment: environmentları tanımlıyoruz.
Networks: hangi networkte olacagını belirtiyoruz.

![image](https://github.com/ibrahimdoss/Docker/blob/77a9a541f16e25c011aad3a017ba6e88771540c0/Images/Compose&Swarm/image27.png)


