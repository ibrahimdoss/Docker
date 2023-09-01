Docker-compose up = compose calıstırır.
Docker compose cli komutlarını sadece docker-compose.yml klasörün olduğu dizinde olduğumuz sürece calıstırabiliriz.
Bunu yapmazsak asagıdaki gibi 

![alt text](https://github.com/ibrahimdoss/Docker/blob/5a0c6ce2421084dd303bec711b3ac4228e64c177/Images/Compose&Swarm/image-30.png)

Hata verir.
Docker-compose down = durdurur.
Docker-compose = komutları ve kullanabileceğimiz opsiyonları verir.
Docker-compose config = kullandığımız yml dosyasını ekranda listeler. Aynı zamanda hangi sırada işlem yaptığını da gösterir.
Docker-compose images = olusturulan servislerin hangi imagelarla olusturduğunu listeler.
Docker-compose logs = ayakta olan servislerin loglarını görürüz.
Docker-compose exec = compose ile olusturduğumuz servis icinde komut calıstırabiliriz.A
Docker-compose ps = ayakta olan servisleri listeler.
Docker-compose top = ayakta olan servislerin içindeki processleri listeler.
Docker-compose pause = ayakta olan servisleri durdurur.
Docker-compose unpause = durdurulan servisleri tekrar başlatır.
Docker-compose rm = ayakta olmayan servisleri siler.
Docker-compose start = durdurulan servisleri başlatır.
Docker-compose stop = ayakta olan servisleri durdurur.
Docker-compose restart = ayakta olan servisleri yeniden başlatır.
Docker-compose kill = ayakta olan servisleri kapatır.
Docker-compose build = docker-compose.yml dosyasını kullanarak image olusturur.
Docker-compose pull = docker-compose.yml dosyasını kullanarak image çeker.
Docker-compose push = docker-compose.yml dosyasını kullanarak image pushlar.
Docker-compose create = docker-compose.yml dosyasını kullanarak servis olusturur.
Docker-compose down = docker-compose.yml dosyasını kullanarak servisleri durdurur.
Docker-compose events = docker-compose.yml dosyasını kullanarak servislerin eventlerini listeler.
Docker-compose port = docker-compose.yml dosyasını kullanarak servislerin portlarını listeler.
Docker-compose pause = docker-compose.yml dosyasını kullanarak servisleri durdurur.
Docker-compose unpause = docker-compose.yml dosyasını kullanarak servisleri tekrar başlatır.
Docker-compose scale = docker-compose.yml dosyasını kullanarak servisleri scale eder.
Docker-compose start = docker-compose.yml dosyasını kullanarak servisleri başlatır.
Docker-compose stop = docker-compose.yml dosyasını kullanarak servisleri durdurur.
Docker-compose restart = docker-compose.yml dosyasını kullanarak servisleri yeniden başlatır.

![alt text](https://github.com/ibrahimdoss/Docker/blob/5a0c6ce2421084dd303bec711b3ac4228e64c177/Images/Compose&Swarm/image-31.png)

Burada servis dediğimiz aslında container diyebiliriz. 1 servis = 1 container
Docker-compose down dediğimiz de direkt silmiyor sadece durduruyor.



