**Konu başlıkları:**

1- Bilgi güvenliği bileşenleri, teker teker incelenedi

**CIA üçgeni**nde bizi şunlar karşılar:

	-Confidentiality(Gizlilik): Bilginin yetkili insanlara bulunması
	-Integrity(Bütünlük): Bilginin değiştirilmemesi, tam olması
	-Availability(Erişilebilirlik): Bilginin yetkili insanlarca	ulaşılabilir olması
	
2- Saldırı türlerini hedefe yönelik 2ye ayırdık:

	Belirli hedefi olan: Belirli kişi, kurum veya sisteme
		-Phishing
		-DDoS
	Belirli hedefi olmayan:
		-Virüsler
		-Botnet saldırıları
		-Solucanlar vb.
		
> ## Zararlı Yazılım (Malware) Türleri
	-**Virüs**: Kendini diğer dosyalara bulaştırarak çoğalan ve zarar veren yazılımlar.
	-**Trojan (Truva Atı)**: Yararlı gibi görünen ama arka planda kötü amaçlı işler yapan yazılım.
	-**Spyware (Casus Yazılım)**: Kullanıcının bilgilerini gizlice toplayan yazılım.
	-**Keylogger**: Klavye girişlerini kaydedip şifre gibi bilgileri çalan yazılım.
	-**Ransomware**: Dosyaları şifreleyip, açmak için fidye isteyen yazılım.
	-**Worm (Solucan)**: Kendi kendine çoğalıp ağ üzerinden yayılabilen zararlı yazılım.
	-**Rootkit**: Sisteme gizlice sızıp yönetici yetkisi kazanan yazılım.
	-**Adware**: Kullanıcıya sürekli reklam göstererek rahatsız eden yazılım.
	-**Stealer**: Şifre, çerez, kripto cüzdan bilgileri gibi hassas verileri çalan yazılım.

> ## Saldırganların Motivasyon ve Hedefleri
	-**Finansal Kazanç**: Fidye, kredi kartı bilgisi veya kripto cüzdanları çalarak gelir elde etme.
	-**Casusluk**: Devlet veya şirket bilgilerini toplamak.
	-**İtibar Zedeleme**: Rakip firmalara veya bireylere zarar vermek.
	-**Eğlence / Ego**: “Hackledim” diyebilmek, prestij kazanmak.
	-**İdeolojik Nedenler**: Hacktivizm (politik/sosyal mesaj verme).

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
