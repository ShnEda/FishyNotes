## DHCP Starvation

DHCP (Dynamic Host Configuration Protocol) protokolünün çalışma mantığını bilmemiz gerekir. Saldırgan sahte MAC adresleri oluşturarak DHCP sunucusuna sürekli IP talebi gönderir. DHCP sunucusunun IP havuzu tükenir ve verebileceği IP kalmaz. Bu durumda yeni bağlanmak isteyen kullanıcılar ağa IP alamadığı için bağlanamaz.

**Savunma:** DHCP sunucusunda limitler tanımlanarak bir cihazın aynı anda çok sayıda IP talebi yapması engellenebilir. Ayrıca MAC adresi başına maksimum istek sayısı belirlenmelidir.

## DHCP Snooping

Switch'ler üzerinde uygulanan bir güvenlik mekanizmasıdır. Trusted port tanımı ile DHCP sunucusunun bulunduğu port belirlenir. Güvenilmeyen portlardan gelen DHCP yanıtları engellenir. Bu sayede sahte DHCP sunucularının ağa dağıtım yapması önlenir. DHCP'nin ağ dağıtımının kötüye kullanılmasını engellemek için kullanılır.

## Yerel Ağ Saldırıları

### Ağ Trafiğinin İzlenmesi (Sniffing)

Ağda gerçekleşen trafiği dinleyerek ne olup bittiğini öğrenmemizi sağlar. Firewall'lar ve IDS/IPS gibi cihazlarla birlikte kullanılır. WIFI bağlantısında elektromanyetik frekanslar üzerinden iletişim sağlanır ve bu dalgalar etrafa yayılır. Ağın AP şifresini biliyorsak WIFI trafiğini dinlememiz kolaylaşır, ancak switch gibi cihazlar devreye girdiğinde sniffing işlemi zorlaşır.

### Sniffing Türleri:

**Pasif Sniffing:** Ağ trafiği yalnızca gizlice izlenir, herhangi bir müdahalede bulunulmaz. WIFI kartı varsa monitoring moda geçilir. Wireshark veya tcpdump gibi araçlar kullanılabilir.

**Aktif Sniffing:** Ağ trafiğine aktif müdahale edilir (ARP spoofing, MAC flooding gibi).

### MAC Adresi Değiştirme

Genel inanışın aksine MAC adresleri `ifconfig` veya `macchanger` gibi araçlarla kolayca değiştirilebilir.

### Kullanım:
```
# Random MAC üretmek
macchanger -r eth0

# Gerçek MAC adresine dönmek
macchanger -p eth0
```

### Kali Linux ile:
```
ifconfig
sudo macchanger -r wlan0
sudo macchanger -p wlan0
```

---

## MAC Flood

Dsniff paketiyle gelen `macof` aracı ile çok sayıda sahte MAC adresi ağa gönderilerek switch'in MAC adres tablosu doldurulur. Hafızası dolan switch HUB gibi davranmaya başlar ve tüm trafiği tüm portlara iletir. Bu durumda switch servis dışı kalabilir veya sniffing yapılabilir hale gelir.

## ARP (Address Resolution Protocol)

IP adreslerini fiziksel adreslere (MAC adresi) çözümlemek için kullanılan protokoldür.

**ARP Request:** Bir cihaz, "Bu IP adresine sahip MAC adresi kim?" sorusunu broadcast olarak ağa yayınlar. IP adresine ait donanım adresini sorgulamak için kullanılır.

**ARP Reply:** Hedef cihaz, "Bu IP benim ve MAC adresim şu" şeklinde unicast olarak cevap verir.
