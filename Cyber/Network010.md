# Kablosuz Network Standartları

## 802.11

Günümüzde kullandığımız cihazlar bunu kullanıyor. `802.11n` çok kullanılan, `802.11ax` ile biten de yeni çıkmış.

**802.11n:** 2.4 GHz ve 5 GHz frekans bantlarını destekler. Maksimum hız: 600 Mbps.

**802.11ac:** Sadece 5 GHz bandında çalışır, maksimum hız: 1.3 Gbps.

**802.11ax (Wi-Fi 6):** En yeni standart, hem 2.4 GHz hem 5 GHz bandında çalışır. Daha yüksek hız ve kapasite sunar.

---

# Kablosuz Ağ Kimlik Doğrulama Yöntemleri

**WEP:** Kırmak çok kolay, çoktandır kullanılmıyor.

**WPA:** WEP zayıflıklarından dolayı geliştirilmiş bir algoritma, 48 bitlik bir algoritma kullanılmakta. Biraz uğraştırıcı kırması.

**WPA2:** Günümüzde en çok kullanılanlardan. Biraz daha kırmak için uğraşılır.

**WPA3:** Yeni çıkmış. WPA3, SAE (Simultaneous Authentication of Equals) kullanarak brute force saldırılara karşı daha dayanıklıdır.

Günümüzde çok kullanılmasa da başka algoritmalar: TKIP, LEAP

---

# Terminoloji

**WarWalking:** Çevrede yaya olarak gezerek kablosuz ağları tespit etmek.

**WarDriving:** Araba ile çevredeki kablosuz ağları tespit etmek.

**WarFlying:** Bunun uçakla yapılan hali.

**WarChalking:** Kablosuz ağ olan bölgeleri işaretlemek.

**Blue Jacking:** Bluetooth teknolojisi kullanılarak telefonlara sızmak.

---

# DeAuth Attack

Deauthentication saldırısı, kablosuz ağ kullanıcılarını geçici olarak bağlantıdan düşürmek için kullanılır. Saldırgan, hedef cihaz ve kablosuz erişim noktası arasında "Disconnect" komutları gönderir. Hedef cihaz, yeniden bağlanmaya çalışırken saldırgan tarafından ele geçirilebilir.
