Docker’da Tüm İmaj ve Konteynerları Kaldırma
Published on: 10/03/2018 | Last Updated on: 20/12/2018 by Mertcan GÖKGÖZ
Bu hafta kısa bir yazı ile sizlerleyim. Docker üzerinde çalışırken geliştirme ortamınızda saçma salak hatalar alıyorsanız. Uğraştınız ve çözemediyseniz. Kafanızı daha fazla yormayıp soruna neden olan bütün imaj ve konteynerları uçurabilirsiniz.
docker rm $(docker ps -a -q) && docker rmi $(docker images -q)
bu komutlar geliştirme ortamında kullandığınız tüm konteyner ve imaj yapısını ortadan kaldıracak ve size temiz bir geliştirme ortamı açmanıza imkan sağlayacaktır.
Kaldırılma işlemi sırasında aşağıdaki gibi bir hata ile karşılaşırsanız.
Error response from daemon: conflict: unable to delete 259ee57c2a34 (must be forced) - image is referenced in multiple repositories
Error response from daemon: conflict: unable to delete 259ee57c2a34 (must be forced) - image is referenced in multiple repositories
Error response from daemon: conflict: unable to delete 7721d6b4045f (cannot be forced) - image has dependent child images
Zorlama yaparak temizleme işlemini sonlandırabilirsiniz.
docker rmi $(docker images -q) --force
Her ne kadar önermesemde geliştirme ortamlarında dockerın saçmaladığı zamanlar gözü karartıp bu işlemleri yapmalısınız.
Docker Makinada hv_get_dhcp_info: not found İle Başlayan Sorun
01/06/2018 by Mertcan GÖKGÖZ
Hyper-V kullanan kurum ve kuruluşlarda kimi zaman linux ile işlem yapacaksınız. Bu esnada bilmeniz gereken en ilginç durum docker kurulumundan sonra gerçekleşmektedir. Özellikle Windows Server 2012 ve Windows Server 2012 R2 veya daha aşağısı kullanılan bir yapıda Docker kullanılmak isteniyor ise aşağıdaki logları görme ihtimaliniz yüksek, görmeme ihtimalinizde var. Üstelik docker çalıştığında yaptığı kontrollerden sonra konteynerleri yeniden başlatacak yada kapatacak sonucunda sizden yeniden başlatma isteyecek.
Loglarda karşımıza çıkan durum şu şekilde olacak tabi herşeyi kurulu olmasına karşın bu satırları kimi zaman görmeye devam edeceğiz.
May 25 19:16:43 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dhcp_info: not found
May 25 19:16:49 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dns_info: not found
May 25 19:16:49 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dhcp_info: not found
May 25 19:16:49 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dns_info: not found
May 25 19:16:49 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dhcp_info: not found
May 25 19:16:49 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dns_info: not found
May 25 19:16:49 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dhcp_info: not found
May 25 19:16:49 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dns_info: not found
May 25 19:16:49 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dhcp_info: not found
May 25 19:25:35 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dns_info: not found
May 25 19:25:35 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dhcp_info: not found
May 25 19:25:35 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dns_info: not found
May 25 19:25:35 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dhcp_info: not found
May 25 19:21:10 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dns_info: not found
May 25 19:21:10 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dhcp_info: not found
May 25 19:21:10 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dns_info: not found
May 25 19:21:10 generic-hostname hv_kvp_daemon[480]: sh: 1: hv_get_dhcp_info: not found
Bunu çözmek için Windows server 2012 ve R2 makinaya direk apt install hyperv-daemons komutunu vereceğinizi düşünüyorum. Kurulumlar tamamlandıktan sonra yukarıdaki durumun geçeceğini sanıyor olabilirsiniz. Haklsınızda lakin dockerda sıkıntı çıkmaya devam edecek.
Docker kardeşimizin çalışmasını sağlayabilmek için ilk başta Hyper-V ile sanallaştırma yapıp herhangi bir linux distro kurmayı bırakın. Direk olarak Windows Server 2016 kurulumu gerçekleştirin sistemin güncelleştirmelerini yapıp, temel sunucu kurulum prosedürünüzü izleyin.

