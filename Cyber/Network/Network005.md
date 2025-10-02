### ARP Ping

Hedef sisteme ARP atılarak cevap dönerse hedef sistemin aktif olduğu tespit edilir. Bunu yapmamızın sebebi bir ağa bakarken ilk olarak oradaki açık
sunucuları bulmamızdır. Genel olarak ARP, firewall tarafından engellenmez. Yerel ağda çalışır.

### UDP Ping
```
nmap -sn -PU
```
ile atılır. Kapalı bir port 'a UDP gönderiyoruz. Eğer **ICMP port unreachable** dönerse makine açıktır. Makine açık değilse **ICMP host/network** unreachable döner.

### ICMP Echo Ping Taraması
```nmap -sn -PE```
ile yapılır. Echo olmayan pingde ping paketlerinin kısıtlanmış olduğu ancak ICMP protokolünün tamamen engellenmediği durumlarda aktif sistemleri belirlemek için kullanılır. İşlemcinin döneceği cevaplardan dolayı pek kullanılmaz.

### Time Stamp Req Reply
```nmap -sn -PP```
ile yapılır. Bu sayede karşı tarafın zaman paketini öğreniyoruz. Yani saatini. Type 13 timestamp Request gönderilir, Type 14 Reply döner.

