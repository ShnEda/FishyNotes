# Statik Analiz
Statik analiz adından da anlaşılabildiği üzere bir yazılım veya dosyanın çalıştırılmadan incelenmesi, analiz edilmesi sürecidir. Bu şekilde olası kod parçacıkları ve olası tehdit unsurlarının tespitinde kullanılır.

## Temel Özellikleri
Statik analiz, dosyanın temel özelliklerini -dosya türü, hash değeri, paketlenmiş dosyanın içerisinde olup olmadığı, vb.- kullandığı fonksiyonları ve davranış kalıplarını incelememizi sağlar. Dosya çalıştırılmadan içeriğini detaylı şekilde taramamıza yarar. Zararlı kod çalıştırılmadan olası tehditleri incelediğimizden çok büyük bir risk oluşturmaz, hızlı şekilde çabuk tanımlanabilir analizler incelenebilir ve ayrıca derlenmemiş kodları inceleyebiliriz. Ancak dinamik analizin aksine çalıştırılmadığından, inceleme yaptığımız dosyanın bazı hareketlerini göremeyebiliriz. Paketlenmiş veya obfuscate edilmiş kodların analizi işimizi zorlaştırır.

> **Hash**: Girdi verisini karmaşık bir algoritmayla özetler, benzersiz ve sabit boyutlu bir çıktı üretir. Bazı örnekleri: MD5, SHA-1, SHA-256 vb.
> **Obfuscation**: Karmaşıklaştırma işlemi.  Genellikle kodda ya da script verilerek karşımıza çıkıyor. Değişken isimleri veya fonk isimleri gibi okunabilir ögeler rastgele veya anlamsız hale getirilir. Çeşitli yöntemlerle de karşımıza çıkabilir phishing vb ile. Kodun işleyişini ve/veya mantığını gizleyerek, analistin kodu analiz etmesini veya kopyalamasını zorlaştırır. Sistemlerde analiz yapan insanların işini zorlaştırmak amaçlarından olabilir.
> **Packing**: İçerisinde dosyanın çalıştırılabilir kısmının packlendiği kısımlar var. Daha sonra bir noktadan çözülerek dinamikte çözülebiliyor. Statikte ise clear şekilde göremiyoruz. Amaç da güvenlik korumalarını aşmak, tespit edilmemek. Yine çeşitli toollar kullanılarak bunu unpack edebiliyoruz genelde. Çalıştırılabilir dosyanın içerisinde paketlenmiş veri olup olmadığını Detect It Easy ve CFF Explorer gibi araçlar yardımıyla öğrenebiliriz.

## Bazı Statik Analiz Teknikleri

1- **İmza Tabanlı Tarama**
Bilinen kötü amaçlı signature'ları dosya içinde arar.
```
Örnek: Bir dosyada bilinen ransomware imzası aranır
Hash değeri: a3f2e8d9c1b4...
Sonuç: Eşleşme bulundu → Tehdit tespit edildi
```
İmza veritabanında bulunan bilinen zararlı yazılım hash değerleri veya pattern'leri ile incelenen dosya karşılaştırılır ve eşleşme durumunda tehdit anında tespit edilir. *Dezavantaj*ı şunlardır: Bilinen tehditler tespit edilebilir, zero-day saldırılara karşı etkisizdir ve bu veritabanlarının güncellenmesi gerekir. Ancak *avantaj*ları arasında düşük false-positive oranı, hızlı tespit süresi ve bilinen tehditler için yüksek doğruluk oranı bulunur.

2- **String Analizi**
Dosya içerisindeki okunabilir metin dizilerini çıkararak analiz yapmamızı sağlayan tekniktir. URL&Domain Adreslerinde Command&Control sunucu bağlantıları, IP adresleri, e-posta adreslerinde potansiyel sızıntı noktaları, API fonksiyon isimleri, Hedef sistem konumları/Dosya yolları, kayıt defteri anahtarları/kalıcılık mekanizmaları, bazı kriptografik işlemleri kapsar.

```
strings -a malware .exe | less
strings -a malware .exe |grep -i "http"
```
Ancak obfuscate edilmiş string'leri tespit edemeyebilir. Hızlı bilgi toplamamıza yarayabilir ve manuel kod analizi gerektirmez.

...Devamı gelecek
