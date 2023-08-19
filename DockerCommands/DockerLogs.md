**docker logs --details con1(con1 = container name) = daha detaylı logları görmek istersek.**

**docker logs -t con1 (con1 = container name) = logları zaman ile görmek istersek bunu kullanırız.**

**docker logs --until 2022-08-02T19:20:32.774309365Z con1 = Belirli bir zamandan sonra ki logları görmek istersek** burada verdiğimiz zamana kadar ki logları gösterir. Yani 20:32 ye kadar ki logları verir.

**docker logs --since 2022-08-02T19:20:32.774309365Z con1** = bu da belirli bir zamandan sonraki logları gösterir ise yarıyor. Yani 20:32 den sonraki logları gösterir.

**docker logs --tail 3 con1** = burada ise son 3 kayıtı görmek istersek –tail ile bunu sağlıyoruz. –tail den sonraki sayı son kac satır logu görmek istediğimiz sayıyı belirtir.

**docker logs -f con1** = bu ise canlıda olusan logları gösterir. Yani nginx de her islemde loglar anlık buraya atılır terminalden cıkmaz bunu yapınca. -f = follow yani logları takip et diyoruz.

**Ctrl + c** ile terminalden cıkabiliriz.
