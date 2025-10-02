DNS Sorgu Tiplerine bakarsak: (Hepsini bilmeye gerek yok)

	-A kaydı: O alan adının host ip sini söyler
	-MX kaydı: mail serverının ip sini söyler
		-dig MX ktu.edu.tr (MAC)
	-NS kaydı: Alan adının kendi DNS sunucu adresini verir
		-dig NS ktu.edu.tr (MAC)
	-TXT kaydı: bildiğimiz txt gibi düşünebiliriz, istediğimizi
	yazabiliriz.
  
	#alan adlarında mail güvenliği için SPF kullanmışız.
	#alan adlarının mail güvenliği için dmarc kayıtları önemlidir.

**WAF(Web Application Firewall)**=>Önce atılan istekler ana bağlantıya gitmeden buraya gelir. Sunucunuzun *IP*'sini değil WAF'ın *public IP*'si dir. Bir sıkıntı yoksa Ana web sunucusuna bu istek yönlendirilir. Örneğimiz h####burada'dan  devam edersek; WAF 'tan sonra firewall 'a ulaşılır ve burada aslında WAN ile LAN arasında bir iletişim de sağlanır. Daha sonra kendi rule larını inceledi, bir sıkıntı yoktu ve sonra sizi *Web Serverı*'na iletti. Şöyle de bir şey var:

Büyük bir yer için 1 adet web app sec yetmeyecek. Şirketlerimiz de bu yoğunlukların önüne geçmek için kullandıkları şu yapı vardır: küçük küçük daha çok sunucu alırlar ve istekler bu birden fazla sunucu arasında dağıtılır.

Bu istekleri dağıtacak şey de: **Load Balancer**. Verilerin saklanması için *DB(Data Base)* bulunur ve sunuculardan buraya bilgiler gider. Ancak büyük veri aktarımları durumunda büyük DB 'lere ihtiyaç duyulur. Bu DB 'lerle **cluster** 
oluşturabiliyoruz. Buradaki serverlardan bir tanesi Master, kalanları da DATA gibi isimlerle adlandırılır. Master olanının ana işlevi ona atılan isteklerin diğer yerlerden çekmesi ve yönlendirmesi. Bunların ayrıca Replica diye adlandırılan DATA'ların yedekleri bulunur. 