Burada en önemli nokta Windows server 2016‘da çekirdek tabanında uzunca süre çalışılıp native bir şekilde windows container yapısının aktif edilmiş olmasıdır. Çekirdek kapsayıcı yalnızca Windows Server 2016 ile kullanılabilir. Merak etmeyin WS 2016 üzerinde docker oldukça kararlı çalışıyor. Ne bir hata ne bir sorun ile karşılaşma imkanınızda pek yok.
Desteklenen sistemler için lütfen referans olarak uygunluk matrisine bakın.

Docker’da Varsayılan Veri Klasörü Nasıl Değiştirilir?
15/07/2020 by Mertcan GÖKGÖZ
Docker’ı sisteme ilk kurduğunuzda indirilen imajlara kadar her şeyi /var/lib/docker içerisinde tutmaktadır. Başka bir yerde bu verileri depolamak istiyoruz, ben genellikle bu tarz verileri SSD üzerinde tutmam, Cold Storage üzerine alırım.
Çözümümüze gelecek olursak başlamadan önce varsayılan klasörü yani /var/lib/docker dizinini temizliyoruz.
docker system prune -a
Komutu işinizi fazlasıyla görecektir. Dizin temizlendikten sonra /etc/docker/daemon.json yoluna gidiyoruz karşınıza aşağıdaki gibi bir yapılandırma dosyası çıkacak.
{
 "authorization-plugins": [],
 "dns": [],
 "dns-opts": [],
 "dns-search": [],
 "exec-opts": [],
 "exec-root": "",
 "experimental": false,
 "storage-driver": "",
 "storage-opts": [],
 "labels": [],
 "live-restore": true,
 "log-driver": "",
 "log-opts": {},
 "mtu": 0,
 "pidfile": "",
 "graph": "",
 "cluster-store": "",
 "cluster-store-opts": {},
 "cluster-advertise": "",
 "max-concurrent-downloads": 3,
 "max-concurrent-uploads": 5,
 "shutdown-timeout": 15,
 "debug": true,
 "hosts": [],
 "log-level": "",
 "tls": true,
 "tlsverify": true,
 "tlscacert": "",
 "tlscert": "",
 "tlskey": "",
 "swarm-default-advertise-addr": "",
 "api-cors-header": "",
 "selinux-enabled": false,
 "userns-remap": "",
 "group": "",
 "cgroup-parent": "",
 "default-ulimits": {},
 "init": false,
 "init-path": "/usr/libexec/docker-init",
 "ipv6": false,
 "iptables": false,
 "ip-forward": false,
 "ip-masq": false,
 "userland-proxy": false,
 "userland-proxy-path": "/usr/libexec/docker-proxy",
 "ip": "0.0.0.0",
 "bridge": "",
 "bip": "",
 "fixed-cidr": "",
 "fixed-cidr-v6": "",
 "default-gateway": "",
 "default-gateway-v6": "",
 "icc": false,
 "raw-logs": false,
 "registry-mirrors": [],
 "seccomp-profile": "",
 "insecure-registries": [],
 "disable-legacy-registry": false,
 "default-runtime": "runc",
 "oom-score-adjust": -500,
 "runtimes": {
  "runc": {
   "path": "runc"
  },
  "custom": {
   "path": "/usr/local/bin/my-runc-replacement",
   "runtimeArgs": [
    "--debug"
   ]
  }
 }
}
Yapılandırma dosyasının içerisinde şu değişikliği yapıyoruz ve kayıt ediyoruz.
"data-root": "/disk1/data/docker_datum",
"storage-driver": "overlay2"
bu işlemin ardından systemctl restart docker komutu ile yeniden başlatıktan sonra gereken docker dosyalarını yeni yerinde bulabilirsiniz. Bu sayede ana diskiniz dolmadan işlemleri yapabilirsiniz.

Docker Container Log Dosyalarının Boyutu Nasıl Küçültülür?
22/09/2020 by Mertcan GÖKGÖZ
Yanlış yapılandırılan her docker konteyneri dışarıya yüklü miktarda log basar, disk alanı az olan sunucularda sistem yöneticileri güneşi hızlı bir şekilde görebilir ve servis kesintileri yaşayabilir.
Aşağıda yapacaklarımızdan hemen önce lütfen docker-compose dosyanız üzerinde gerekli olan ince ayarları yapınız, aksi taktirde yapacağınız bu işlemlerin log dosyalarının boyutunu düşürmede bir etkisi olmayacaktır.
logging:
      driver: "json-file"
      options:
        max-size: "1g"
        max-file: "10"
