Docker'da container üzerinde yapacağımız işlemlere geçmeden önce, önemli bir kaç komuta bakalım. Öncelikle docker container run komutu, docker container create ve docker container start komutunun birleşimidir.

Her image'da, o image'dan bir container create ettiğimiz zaman default çalışması için ayarlanmış bir uygulama vardır. Container, bu uygulama çalıştığı sürece ayakta kalır. Uygulama çalışmayı bıraktığında container da kapatılır.

Peki image'ın içinde sadece tek bir uygulama mı var? Hayır bir Docker image'ının içinde birden fazla uygulama olabilir. Sadece tek bir uygulama içermelidir gibi bir kural yok. Fakat Docker, container start edildiğinde default çalışması için yalnız tek bir uygulamanın ayarlanmasına izin verir. Bunun hangi uygulama olacağını container yaratılırken belirtebiliriz.

