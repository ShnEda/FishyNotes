# Güvenlik Zafiyeti Nedir?

Sistemde hataya sebep olabilecek bir açığa güvenlik zafiyeti diyoruz. Amacı saldırganların bunu kullanarak sistemden bilgi çalması, sistemi değiştirmesi veya zarar vermesi.

---

# Sızma Testi Nedir?

Bir güvenlik uzmanının sistemde zafiyet bulma çalışmasıdır. Amacı saldırganın bulabileceği zafiyetleri önceden tespit etmek.

## Sızma Testi Alanları:

**Ağ Güvenlik Testi:** İç ağ ve dış ağ testleri yapılır. İç ağ çalışan ağlarıyla alakalı servisler gibi.

**Web Uygulama Güvenliği:** Web uygulamalarında SQL Injection, XSS, CSRF gibi zafiyetlerin tespit edilmesi.

**Mobil Uygulama Güvenliği:** Web ile benzer, amaç genel olarak uygulamanın eriştiği adreslerde anormal çıktı elde etmek. Eriştiği servislerde zafiyet var mı yok mu kontrol etmek. Aslında ayrı alanlar da benzer servisler bulunmakta olduğundan benzer dedik.

**API Güvenliği:** Genel olarak API'da server taraflı zafiyetleri tetiklemek, her bir API endpoint'ine farklı değerler vererek bir zafiyet bulmak amaçlanır.

**DDoS ve Yük Testi:** İkisi arasındaki fark yük testi sistemin kapasitesini ölçmek için, DDoS testi ise servis dışı bırakma saldırılarına karşı dayanıklılığı test etmek için yapılır.

**Sosyal Mühendislik:** Phishing gibi yöntemler. Şirketlerin bu tarz şeylere maruz kalmaması için önceden bir çalışma yapıyorlarmış.

**Kritik Altyapı Sistemleri Güvenliği:** Su altyapıları gibi sistemlerde arka planda kullanılan PLC dediğimiz bazı endüstriyel yazılımların zafiyetleri bulunmakta, amaç da bunu kontrol etmek. Vana açma kapama gibi işlemler.

**Fiziksel Güvenlik:** Binaların fiziksel erişim kontrollerinin test edilmesi. Kartlı geçiş sistemleri, kamera sistemleri gibi fiziksel güvenlik önlemlerinin test edilmesi.