Bir müşteride mevcut logların boyutunu şu şekilde gördüm, burada anladığım kadarıyla 2 konteyner aktif olarak kullanılmış ve üzerinde ciddi anlamda işlem yapılmış ve log üretilmiş.
-rw-r----- 1 root root 40,2M 2020-08-20  /var/lib/docker/containers/cff872f1769dfed9c36d5f7e61627d2ff77973441325b07847fb4874ef1a0acf/cff872f1769dfed9c36d5f7e61627d2ff77973441325b07847fb4874ef1a0acf-json.log
-rw-r----- 1 root root 8,2M 2020-08-20  /var/lib/docker/containers/02a78f490f6b7ace252f3126689cf9200f488e94b909b9a2e5ee29613a1ee305/02a78f490f6b7ace252f3126689cf9200f488e94b909b9a2e5ee29613a1ee305-json.log
-rw-r----- 1 root root 3,3M 06-10 11:19 /var/lib/docker/containers/4cb9f353b394287dff456c1ce08d13c1a3206ad902e44eb5a5f3cd33e747320c/4cb9f353b394287dff456c1ce08d13c1a3206ad902e44eb5a5f3cd33e747320c-json.log
-rw-r----- 1 root root 578G 09-22 10:12 /var/lib/docker/containers/7e1bb748c785343f47511e08cb10aa676df09d4fc4abe1f371bc7b49a3d88b9d/7e1bb748c785343f47511e08cb10aa676df09d4fc4abe1f371bc7b49a3d88b9d-json.log
Bu loga ulaşmak için şu komutu kullandım
docker ps -aq | xargs -I'{}' docker inspect --format='{{.LogPath}}' '{}' | xargs ls -lh
Müşteri bana logların önemli olabilecek verileri uzak storageda tutabileceğini ve gerektiği kadarını silmemi (bence saçma, bir işine yaramaz bu log ama neyse)
cat /var/lib/docker/containers/*-json.log | bzip2 --best --compress --stdout > /mnt/nfs-storage-shared/2020-09-22.log.bz2
Ardından log dosyasını bölmem ve çoğunu kesmem gerektiği için apt install util-linux kurulumu yaptım(ilginç şekilde yüklü değildi), ardından fallocate ile dosyayı bölme işlemine geçiş yaptım ve aşağıdaki gibi büyük çoğunluğunu uçurdum.
fallocate --collapse-range --offset 0 --length 577GiB --verbose /var/lib/docker/containers/7e1bb748c785343f47511e08cb10aa676df09d4fc4abe1f371bc7b49a3d88b9d/7e1bb748c785343f47511e08cb10aa676df09d4fc4abe1f371bc7b49a3d88b9d-json.log
Böylelikle dosyada 1 GB‘lik kısmı bıraktım, ancak ben bunu yapıncaya kadar sistemde yapılan işlemler sebebiyle +4 GB kadar daha log birikmişti. Docker ile ilgilenen arkadaşa ilettim konuyu(ancak çözmemiş)
Otomatik log rotasyonu aktif edildiği taktirde bu makalede anlatılan çözümü yapmanıza gerek yok.
Docker-compose Kullanarak Mevcut Docker Imajları Nasıl Güncellenir?
Published on: 01/08/2021 | Last Updated on: 16/01/2022 by Mertcan GÖKGÖZ
Birden fazla geliştirme ortamı kullandığımız ve imajların güncelliğini yitirdiği senaryolar olabiliyor, mevcut bir konteyneri silmek istemeyebiliriz. Kullanılan bu konteyner production ortamında çalışıyor ve üzerinde işlem yapılıyor olabilir.
Docker kardeşimizde imajlar geçici olacak şekilde tasarlanmıştır. Yani mevcut bir imajı güncellemek için eskisini mecbur kaldırır ve yenisini başlatırsınız.
Bu işlemi yapmak için aşağıdaki prosedürü izlemeniz yeterlidir.
docker-compose pull
docker-compose up -d --remove-orphans
docker image prune -f
Bir imajın indirilmesinin başarısız olacağı senaryolar olabilir, kesintilerin sizin için önemli olacağı senaryolar olabilir. Bu sebeple tekrar imajı composer üzerinden pull etmeden ayağa kaldırma komutumuzu vermiyoruz. Güncel imajı indirmek ve bunun üzerinden tekrar konteyner ayağa kaldırmak bizim için önemli.

Kullanılan Özel Container Registrylerin Watchtower ile Güncellenmesi
26/02/2022 by Mertcan GÖKGÖZ
Bazı şeyleri otomatize ederken oto deployun yanı sıra otomatik güncelleme yapmakta önemli, bunun için rsync veya ssh üzerinden güncelleme yapmak yerine direk olarak docker containerı güncelleyebilirsiniz.
Bu işlem için ise direk olarak docker container build etmemiz bizim için yeterli, uygulamamız bunun içerisinde çalışacak ve watchtower bunu otomatik güncelleyecek.
İmaj oluşturmak için .gitlab-ci.yml için aşağıdaki yapılandırmayı kullanabilirsiniz.
image: docker:latest

docker-build:
  stage: build

  before_script:
    - docker info
    - docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD" "$CI_REGISTRY"

  variables:
    DOCKER_DRIVER: overlay2
    DOCKER_TLS_CERTDIR: "/certs"
    IMAGE_TAG: $CI_REGISTRY_IMAGE:latest

  script:
    - docker build -t "$IMAGE_TAG" .
    - docker push "$IMAGE_TAG"
Bu yapılandırma direk olarak mastera gönderilen her kodu container haline getirecek ve gitlab “container registry” içerisine basacak. Burada çift branch kullanmanızı öneririm. dev ve master olarak yoksa otomatik güncellemede sorunlarla karşılaşabilirsiniz.
Dockerfile yapılandırmamız ise aşağıdaki gibi, NodeJS uygulamamız çalışıyor siz kendinize göre güzel bir yapılandırma uygulayın.
FROM node:17

RUN set -eux; \
  npm install -g pm2

COPY app .

RUN npm install

CMD ["pm2-runtime", "index.js"]
İşlemler tamamlandığında imajımız gitlab’da duracak, isterseniz bu imajı docker hub üzerinede gönderebilirsiniz, karar size kalmış. Gitlab kullandığımız için biz başka bir alanda barındırmak istemedik.
Otomatik güncelleştirme kısmına geldik aşağıdaki gibi bir docker-compose.yml dosyası işimizi fazlasıyla görecek
version: "3.7"
services:
  monit:
    image: developer-core-team/monitoring_v01
    container_name: core_monitoring
    restart: always
  watchtower:
    image: containrrr/watchtower
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - /root/.docker/config.json:/config.json
    command: --interval 30
Yapılandırmayı kendinize göre özelleştirmekte özgürsünüz 30 saniyede bir container registrymiz kontrol edilecek varsa güncelleme alınacak, isterseniz bu süreyi arttırabilirsiniz.
•	https://github.com/containrrr/watchtower






Docker Notlarım

Docker CLI ve Docker Compose ile ilgili sıkça kullandığım komutlar yer almaktadır. bu komutları terminal aracınıza kaydedip snippet olarak kullanabilirsiniz. Termius ve xShell üzerinde işlemlerinizi yapabilirsiniz.
Docker CLI
docker build -t name .
docker run -p 8080:80 name 
docker run -d -p 8080:80 name 
docker exec -it [id] bash
docker ps 
docker stop <id>
docker ps -a
docker kill <id>
docker rm <id>
docker rm $(docker ps -a -q)
docker images -a
docker rmi <image-name>
docker rmi $(docker images -q)
docker logs <id> -f
docker login
docker tag <image> repository:tag
docker push repository:tag
docker run repository:tag

docker system prune
docker system prune -a
docker volume prune
docker network prune

docker service create <options> <image> <command>
docker service inspect --pretty <service> 
docker service ls 
docker service ps
docker service scale <service>=<replica>
docker service update <options> <service>

docker stack ls
docker stack deploy -c <compose-file> <app-name>
docker stack services <app-name>
docker stack ps <app-name>
docker stack rm <app-name>
Docker Compose
docker-compose up 
docker-compose up -d
docker-compose down
docker-compose logs
docker-compose restart
docker-compose pull
docker-compose build
docker-compose config
docker-compose scale <servicename>=<replica>
docker-compose top
docker-compose run -rm -p 2022:22 web bash

