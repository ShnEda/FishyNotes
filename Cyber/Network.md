**TCP/IP**=> Bilgisayarlar arası ağ bağlantılarını simüle etmek için bir uygulama / websitesi vardı; bunun üzerinden rahatça yapılan sanal davranışlar rahatça görülebilir, örneklerle şekillendirilebilir.

Ya da isterseniz CISCO'nun paket trace diye bir uygulaması var onun üzerinden de inceleyebiliriz hem fiziksel hem de cihazlar arası.

	O(A mac adresi olsun. 10.0.0.1 diye de ip si oldu)
        |
O ------------- O(B mac adresi olsun. 10.0.0.4 ip'si)
        |
        O -> Böylece network ümüzü inşa ettik

2. katmanda bulunan ip, switch, ICMP(ping atabiliriz), IGMP(ICMP ile alakalı)

Başka bir ilde bulunan bir bağlantıyı sağlamak için kablo döşemek yerine LAN'ı icat ettik diyebiliriz.
**LAN(Local area network)** -> belli bir bölgedeyken;
**WAN(wide area network)** -> sayesinde uzak bölgelerde bulunan ağlara da bağlanmamızı sağlanabilir.

Burada paketin doğruluğunu şu şekilde kontrol edebiliriz: **TCP**!
    Verinin güvenirliliği için TCP (3. katmanda: TCP ve UDP 'yi inşa etmiş oluruz, burada başka bir şey karşımıza çıkmaz diyebiliriz) paket açıldığında karşı taraf diyebilir ki artık bu paket doğrudur, eksiği olmadan ulaşmıştır. TCP dendiğinde akla gelecek ilk şey **üçlü el sıkışması** olabilir, bunu şöyle açıklayabiliriz: (sıra no önemli)
        +A->B'ye SYNo paketi yollar. (sorguluyo B orda mı bağlantıya uygun mu)
        +B->A'ya SYN+Ack paketleriyle art arda yollama yapar.
		+A->B'ye Ack yollar.
		+A->B'ye istediği bilgiyi yolladı diyelim
		+Açılan TCP oturumunun kapanması lazım yoksa karşı bilgisayarda yer
		kaplar, bu yüzden de istekle açıldığı gibi kapanır diyebiliriz.
		+Bağlantıyı kapatmak için fin bayraklı paket yollanır: A'dan B'ye
		+Sonra da Fin+Ack bayraklı paket yollanır ve bağlantı sonlandırılır.
		Her istek atıldığında bu tekrarlanır.

Diyelim ki istenen bilgi Hello world ama en sondaki d harfi gitmemiş, bu durumda **parity check** yapıldı ve baktık ki bilgiler uyuşmuyor. Olmaması gereken bir durum gerçekleştiği için RST paketi ile cevap verilir.

**PSH & URG** paketlerinin ismen hatırlamamız kafi

**TCP** default port: **80**

**UDP**=>User Datagram Protocol, 
A bilgisayarı B'ye istek atsın.
    +Dümdüz mesajlar gönderilir, daha sonrasındaki özelliklerin bir önemi yoktur; gönderilen bilginin karşıya ulaşıp ulaşmadığı, doğru gönderilip gönderilmediği önemsenmez. TCP'den bu yüzden hızlıdır. Peki kapalı bir bilgisayara atarsak? Bu sefer bir alttaki katmana geri döneriz ve karşı bilgisayarın kapalı olup olmadığı sorgulanıp size şöyle bir hata verir: Bilgisayar kapalı. UDP kesin bir şey söylemez bununla yapılan port taramaları çok kesin değildir.

**UDP** default portu: **53**

**TCP & UDP** farklarından bazıları:
- Hız
- Güvenilirlik
- Port Farklılığı vb.

**Not**: *Bozulma yaratmayacak şeyler UDP, email vb şeyler TCP ile yollanabilir.*

**ICMP**=> işleyiş: req yollanır aslında. Kendi içerisinde de farklı tip-
leri bulunur. Örneğin ICMP type8 vb. **Nmap**te işimize yarar fakat kısa bir örnek göstereceğiz.
    ICMP ile bilgisayarın açık olup olmaması öğrenilebilir, silverfish ile reverse shell alınabilir veya birçok şey yapılabilir.

Networkleri kullanarak bir dosya paylaşım sistemi yapalım dedik, bunun üzerine servisler ortaya çıktı. Bunlar email vb şeyler olabilir. Bunlar için de bir standart oluşturulmak istendi: **Application Katmanı**. İnternet sitesine istek atarken HTTP req yaparız. Aslında alt taraftaki protokolleri de kullanır. Daha detaylı şeklini daha sonra inceleyeceğiz.

Application Katmanındaki protokollerden bazıları: SMTP, FTP, IMap, SMB, SSH, TelNet, DNS, RDP, HTTP, HTTPS... Peki bunlar ne yapıyor?

**SMTP**: Simple Mail Transfer Protocol, Port:25 fakat şu anda güncel ola-
rak başka portlar kullanmakta, arkada TCP kullanılır.
**FTP**: File Transfer Protocol, Port:**21**, TCP alt katmanında kullanılır.
**IMap**: Port:**143**, TCP, mailleri almak için
**SMB**: Port:**445**, Server message block, TCP
**SSH**: SecureShell, Port:**22**, TCP
**TelNet**: Uzaktan erişim için, PORT:**123**, TCP
**DNS**: Domain Name Server, Port:**53**, UDP; HIZLI OLMAK İÇİN
**RDP**: Remote Desktop, Port:**3389**
**HTTP**: Hyper Text Transfer Protocol, Port: **80**, TCP
**HTTPS**: secure hali, Port:**443**, TCP

**Not**: *TCP/IP'de alttan üste doğru ilerlediğimizden bu şekilde buraya kadar anlattık.*
