
![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/a7.png)

Docker depolama alt yapısında UnionFS (Union File System, Birlesim dosya sistemi ) kullanır.

Docker imageları mevcut bir base image üzerine insa edilir. Bu image üzerine yapılacak her degisiklik sırayla birer katman olarak eklenir. Bunlar da ayrı birer dosya olarak depolanır.

Daha sonra UnionFS sayesinde bu katmanların her biri tek bir dosya seklinde görmemiz icin ayarlanır ve biz alısık olduğumuz sekilde normal bir dosya görürürz.

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/a8.png)

Yukarıda gözüktüğü gibi sistem katmanların sırası asagıdan  yukarıya 1,2,3.katman olarak ilerler. Mesela burada java dosyası olsaydı onun icin JRE indirmemiz lazımdı o da ayrı bir katman olarak tutulurdu, katmanların sayısı eklenen uygulamaya göre degisir.

**En üstteki hello-app’a image tag diyoruz.**

**Docker image kısaca  bir temel linux isletim sistemini alıp, üstüne yaptığımız her bir degisikliği ayrı bit katman olarak alıp ve tutulduğu en sonunda bu katmanların tek bir bütün gibi calısmasının sağlandığı bir docker objesi**

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/a9.png)

Docker image Read-only tutuyor.

Üstüne bir katman daha ekliyor.

**Ona da Container Yazılabilir Katman (R/W Layer) diyoruz.**

**Her container icin bir adet yazılabilir katman olusturuluyor.**

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/a10.png)

Diğer tüm dosyalar 1.katman olan base imajda duruyor.

Bunların her birinin ayrı ayrı katmanlar olarak saklanmasına rağmen hepsini bir arada görmemizi UnionFS sağlıyor.

Bir image’dan container olusturduğumuz zaman bu containerda yaptığımız her islem bu yazılabilir layerda saklanıyor.

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/a11.png)

Eğer katmanlarda bir degisiklik yapacaksak yukarıdaki örnekte var dosyasının yanına abc.txt ekledik, container bunu alıyor R/W layet katmanına kopyalıyor, asıl olanı gizliyor. Aartık degisikliği R/W layer katmanda yapmak mümkün oluyor.

İmage’daki dosyaya dokunmuyor.

**Docker container prune** = bu sistemde çalışmayan tüm containerları sistemden temizler.
