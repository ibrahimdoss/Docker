## docker container run hello-world

- docker container run hello-world -> komutu hello-world isimli image ile yeni container oluşturur ve başlatır. Docker Daemon, Image' ın localde olup olmadığını kontrol eder. Image localde yer alıyorsa bu image'ı kullanarak yeni bir container oluşturur. Eğer image lokalde yoksa varsayılan kayıt defteri olan hub.docker.com adresinde hello-world isimli image'ı sorgular. Burada image yer alıyorsa image'ı locale indirir ve bu image'ı baz alarak yeni bir container oluşturur ve çalıştırır. Böylece servis ayağa kalkmış olur:





