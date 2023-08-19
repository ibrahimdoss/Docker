![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/d2.png)

Linux sistemlerde uygulama calıstırdıklarında bu uygulamalara giris-cıkıs,

Standart Input(stdin), Standart Output(stdout) Standart Error (stderr) bu üc akıs ile sağlanır.

Terminal uygulamasının bizimle iletisim kurması icin temel giris-cıkıs akısı.

Stdin, giris akısı.

Stdout uygulamanın genel cıkısı,

Stderr genellikle hata mesajı göndermek icin kullanılır.

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/d3.png)

![image](https://github.com/ibrahimdoss/Docker/blob/main/Images/d4.png)

Yukarıda docker logs container_name or _id verilince logları listeler.

İkinci görselde en altta ise logların direkt değil de bir log dosyası üzerinden bize sunulduğunu buradaki örnekte nginx’in loglar icin yaptığı islemler gözükmektedir.

En altta loglar icin 2 tane file acıp stdout ve stderr leri buna maplemisler.

