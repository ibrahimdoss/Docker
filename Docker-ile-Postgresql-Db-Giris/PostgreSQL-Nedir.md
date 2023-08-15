PostgreSQL ya da Postgres, özgür ve açık kaynak kodlu, SQL destekli bir nesne ilişkisel veritabanı yönetim sistemidir.SQL dilinin güvenlik, depolanabilirlik ve ölçeklendirilebilme özelliklerinden faydalanan PostgreSQL, birçok alanda kullanılmaktadır. Buradaki hiyerarşik yapı genelden özele gidecek olursak, sunucu > veritabanı > şema > tablo şeklindedir.

## Veritabanlarını Yönetme

### Veritabanı Oluşturma ve Görüntüleme

**create database test-db;**

image-1


Var olan veritabanlarını görüntülemek için iki farklı komut kullanabiliriz. Bunlardan ilki sistem view'ı olan pg_database tablosundan select çekmek olabilir. İkicisi olarak ise **\l** ' yi kullanabiliriz. Postgresql'in kısa yollarından biridir. Detaylı kısa yollar için **\?** ile tüm komutları bulabilirsiniz. **SELECT datname FROM pg_database;**

image 2


## TEMPLATE OLUSTURMA

Biraz da template database kavramı üzerinde duralım. Bir veritabanını default ayarları dışında oluşturmak ve bunun devamlılığını sağlamak istersek bunun için yeni bir **TEMPLATE** oluşturmamız gerekir. Oluşturmak istediğiniz standardı tasarladıktan sonra template1 **template_ismi** şeklinde yeni bir template oluşturabiliriz. Ve bu template ile veritabanlarımızı istediğimiz standartlarda oluşturabiliriz. Default olarak bir postgresql kurduğunuzda 2 farklı template görürsünüz. Bunlardan template0'da değişiklik yapılamaz. Her oluşturduğunuz veritabanı aslında bu **template0** standardı ile kurulur. Bu nedenle değiştirilemez. Fakat yeni bir standarta ihtiyacınız varsa, template1 şablonunda gerekli değişikleri yapıp, yeni veritabanları bu şablonu kullanarak oluşturabilirsiniz. Örnek olarak; Veritabanı oluşturabilmeniz için ya öncelikli bir kullanıcı olmalısınız ya da **CREATEDB** yetkisine sahip bir kullanıcınız olmalı.

Öncelikle template1'e **\c template1** (connect anlamına gelir) diyerek bağlanıp bu template'te bir tablo oluşturalım.

image-1

Daha sonra bu template'ten bir veritabanı oluşturup, oluşturduğumuz veritabanına bağlanarak **\dt** (description table) komutu ile tablonun otomatik bu veritabanında oluştuğunu görelim.

image -2


## Schema (Şema) Oluşturma

Schema veritabanındaki tablo, view ve stored procedure gibi objeleri gruplamaya yarar. Bir objeyi bir şema altında yaratabilirsiniz veya bir şemanın altına transfer edebilirsiniz. Ayrıca şema bazlı yetki de verebilirsiniz. Yani user sadece izin verdiginiz şemanın altındaki objeleri görebilir diğerleri göremez. Normalde obje sayılarının fazlalığı yönetimi ve izinlerini oldukça zorlaştıracaktır. Her bir objeyi tek tek yetkilendirmek yerine şema bazında yetkilendirme yapmak daha uygun olacaktır. Postgresql default olarak oluşturduğunuz her objeyi, şema belirtmediğiniz sürece public şeması altında oluşturur.

Bir şema oluşturmak için aşağıdaki komutu kullanabiliriz. Aşağıdaki komut dizisine göre; bayi1 isimli bir şema yaratıldı ve arabalar veritabanında markalar isimli bir tablo oluşturularak bu şemaya eklendi. Böylece hem public hemde bayi1 şemasında markalar isminde 2 farklı tablomuz olmuş oldu.

image -3

## Yetkilendirme


Öncelikle veritabanımızda sinem isimli bir kullanıcı oluşturalım, yeni kullanıcıları postgres gibi yetkisi olan bir kullanıcıyla oluşturabiliriz. **\q** komutunu quit anlamına gelir veritabanından çıkmak için kullanabiliriz. Veritabanına önceden postgres ile bağlıydık, çıkış yaptıktan sonra artık sinem kullanıcısıyla giriş yapabilmek için, psql komutunda **-U (username), -d (dbname), -h (hostname/ip)** parametrelerini kullanmamız gerekiyor.

image -4

Yukarıdaki çıktıda gördüğümüz gibi bize **'ERROR: permission denied for table araba'** hatası veriyor. Çünkü arabalar veritabanında, sinem kullanıcısının **SELECT** yetkisi bulunmuyor. Şimdi **GRANT** ile sinem kullanıcısına, arabalar veritabanındaki markalar tablosu için **SELECT** ve bayi1 şeması için **USAGE** yetkisi verelim. Ardından sorguyu tekrardan çalıştıralım.


Yetki verme işlemini postgres veya yetkili başka bir kullanıcı ile yapmanız gerekmektedir. Ve yetkiyi vereceğiniz ilgili veritabanına bağlı olmalısınız. Aşağıdaki örnekte arabalar veritabanına postgres kullanıcısı ile yeniden bağlanılmıştır. (Linux shell'de yeniden psql diyerek bağlanabilir ve \c arabalar diyerek veritabanına geçebilirsiniz.)

image -5


## OWNER Yapma

postgres kullanıcısına geçerek sinem kullanıcısnı arabalar veritabanının sahibi yapalım.

image -6

## TABLESPACE

Tablespace verilerin aslında fiziksel olarak saklandığı yerdir. Bizim aynı veritabanı içerisindeki farklı verileri, farklı disklerde saklama ihtiyacımız varsa yeni bir tablespace oluşturabiliriz. Örneğin bazı tablolarda performans ihtiyacınız olduysa veya genelde veritabanı yöneticileri indexlerin performansını arttırmak için sunucuya yeni ve hızlı bir disk ekleyip tablespace oluşturarak tabloları veya indeksleri bu alanda tutar. Ve bu şekilde verileri farklı lokasyonlarda, disklerde tutmuş olur.

Postgresql'de default olarak 2 alan vardır.

- pg_default : Template1 ve template0 şablonlarının varsayılan tablo alanıdır.
- pg_global : Metadata verisinin tutulduğu yerdir. Paylaşımlı sistem katalog verileri saklanır.

Şimdi farklı bir tablespace oluşturmak için öncelikle kendimize ait bir lokasyonda klasör oluşturmamız gerekiyor. Bizim burada örneğin /data2 diye farklı bir diskimiz sunucu üzerinde mevcut. (Siz linux shell'de mkdir -p /data2 diyerek yeni bir path oluşturabilirsiniz.)

Daha sonra **hizlialan** adında bir **TABLESPACE** oluşturuyoruz. Aşağıdaki select sorgusuyla 3 farklı tablespace olduğunu görebilirsiniz.

image-7

Tablespace oluşturduktan sonra hizlialan içerisinde personel isimli bir tablo oluşturalım.

image -8


Aşağıdaki komut ile veritabanındaki tablolar hakkında detaylı bilgi alabiliriz. Bu örnekte personel tablosunun tablespace kısmının default olmadığını hizlialan olduğunu görebilirsiniz.

image-9