**Konu başlıkları:**
1- Bilgi güvenliği bileşenleri, teker teker incelenedi
**CIA üçgeni**nde bizi şunlar karşılar:
	-**Confidentiality(Gizlilik)**: Bilginin yetkili insanlara bulunması
	-**Integrity(Bütünlük)**: Bilginin değiştirilmemesi, tam olması
	-**Availability(Erişilebilirlik)**: Bilginin yetkili insanlarca	ulaşılabilir olması
2- Saldırı türlerini hedefe yönelik 2ye ayırdık:
	Belirli hedefi olan: Belirli kişi, kurum veya sisteme
		-Phishing
		-DDoS
	Belirli hedefi olmayan:
		-Virüsler
		-Botnet saldırıları
		-Solucanlar vb.
3- saldırganların kimlerin olabileceği
	-Kurum içi çalışanlar
	-Devlet Destekli Aktörler
	-Siber suçlular
	-Hacktivistler
	-Script Kiddies
4- Kurumsal sistemlerin güvenilirliğinin denetlenmesi etc, daha sonrasında ise saldırganın gözünden bakılması, incelenmesi.
5- Bazı pentest metodojileri:
	-OSSTMM
	-NIST SP800-115
	-ISSAF
	-OWASP ->en çok kullanılanı OWASP
6- Pentestin genel adımları:
	-Keşif
	-Tarama
	-Zafiyet Değerlendirmesi
	-İstismar
	-Raporlama(En önemli kısım)
7- Bilgi toplama yöntemleri: **Pasif/ Aktif** olarak incelendi
	Pasif:
		-Arama motorları, burada loglanan veriler vb. 
			burada arama için kullanacağımız terimler önemli, örneğin site ismi vb şeyler belirli şekilde aranabilmekte.
		-whois sitesi ile domain history
		-viewdns.info ile dns aramaları
		-dns dumpster
		-pimeyes fotoğraf
		-intelligence x
		-breach.vip
		-project discovery
		-cyberchef
		-osint.rocks
		-osint industries ama sanırım paralı
		-birdhunt
	Aktif:
		-wiglenet
		-shodan
		-robots.txt kullanılması
		-dns sorgu tipleri(üzerinde durulmadı)
		-eavesdropping, shoulder surfing, dumpster diving, impersonation sosyal müh. bilgi toplama aşamaları.
