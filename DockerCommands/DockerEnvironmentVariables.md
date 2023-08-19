Environment Variables : Env bu dokumanda kısaltması bu sekilde olacaktır.

**Env** : container ortamında image yaratılırken ya da container yaratılırken tanımlanan değerlerdir.

Container ortamında iki sekilde olusturuluyor;

**--env Variable= degeri**

**-e variable = degeri**

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/a5.png)

Yukarıda örnek ile olusturabiliyoruz. 

**Urgent**: env olustururken variables büyük kücük harf duyarlılığı var yani VAR1, var1, Var1 bunların ücü de farklıdır aynı değil olustururken buna da dikkat etmek lazım. (**case sentetive**)

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/a6.png)

Linuxta env görmek icin **printenv** kullanılır.

Env görmek icin ise echo **VAR1** diyebiliriz.

File üzerinden de ulasabiliriz.
