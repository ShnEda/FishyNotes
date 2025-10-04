> *Bu dosya, içerisinde **WEB** konu başlıklarını içermektedir. Aynı bilgilerin benzerleri Cyber/WEB klasörü altında da incelenmektedir!!!*

DNS Sorgu Tiplerine bakarsak: (Hepsini bilmeye gerek yok)

	-A kaydı: O alan adının host ip sini söyler. sizin erişmek istedğnx domainin ip sini tutan kayıtdeğeri
	-MX kaydı: mail serverının ip sini söyler
		-dig MX ktu.edu.tr (MAC)
	-NS kaydı: Alan adının kendi DNS sunucu adresini verir. Domainlerden aldığınız yerlerden name serverin tanımlı olduğu yer
		-dig NS ktu.edu.tr (MAC)
	-CNAME: Subdomain oluşturup yayınlamanızı sağlayan yapı. Örneğin domain.com domainine mail.domain gibi subdomainler sağlanabilir.
	-TXT kaydı: bildiğimiz txt gibi düşünebiliriz, istediğimizi
	yazabiliriz.
  
	#alan adlarında mail güvenliği için SPF kullanmışız.
	#alan adlarının mail güvenliği için dmarc kayıtları önemlidir.

# FIREWALL

Firewall'ın amacı tamamen **network yönetimi**dir. Gelen ve giden paketleri incelemek, durumları analiz etmek için kullanılır. Belli başlı kurallar yazmamız lazım, buraya işte Türkiye'den sadece şu internet sağlayıcısından gelen paketlere izin ver gibi. Günümüzde bazı firewall'lar sanki bir güvenlik analiz aracı gibi alert verebilir.

**WAF(Web Application Firewall)**=>Önce atılan istekler ana bağlantıya gitmeden buraya gelir. Sunucunuzun *IP*'sini değil WAF'ın *public IP*'si dir. Bir sıkıntı yoksa Ana web sunucusuna bu istek yönlendirilir. Örneğimiz h####burada'dan  devam edersek; WAF 'tan sonra firewall 'a ulaşılır ve burada aslında WAN ile LAN arasında bir iletişim de sağlanır. Daha sonra kendi rule larını inceledi, bir sıkıntı yoktu ve sonra sizi *Web Serverı*'na iletti. Şöyle de bir şey var:

Büyük bir yer için 1 adet web app sec yetmeyecek. Şirketlerimiz de bu yoğunlukların önüne geçmek için kullandıkları şu yapı vardır: küçük küçük daha çok sunucu alırlar ve istekler bu birden fazla sunucu arasında dağıtılır.

Bu istekleri dağıtacak şey de: **Load Balancer**.
```
# Load Balancer
	Normalde sitenize 1k istek geliyor fakat bir anda 10k istek gelmeye başladı.
Bu durumda load balancer yapısıyla sunucunun çökmesini engellemek için
birtakım işler yapıyor, 3-4 farklı instance'a bölmek gibi.

Bazı kullanım yöntemleri var:
	Scale-Out (Horizontal Scaling): Aynı boyutta farklı sunucular eklemek.
Yük arttığında yan yana yeni sunucular ekleyerek kapasiteyi artırır.
	Scale-Up (Vertical Scaling): Mevcut sunucunun kaynak artırımı.
2 GB RAM'i 4 GB'a çıkarmak, CPU sayısını artırmak gibi
donanımsal iyileştirmeler yapılır.
```

Verilerin saklanması için *DB(Data Base)* bulunur ve sunuculardan buraya bilgiler gider. Ancak büyük veri aktarımları durumunda büyük DB 'lere ihtiyaç duyulur. Bu DB 'lerle **cluster** 
oluşturabiliyoruz. Buradaki serverlardan bir tanesi Master, kalanları da DATA gibi isimlerle adlandırılır. Master olanının ana işlevi ona atılan isteklerin diğer yerlerden çekmesi ve yönlendirmesi. Bunların ayrıca Replica diye adlandırılan DATA'ların yedekleri bulunur. 

**SOC**=> Önceki örneğe devam edersek h####buradanın çalışanları eleman olarak gözüksün. Artık Firewall 'ların *VPN* özellikleri de olduğundan local ağlara bağlanabilirler. Firewall 'da da WLAN özelliği bulunmakta. Bölümlere ayrılmış bu WLAN'ları SOC; bu bütün WLAN, DB, çalışanların bilgisayarlarını vb izler.
	
SOC tarafından yazılan *RULE*'lar barındırılarak belirli ürünler tarafından bu işlemler gerçekleştirilir. Bu yazılan kurallar arasında 

	whoami
komutunu terminalde yazmak istediğimizde alarm gidiyorsa yazılan kurallar bazında oynama yapılarak istediğimizi yazmaya çalışabiliriz.
