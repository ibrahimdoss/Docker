Docker, açık kaynak bir Container motorudur. Daha iyi anlamak için mimarisini ve bileşenlerini inceleyelim:

![Names](DockerCommands/CommandImages/docker-infra.png)

- Docker Client, docker komutlarını çalıştırdığınız komut satırı arayüzü aracıdır. Gelen talepleri Docker API üzerinden Docker Daemon' a iletir.

- Docker Host üzerinde Docker Daemon çalışmaktadır.

- Docker Daemon, API üzerinden gelen istekleri dinlemekte ve gerçekleştirmektedir. Tüm container süreçleri burada yönetilir.

- Docker Registry ise açık kaynaklı olarak image' larınızı yükleyebileceğiniz ve DockerHub' da paylaşabileceğiniz bir kayıt defteri aracıdır. Docker içerisinde çalıştırabileceğiniz image' lar burada saklanır. DockerHub, docker tarafından hizmet veren herkesin kullanımına açık public bir kayıt defteridir.

- Docker Image, container oluştururken kullandığımız template'lerdir. Çalışacak uygulamanızın ve uygulamanızın altyapısında çalışan gerekli işletim sistemi kütüphanelerinin bulunduğu bir yapıdır. Container' ların yeteneklerini ve ihtiaçlarını tanımlayan metadata verilerini de saklamaktadır.

- Docker Container, docker image' lardan oluşturulan uygulamalardır. Docker Image'ın çalışan bir örneğidir. Uygulamayı çalıştırmak için gereken tüm paketleri containerlar bünyesinde tutmaktadır. Image bir şablondur ve containerlar da bu şablonun çalışan bir kopyasıdır.

