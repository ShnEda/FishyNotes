## Kriptoloji
Matematiğin biraz daha ön planda olmasından dolayı biraz niş kalıyor. Kriptografi, okunabilir durumdaki verinin istenmeyen taraflar tarafından okunmayacak hale dönüştürülmesi işlemlerinin bütününe verilen isimdir.

**Encryption** -> Şifreliyoruz

**Decryption** -> Şifrelemeyi çözüyoruz.

Kriptografik algoritmalarda private key vb. terimler bulunmakta. **Public Key** de ise elinizde bir veri var ve Public key ile açabiliriz. Tamamen açabilmek içinse **Private Key**'e de ihtiyacımız olur. 

### Hash Fonk.
Matematik fonksiyonlara verinin kriptografik olarak özetlenmesini sağlar. Hashler geri döndürülemez ancak elimizde bu hash'e benzer bir hash'imiz varsa daha önceden bunun sızdırılmış yani elde tutulan veriye sahip olmasıyla bu şekilde benzer yöntemlerle geri açılabilir. Eğer böyle bir durum yoksa yani fonksiyona erişimimiz yoksa bunun açılması imkansıza yakındır. Bazı durumlarda hashler çakışabilir, bu durumda verinin güvenirliliği ve tutarlılığı değişebilir.

Şifre kırma yöntemleri çok fazla bulunmakta, genelde **Brute Force** kullanılır. Frekans analizi çok fazla kullanılmaz,  Cryptanalysis de aynı şekilde.

Tahmini Şifre kırma süresi değişkenlik gösterir. Brute Force saldırısının başarısı şunlara bağlıdır: şifrelenen metnin uzunluğu vb.

### Parola Saldırıları
Wordlist Oluşturma için **crunch aracı** kullanılabilir. 
```
crunch 3 3 .^, -o wordlist.txt
```
(en basit kullanımı) Baktığımızda çok fazla kullanmıyoruz ancak gerekli durumlarda ihtiyaç duyulabilir.

---
Küçük bir uygulama yaparsak: 
```
nano ktu.txt
zip -e ktu.zip ktu.txt
```
şifre girmemiz istenecek.
```
rm ktu.txt
```

Önce hash ini almamız lazım:
```
zip2john ktu.zip > ktuhash.txt
john --wordlist=/usr/share/wordlists/rockyou.txt crackmehash.txt
(bulunan wordlist path 'i) ktuhash.txt
```
ile şifre kırılmış olur
```
unzip ktu.zip
```
Şifreyi giriyoruz

---

### hashcat
``` hashcat -m 0 -a 0 md5.txt /usr/.../rockyou.txt ```
(path ı tam yazmadım) şeklinde de kırılabilir.
