Docker container run –name ilkcontainer ibrahimdoss/app1

Yukarıda –name yanında yazdığımız sey ile containere isim veriyoruz.

Docker container ls = o sistemde çalışan tüm containerları gösterir.

Docker container ls -a = sistemde çalışan ve durdurulmuş tüm containerları listeler.

Docker ps = calısan containerları gösterir.

Docker container logs  “container id” = burada container objesinin loglarına bakabiliriz.

**Her container imajında, o imajdan bir container yarattığımız zaman varsayılan olarak çalışması için ayarlanmış bir uygulama vardır.**

**Bu uygulama çalıştığı sürece container ayakta kalır.**

**Uygulama çalışmayı bıraktığında container da kapatılır.**

**Docker imajlarında sadece tek bir uygulama mı vardır?**

-> Hayır, Docker imajında birden fazla uygulama olabilir. Sadece tek bir uygulama içermesi kural değildir.

**Docker imajlarından container yaratıldığında çalışması için birden fazla uygulama atabilir mi?**

-> Hayır, Docker container başlatıldığı zaman otomatik çalışması için tek bir uygulamanın ayarlanmasına izin verir.

**Docker container içerisinde sadece tek bir uygulama mı çalıştırılabilir?**

-> Hayır, Docker container başlatıldığı zaman otomatik çalışması için tek bir uygulamanın ayarlanmasına izin verir fakat container içerisinde daha sonra bu uygulamanın yanında başka uygulamalar da çalıştırılabilir.

**Docker image’ında varsayılan olarak çalıştırılması için ayarlanan uygulama yerine başka uygulama ile container başlatabiliyor muyuz?**

-> Evet, container yaratılırken hangi uygulamayı çalıştırmasını istediğimizi belirtebiliriz.

**Çalışan bir containerı sistemden silinemez.**

**Önce stop edilir ardından silinir.**

**Container çalıştırdıktan sonra içine ayrıyaten şunu yap vs gibi işlemler yapamayız. Bu islemler image asamasında gerceklestirilir ve image olarak paketlenir.**

**Container o imajdan yaratılmıs calısan bir kopyadır. İdeal olarak tek bir uygulama çalıştırılması için hazırlanır. Container çalıştırıldığı zaman o uygulama çalışır, uygulama çalıştıkca container çalışmaya devam eder.**

**Ideal olan container hangi uygulama çalışması icin ayarlanmıssa onunla ilgili her türlü ayarların imaj aşamasında halledilmesi lazım.**

**Docker containerın icerisine bağlanarak degisiklik yapmasına izin verir.**

**Bunu da o container imaj icerisinde bağlanabileceğimiz bir shell olmasıdır ki çok kücük ve spesifik ve bazı imajlar dısında hepsinde bir shell mevcuttur.**

**Örnek bir container olusturma = docker container run --name websunucu -p 80:80 -d ozgurozturknet/adanzyedocker**

**Çalışan containere docker container exec komutuyla bağlanıyoruz.**

**docker container exec -it websunucu sh**

**yukarıdaki komutta exec ile containere bağlandık. Sonra nerede uygula kısmına olusturduğumuz containerın adını yazıyoruz. Neyi uygula kısmına sh komutunu uygula demis oluyoruz. Sh = shell demek.**

Yani kısaca bu container icerisinde shell calıstır demis oluyoruz.

-it ise (--interactive ve –tty) opsiyonlarının birlesimidir. Yani bu containera interactive modda bağlan, kısaca komutlarımı bu container icerisinde calıstır, ve bunu sağlamak amacıyla sözde bir terminal bağlantısı kur demek. Bu ikisini birlestirip -it olarak giriyoruz.

Bağlandıktan sonra bize direkt mevcut konumdaki dosyayı acar.

Oraya da ls -l dersek hangi dosyalar varmıs ona bakabiliriz.

**Calıstıgını da görmek icin browsera 127.0.0.1 hostunu girip bakabiliriz. Diğerleri icin de gecerli.**

![image-20210703170849654](https://github.com/ibrahimdoss/Docker/blob/main/Images/vm-3.png)

Yukarıda islemlerin komuttaki gösterimi belirtilmistir.

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/vm-4.png)

Yukarıda en son cıktımız bu sekilde.

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/vm5.png)

**Yukarıda editleme islemi yapıyoruz. Ve bir yazı yazıyoruz.**

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/vm6.png)

**Yukarıda editleme yapıldıktan sonra degisiklik gösterilmis oldugunu görüyoruz.**

Containerın ilk uygulaması durursa container da durur

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/vm7.png)

**Yukarıda ps ile container ile calısan uygulamalara baktık. Birden fazla uygulama calısıyor ama ilk baslama esnasında sadece bir tanesini calıstırabiliriz.**

**Kill 1 ile PID 1 olanı stoplarsak , uygulama ve dolayısıyla container stop olur.**

**Daha sonra start diyerek tekrar calıstırabiliriz, rm ile silmediğimiz sürece stop ettiğimiz containerları tekrar calıstırabiliriz.**

**Not : Aynı image kullanıp birden fazla container calıstırabiliriz ve bunların tamamı birbirinden bağımsız, ayrı containerlardır.**

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/vm8.png)

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/vm9.png)

**Not yazısındaki islemler yukarıda belirtilmistir. Cıktıya baktığımız da eklediğimiz yazı burada gözükmüyor cünkü image aynı olsa da olusturulan containerlar birbirinden bağımsızdır.**