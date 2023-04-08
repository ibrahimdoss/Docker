Şimdi bu volume objesini bağlayacağımız bir container yaratalım. **docker container run -it -v ilkvolume:/uygulama alpine sh** komutunu incelersek; **docker container run** ile bir container yarattığımızı, **-it** komutuyla bu container'la interaktif bir bağlantı kurduğumuzu, **-v ilkvolume:/uygulama** komutuyla bu container'a ve spesifik bir klasörüne (uygulama) bir volume bağlamak istediğimizi, **alpine** komutuyla bu container'ı alpine base image'ından yaratmak istediğimizi ve **sh** komutuyla da shell açmak istediğimizi görebiliriz:

Bu şekilde container'a interaktif bir şekilde bağlanmış olduk.

NOT: Volume objesinin kullanımı hep aynı şekilde olmalıdır:

image -1


Volume objeleri hakkında bilinmesi gereken bir başka konu da, container silinse bile volume objesinin silinmeyeceğidir. Aynı volume'ü yeni bir container'a bağlasak bile içindekilerin silinmediğini görebiliriz. Yani verilerimizi bir nevi container'ın dışında, container yaşam süresinden daha uzun bir süre tutmayı başarabiliriz. Hatta aynı anda birden fazla container'da aynı volume objesini barındırabiliriz.

Şimdi **docker volume ls** komutu ile volume objelerini görüntüleyebiliriz:

image -2


Production gibi ortamlarda önemli veriler ile uğraşırken, veri saklamak için kullanacağımız tek yöntem volume'dür. Fakat container dışında veri saklamak adına **Bind Mounts** adında bir yöntem daha mevucttur. **Bind Mounts** yöntemini test ortamında veya kendi lokalimizde development yaparken kullanabiliriz.


Volume gibi bir docker objesi yaratmak yerine, **host makinedeki bir klasörü container içine map etmeye** **Bind Mount** denir. Yani container'ın verilerini aktaracağı yerin lokaldeki bir yer olması. Bu sayede verilerimizi container'dan alırken zahmete girmeyiz, hem dışarıdaki verileri container'a atarken zahmete girmeyiz, hem de container silinse bile verilerimizi lokalde saklamış oluruz.

