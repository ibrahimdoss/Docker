# Container ve Sanal Makine (VM) Farkı

![Container](https://github.com/ibrahimdoss/Docker/blob/main/Images/vm.png)


Sürece baktığımız zaman ilk başta fiziksel sunucu alınır ve onların üzerine işletim sistemleri kurulur bu sekilde kullanılır.

Bare-Metal olarak adlandırılan bu durumda en büyük sıkıntı her yeni uygulamada fiziksel olarak sunucuyu temin etme sıkıntısı.

Daha sonra VM dediğimiz sanal makineler giriş yaptı. Bu sefer de Fiziksel sunucunun üzerine sanallastırma katmanı kurduk, ardından bu makinenin icine kapasitesi oranında sanal makineler olusturup, işletim sistemlerine de bu VM’leri kuruldu.

Genel bakacak olursa VM kısmına kadar önceden 10 tane app’I 10 tane fiziksel sunucu da yönetirken, VM’ döneminde 2 tane fiziksel sunucuda 10 ayrı app kullanabilir duruma geldi.

**Bu fiziksel makine bazında tasarruf sağladı ama 10 tane ayrı işletim sistemi yönetmek zorunda kaldık.**

**Container**

Containerlar döneminde ise artık tek bir fiziksel makine üstünde tek bir işletim sistemi içerisinde 10 tane container olusturarak yapmak istediğimiz işi yapabiliyoruz.

## VM-CONTAINER FARKI

**En önemli farkı container icerisinde bir isletim sistemi çekirdeğine ihtiyaç duymadığımız icin ortamda yönetmemiz gereken, ve kaynak tüketen onlarsa isletim sistemi bulunmaz**

![Container](https://github.com/ibrahimdoss/Docker/blob/main/Images/vm-2.png)