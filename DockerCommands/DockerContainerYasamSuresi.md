
![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/a1.png)

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/a2.png)

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/a3.png)

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/a4.png)

Case : Hesaplama adında bi uygulamamız olduğunu varsayalım sürekli hesaplama yapıyor ve onları hesaplama.log adı altında topluyor ve dosya sürekli büyüyor.

Bu uygulamayı ozgurozturknet/hesaplama adı altında bir image olusturduk ve bundan bir container olusturduk.

Diyelim uygulamada sorun cıktı containerı kapattık, yeni bir container actık ama kayıtlar yok.

Bir önceki kayıtlar container1’n RW layer katmanında tutuluyor container2 de haliyle oraya erisim sağlayamaz.

**Containerlar tek kullanımlıktır.**

**Bu durum eğer uygulama kayıtlarını harici db lerde tutulmuyorsa sıkıntı olabilir.**

**Bu ve benzeri durumları engellemek adına, container yasam süresinden daha uzun tutmamız gereken veriler varsa bunları container icerisinde tutmayız.**

**Bunları container dısına alıp, orada saklamamız lazım ve her yeni container paylasılabilir ve erisilebilir yapılması lazım.**

**Docker tarafında bunun cözümü volume’lerdir.**
