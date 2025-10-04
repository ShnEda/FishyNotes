## Firewall
Genel açıklaması şu şekildedir;

Genel bir ağdaki bir network içerisinde bütün düzenlemeyi sağlar. Kurallar gireriz ve kurallar çerçevesinde bütün ağ içerisi kontrol altına alınır. Normalde öyle çalışır ancak günümüzdeki firewall larda çok fazla özellik bulunmakta. Mesela VPN özellikleri olabilir; IDS, IPS gibi ürünler bulunabiliyor; URL filtreleme olabilir. Türleri;
### -Statik Filtreleme
-Network katmanında çalışır, yalnızca paketlerin kaynak ve hedef ip adresleri, port no ve protokol türüne göre filtreler. Burada bu firewall ı bypass leyebiliyoruz.
### -Dynamic Filtreleme
-Network katmanında çalışır, kaynak ve hedef ip adresleri, protokol ve port no göre filtrelerken bağlantı durumlarının takibi yapılabilir.  Burada takip kelimesi çok önemli. Burayı daha zor şekilde bypass lamak gerekebilir.
### -Uygulama Katmanı Firewall
-Uygulama katmanında çalışır. Protokol datası incelenerek uyg. özelliğine göre incelenebilir.
### -Proxy Firewall
-Üzerinde çok durulmadı ama kısaca Proxy'ler istemci ile sunucu arasında bir köprü oluşturur ve tam bir oturum analizi yapabilir.

## VPN (Virtual Private Network)
Günlük kullandığımız VPN servislerinin aksine **kurumsal** VPN’ler şirket çalışanlarının, uzaktan şirketin sistemine güvenli şekilde bağlanmalarını sağlar ve tıpkı ofiste gibi şirket ağına bağlanarak fiziksel ofisteymiş gibi şirket sistemlerine, dosya sunucularına ve diğer ağ kaynaklarına erişim sağlayabilir. Bu yapı, hem güvenliği artırır hem de esnek çalışma imkânı sunar.
