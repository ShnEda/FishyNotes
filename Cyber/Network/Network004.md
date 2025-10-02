###Traceroute

Sizin gitmek istediğiniz yere ulaşırken hangi bilgisayarlardan/*IP*'lerden adım adım geçtiğinizi gösterir. Local ağlar üzerinde giderken benim paketimin nerelerde takılı kaldığını/ nerelerden geçtiğini anlamamızı sağlayabilir veya aklımızda daha rahat canlandırmamızı sağlar*(network topolojisi)*

Kali'de:

    traceroute google.com

Windows'ta:

	tracert www.google.com

Biz bunu yazıp üzerine * işareti çıkarsa bunun nedeni ya bir switch ya da firewall olabilir. Peki bu yasaklar nasıl atlanılabilir?

1- UDP paketleriyle erişilmeye çalışılabilir

2- -I eklersek ICMP paketleri yollayıp ilerlenebilir

3- -T kullanarak TCP paketleriyle yollanıp ilerlenebilir

Port yazıp erişim sağlanmaya çalışılabilir.

Peki biz bu sırayla gördüğümüz adresleri nasıl görüyoruz? **TTL**!

Ana mantık *TTL* üzerinden işliyor. Sizle ilk olarak ICMP isteğini attığımızı varsayalım. Bunun destination'ı google.com 'a gidecek. Bunun ICMP paketinin değerini 1 yapıyoruz. Paket öldüğü zaman paketin yolda öldü diye cevap veriyor. Bu şekilde haber ala ala öğrenmiş oluyoruz. TTL değeri cihazınızda zaten tanımlıdır. (TTL=Time to Live : paketin yaşama süresi gibi bir şey) Eğer paketin öldü demezse sonrakine geçerek *** şeklinde gösteriliyor.
