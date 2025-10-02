### ARP Ping

Hedef sisteme ARP atılarak cevap dönerse hedef sistemin aktif olduğu tespit edilir. Bunu yapmamızın sebebi bir ağa bakarken ilk olarak oradaki açık
sunucuları bulmamızdır. Genel olarak ARP, firewall tarafından engellenmez. Yerel ağda çalışır.

### UDP Ping
```
nmap -sn -PU
```
ile atılır. Kapalı bir port 'a UDP gönderiyoruz. Eğer **ICMP port unreachable** dönerse makine açıktır. Makine açık değilse **ICMP host/network** unreachable döner.

### ICMP Echo Ping Taraması
```
nmap -sn -PE
```
ile yapılır. Echo olmayan pingde ping paketlerinin kısıtlanmış olduğu ancak ICMP protokolünün tamamen engellenmediği durumlarda aktif sistemleri belirlemek için kullanılır. İşlemcinin döneceği cevaplardan dolayı pek kullanılmaz.

### Time Stamp Req Reply
```
nmap -sn -PP
```
ile yapılır. Bu sayede karşı tarafın zaman paketini öğreniyoruz. Yani saatini. Type 13 timestamp Request gönderilir, Type 14 Reply döner.

### TCP SYN Ping
```
nmap -sn -PS
```
TCP paketleri ile yapmak istersek açık porttan SYN/Ack cevabı, kapalı porttan RST döner. Firewall TCP bağlantılarını loglar ve bu yüzden sadece port açık mı diye bakıp bağlantı kurmadan bağlantıyı kesiyoruz.


```
nmap -sn -PA
```
TCP üzerinden veri aktarıyormuş gibi Ack bayrağı taşıyan paket gönderilir.

### IP ping
```
nmap -sn -?
```
ICMP, IGMP, TCP, UDP gibi protokolleri istek atıyoruz.

> Bunların dışında; nmap, hping, Pinger, Ping Sweep gibi programlar ve standart ping komutu ile ping taraması yapılır.

> ```nmap -sP``` komutu artık ```nmap -sn``` olarak kullanılıyor. Ama eski sürümlerde -sP geçerlidir ve ping taraması yapar. Bu komut, ağ taramaları ve cihaz keşfi için yaygın olarak kullanılır.

**TTL değeri** hedef sistemin uzaklığı ve işletim sistemi hakkında bilgi verir. TTL değeri bu yüzden değişkendir, değişebilir olduğundan da güvenilir değil.

Portlar işletim sisteminin iletişim için kullandığı sanal kapılardır. Ağ servisleri iletişim kurmak için bunları kullanırlar.

> Toplamda **65535** adet port bulunmaktadır. (Sınavlarda çıkabilir)

***0-1024*** arası *port*lar sabit görevlerde kullanılırlar değiştirmiyoruz. Hatta bunlar ***Well-Known Services*** olarak da bilinirler. Bir portu aynı anda iki servis <ins>kullanamaz</ins>. Bunun sebebini şöyle açıklayabiliriz: Diyelim ki bir portta iki uygulama var ve bu porta istek atmamız gerekti. Atılan isteği hangi uygulama üzerine alacak? Kısaca karmaşa gerçekleşiyor. Özetlersek her portta bundan dolayı tek bir uygulama çalışır. 1024 üzerindeki portlar iletişim sistemi tarafından ihtiyaca göre rastgele kullanılır. 

TCP portunun açık olup olmadığını anlamak için ```nc``` veya ```telnet``` kullanılır.
