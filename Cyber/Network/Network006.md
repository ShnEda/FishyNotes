## NMAP ile Port Tarama

Nmap aracı port tarama, servis belirleme, işletim sistemi tespiti gibi gelişmiş özelliklere sahip bir ağ haritalama aracıdır.Standart olarak belirli
portları tarar. Temel bir **nmap taraması**:

	nmap 192.168.1.1
  
	nmap www.abc.com.hs

nmap kullanırken illa ki IP girmemiz gerekmiyor. Örneğin:
```
nmap -p 80 ktu.edu.tr
```
ile ktu.edu.tr 'nin 80 portunu taradık.

```
nmap -iL liste.txt
```
ile liste.txt üzerinden IP list'i kullanarak içerisinde bulunan IP'ler üzerinden port taraması yapılabiliyor.

> NOT: iptables= Linux'un firewall u denebilir.

### Port Tarama Yöntemleri
> (ÖNEMLİLER= sS, sA, sF veeeee sV!!!!)

```-sT```=> Dümdüz TCP taraması. Arkada iz bırakır ve yavaş işliyor.

```-sS```=> En çok kullanılan parametrelerden biri. nmap'te Syn scan olarak da
geçer. Doğrudan RST paketi yollarız ve arkamızda da iz bırakmaz. #ÖNEMLİ

```-sA```=> Çok kullanılmaz. Kendine özgü bir parametredir. Firewall varsa onu **bypass**'lamak için kullanılır. Dümdüz bir Ack paketi yolluyoruz. Yanıt olarak ICMP Unreachable gelmesi veya cevap gelmemesi portun filtreli olduğu anlamına gelir. Normalde RST paketi dönmesi gerek ve bu portun kapalı olduğu anlamına gelir ve RST gelmeyenler açık portlardır. Filtrelenmiş  portları bu parametreyle buluruz. Açık olup olmadığını göremeyiz.

```-sF```=> Fin scan. Kapalı bir port a Fin paketi atıyoruz RST paketi dönerse o port kapalı denebilir. Yapılan işleme göre kapalı port tan cevap geliyor. Cevap gelmeyen her port 'a açıktır diyebiliriz.

```-sN```=> Ana amaç TCP paketi atılır ancak bayrağı yoktur. İçi boş TCP paketi ile kapalı porta gittiyse RST paketi geri döner, bu şekilde portun kapalı olduğu anlaşılabilir. (NULL Scan)

```-sM```=> FinAck atıyoruz.

### Nmap Script Kullanımı
```-sC```=> Otomatik olarak bu parametre sayesinde zafiyet taramaları gerçekleştirilebilir. Aynı zamanda kendi Script 'inizi de yazabilirsiniz. Ayrıca yapacağınız taramanın hangi scriptler kullanılacağını da yazabilirsiniz.

---
> ```-A``` => -sV ve -sC nin beraber yazılmış hali denebilir
> zenmap: nmap için grafik arabirimidir.
---

### UDP Taramaları

Port 'un kapalı veya filtrelenmiş olduğunu anlayamayız. Genelde son çaredir.

```--reason``` parametresi ne işe yarar? Şunu söyler: Bu port neden açık.

### Tarama Sonuçlarını Kaydetmek

```-Pn```=> TCP Paketlerinden önce o makinenin açık olup olmadığını kontrol ediyor.

```-f```=> Firewall ya da IDS gibim sistemleri atlatmak için TCP paketlerini
parçalara ayırıyor.

```-T5```=> Tarama hızı, rakam arttıkça hız da artar.

## IP Address Spoofing
Aslında IP başlığındaki Source IP 'nin değiştirilmesi denebilir. Saldırganımız olsun ve bir TCP paketi olsun; bunun source ve destination IP'leri bulunmakta. Ancak bizim burada yaptığımız kısım source IP yerine başka bir IP yazmamız demek. Cevabını bize yani saldırgana değil yine asıl gönderilecek cihaza yönlendiriliyor. Buradan *şunu* yapabiliriz:

	B sunucusu olsun ve desin ki ben sadece A sunucusundan istek alırım başka kabul etmem. Burada hatırlarsanız seq num vardı, A sunucusuna kapalı porttan Ack yollarsak bize RST dönecek. Sonra IP spoofing ile kendi ip 'mize A sunucu IP' sini yazdık ve B' ye yolladık. Aralarında dönecek işlemler doğrultusunda (RST) portların açık/kapalı durumlarını öğrenebiliriz.

Bunu nmap ile nasıl yapabiliriz?

	-Metasploit  VM'inden Firewall açtık.
	-sudo nmap -sS 192.168.X.X (VM)
	-sudo nmap -sA "              (VM)
	
	Bundan sonra windows 7 VM 'ini açtık.
	
	-sudo nmap -sI 192.168.X.Y 198.168.X.X (1.si zombie makinemiz)
	
	Bu şekilde IP spoofing yaparak açık portları görmüş olduk.

```-sV```=>portta çalışan uygulama ve hangi versiyonu olduğunu söylüyor.

```-sO```=> Hedef makinenin desteklediği IP protokollerini tespit eder.

```-O```=> Bizim karşı taraftaki bilgisayarın OS 'ini anlamak için kullanılır.
