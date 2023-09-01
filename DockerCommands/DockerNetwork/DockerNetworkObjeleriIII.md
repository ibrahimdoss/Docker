Default olarak gelen 3 network objesi dısında docker altında bu defaultları kullanmak zorunda değiliz. Kendimiz de yeni bir network olusturabiliriz. Host ve none networkleri icin yeni bir tane olusturmamıza gerek yoktur. Bunlar zaten mevcut haliyle yetiyor.

Eğer istersek yeni bridge networkler yaratabiliyoruz.

![image](https://github.com/ibrahimdoss/Docker/blob/640dd7d2c364ff0c988867fa39fc54ee85efe19f/Images/NetworkImages/n8.png)

Neden yeni bridge network olusturmaya ihtiyac duyuyoruz ?

İlk ve en öncelikli neden olarak birden fazla container ile çalışırken daha karmaşık network topolojilerine ihtiyaç duyabiliriz. 

Örneğin yukarıda bir makine üstünde bir web bi de database container calısıyor. Bunların birbirleri ile iletisim kurması gerekiyor ama Diyelim ki aynı zaman da 5 tane daha farklı container calıstırıyoruz bunların web container ile alakası yok ama bunların hepsini default bridge networke koyarsak hepsi birbirileri ile haberlesebilecekler.

Aynı networke bağlı containerlar birbirlerine port publish etmeden haberlesebiliyorlar.

![image](https://github.com/ibrahimdoss/Docker/blob/640dd7d2c364ff0c988867fa39fc54ee85efe19f/Images/NetworkImages/n9.png)

Eğer bunu istemiyorsak ayrı ayrı containerları farklı bridge networklere bağlayarak network izolasyonu sağlayabiliriz.

![image](https://github.com/ibrahimdoss/Docker/blob/640dd7d2c364ff0c988867fa39fc54ee85efe19f/Images/NetworkImages/n10.png)

Yukarıdaki gibi db ve web containerlarına isim üzerinden erisim sağlayamayız. Ama biz bi tane bridge network olusturup bu iki containerı da buna bağlarsak bunlara bridge networkteki isim üzerinden bunlara erisebiliriz.

**Docker container run -dit –name websunucu –net kopru1 image_name**  = dit opsiyonu, containerı yarat bununla bağlantıyı kur, arka planda kur ve calısmaya devam edebilelim.  Bu ise yarıyor.

**Docker attach websunucu** = container icerisine bağlanma.

**Docker network connect kopru2 container_id ya da name**

**Docker network disconnect kopru2 database** = kopru2 üzerinden database container bağlantısını kes

**Docker network rm kopru1** = bridge silme islemi.

**Ama container bağlı iken silme islemi yapamayız. Kullanıcı tanımlı bridge silmek icin o bridge üzerinde calısan container olmaması gereklidir.**