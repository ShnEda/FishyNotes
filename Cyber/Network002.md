**Subnetting** önemli, nedir ne işe yarar?

Subnetting, bir IP adresini kendi alt ağlarına bölmesidir. Daha rahat anlayabilmek için şu şekilde gösterebilirz:

	  -10.0.0.1/16

**IP** dediğimiz şey nasıl işler?
*0.0.0.0* ->4 bloktan oluşur, gidebileceği en yüksek sayı da 225'tir.
32 bittir. 


00010111'den dört tane düşünürsek: 23.23.23.23 oluşur. Daha sonra da 10.0.0.0'a /24'lü **subnet** geldiğini varsayalım. Bu da şu anlama denk gelir: 0'dan 255'e kadar sayı verebiliriz.
	
**Windows** işletim sistemlerinde -> **ipconfig** komutu ile cmd'den veya Powershell'den **IP** öğrenilebilir. Ya da Control Panel üzerinden network ayarlarından da yine detaylı bir şekilde görebiliriz.

**ARP**: ping gibi işlediğini düşünebiliriz.

Windows'ta -> 
		
		arp -a
(bulunduğunuz bütün network e arp istekleri göndermemizi sağlar.)

ARP üzerinden saldırılar da gerçekleştirebiliriz: **ARP poisoning** vb.

DNS Sorgu tipleri tablo halinde incelendi.

-Örneğin KTÜ'ye http isteği atmamız için daha öncesinde DNS ile Ktüye 
bağlanmamız için DNS ile istek atmamız gerekir.

*Burası yanlış olabilir düzeltin lütfen! Düzelttikten sonra söyleyin!*

      Aşağıdaki adam /etc/hosts içerisinde diye düşünülsün.
	     O  Soldaki gibi bir adam olsun. Bu adam da Hepsiburada.com'a istek
	    /|\   atmak istiyor, girmek istiyor. Önce bilgisayarının içerisinde
		/ \   DNS ayarlarının olduğu /windows/System32/drivers/etc/hosts.conf
		benzeri bir dosya path'i vardır.
		    Bu adam gitsin 8.8.8.8 ile hepsiburadaya bağlanmak istesin.
		Google desin ki bn burayı bilmiyorum. Sonra bu adam 8.8.4.4 ile TLD serverına gider
		(TLD=TOP LEVEL DOMAIN). Burası da desin ki bende yok. Gideceği 3. server
		da ROOT server olacaktır. Doğrudan hepsiburadanın kendi DNS serverına gider.
		Eğer hepsiburadanın kendi serverında da yoksa yok artık.
		Bağlanırsa da artık TCP bağlantısı kurulmaya hazır denebilir.
