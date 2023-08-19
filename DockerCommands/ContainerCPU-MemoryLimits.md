--memory=limit = bu komutta biz containerın ne kadar ram kullanmasını istersek mb,gb,kb olarak verip limitleyebiliriz.

**docker container run -d --memory=100m ozgurtozturknet/adanzyedocker(image)**

yukarıda olusturduğumuz container 100 mb ram kullanacaktır.

Bu container kullandığın ram miktarı 100 mbi gecerse o zaman swap olarka diskten belirli bir alan ayırmasını da sağlayabiliriz.

**docker container run -d --memory=100m –memory-swap=200m ozgurtozturknet/adanzyedocker(image)** 
swap alanı olusturmus olduk ve 100 mbi gecerse swapten kullanacaktır.


**Cpu tarafında limitleme icin ise ctrl+alt+del tıklayıp task manager acıyoruz orada performance tıklayıp cpuya baktığımız zaman orada cores ve logical processors vardır biz cpu üzerindeki kısıtlamayı mesela logical processors 8 ise bunun 2 sini kullan gibisinden limitleme yapabiliyoruz.**

**--cpus=”core_sayısı” = cpu da core sayısı üzerinden limitleme**

**Docker container run -d –cpus=”1.5” ozgurozturknet/adanzyedocker = dersek bu container bu sistemin icerisinde ne kadar core varsa onun sadece 1.5 I kadarını kullanacak.**

Diğer yöntem ise ;

**--cpuset-cpuıs=”core_numarası”**

**Docker container run -d –cpus=”1.5” –cpuset-cpus=”0,3” ozgurozturknet/adanzyedocker =**

Bu containerı logical processora direkt atabiliyoruz, yani 8 coren icerisindeki 1.5 katı değil de direkt 3 ve 5 coreları kullan gibisinden diyebiliyoruz. 

Yukarıdaki  komutta ise cpu 0 ve cpu 3 ü kullan demis olduk.
