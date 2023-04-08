## ADIM 1: Sistemi Güncelle

İlk adım, sistemi güncellemek ve gerekli bağımlılıkları kurmaktır: **sudo apk update** **sudo apk upgrade sudo apk add ca-certificates wget**

## ADIM 2: PostgreSQL RPM Deposu Ekleyin


Ardından, PostgreSQL RPM deposunu sisteminize ekleyin: **docker pull postgres sudo wget -O /etc/apk/keys/postgresql.asc https://www.postgresql.org/media/keys/ACCC4CF8.asc sudo sh -c 'echo "http://dl-cdn.alpinelinux.org/alpine/edge/main" >> /etc/apk/repositories' sudo sh -c 'echo "http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories' sudo sh -c 'echo "http://dl-cdn.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories'**

- Bu komut, güncel Postgres imajını indirir.


## ADIM 3: PostgreSQL'i Kurun

Artık aşağıdaki komutu kullanarak PostgreSQL'i kurabilirsiniz: **sudo apk add postgresql**
Bu komut,


## ADIM 4: PostgreSQL'i yapılandırın.

PostgreSQL'i kurduktan sonra, yeni bir veritabanı kümesi oluşturmanız ve yapılandırmanız gerekir. Veritabanını başlatmak ve PostgreSQL sunucusunu başlatmak için aşağıdaki komutları kullanın: **sudo mkdir /run/postgresql sudo chown postgres:postgres /run/postgresql sudo -u postgres initdb -D /var/lib/postgresql/13/data sudo -u postgres pg_ctl -D /var/lib/postgresql/13/data -l logfile start**

## ADIM 5: PostgreSQL'i Otomatik Başlatılacak Şekilde Yapılandırma

Varsayılan olarak PostgreSQL, açılışta otomatik olarak başlayacak şekilde ayarlanmamıştır. Bunu etkinleştirmek için aşağıdaki komutu kullanın: **sudo rc-update add postgresql**

## ADIM 6: PostgreSQL Kurulumunu Doğrulayın


Aşağıdaki komutu kullanarak PostgreSQL sunucusuna bağlanarak kurulumu doğrulayabilirsiniz: **psql -U postgres**

- -Bu komut, PostgreSQL komut istemini başlatacaktır. Artık yeni bir veritabanı oluşturabilir ve PostgreSQL'i kullanmaya başlayabilirsiniz.

-Tebrikler, RPM paket yöneticisini kullanarak Alpine Linux'ta PostgreSQL'i başarıyla kurdunuz ve yapılandırdınız.









