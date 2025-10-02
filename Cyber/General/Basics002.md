## Honeypot nedir?
CTI firmalarının kullandığı bir uygulamadır. Burayı hacklenmesi için oluşturursunuz. Zafiyeti özellikle koyuyoruz. Makinenin içerisinde ekstra olarak sistemi monitör eden yazılımlar var. Buradaki asıl amaç bir hackerın bu zafiyeti nasıl çözdüğünü izleyip bu insanın burada nasıl bunu elde ettiğine bakılmasıdır.

## Zayıflıkların isimlendirilmesi
En çok kullanılan zafiyet isimlendirilmesi **CVE**Common Vulnerabilities and Exposures. CVE - hangi yılda bulunduğu - o yıl bulunduğu sıra numarası. Bu sayede dünya genelinde bulunan zafiyetlerin takibi kolaylaştırılmış oluyor. Bunun için çok kullanılan bir internet sitesi. *cve.mitre*; *web.nvd.list* de bunun için kullanılan bir site. Microsoftun kendi zafiyetlerini yayınladığı bir yer de var: *https://msrc.microsoft.com/update-guide/vulnerability*. Aynı zamanda *exploit-db* diye bir yer var , *vuldb* de kullanılabilir. CVE 'lerin ayrıca derecelendirilmesi için kullanılan sistemdir. Genelde **0-10** arasında *puanlanır*.

> **Not**: CVElerin bir de skorlanma sistemi var. Öncelik yüksek olması. yüksek-orta-düşük gibisinden. Her bulduğunuz CVE nin bir önemi bulunur.

