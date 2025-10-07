## Virtual Memory nedir?
Bilgisayarın RAM yetersiz olduğunda disk alanında bir yer açıp orada geçici bir alan oluşturup yetersiz alanın büyük programlar için çalışmasını sağlattırır.

- **Disk Desteği**: RAM yetmezse diskten alıyor.
- **Paging**: Bellek küçük parçalara bölünerek sadece ihtiyaç duyulan parçaların RAM'de çalışması sağlanarak gereksiz kısımların diskteki virtual memory'e aktarılması sağlanır.
- **Adres Dönüşümü**: Programların kullanıldığı adresler, gerçek bellek adreslerine dönüştürülür.
- **Koruma**: Her işlemin (process) kendi sanal adres alanı vardır. Bu, işlemlerin birbirlerinin belleğine erişmesini engelleyerek bellek izolasyonu ve güvenliği sağlar.
sağlanır. Sistem performansının artırılması için kullanılan bir yöntemdir.
- **MMU (Memory Management Unit)**: Sanal adresleri fiziksel adreslere dönüştüren donanım birimidir. Paging ve koruma işlemlerini de destekler.

---

# Syns & Rsc Mng.

## Semaphore
Bir tane kaynak vardır ve bir tane thread bu kaynağa erişmek ister. Semaphore, sınırlı sayıda thread'in bu kaynağa aynı anda erişmesini sağlar. Bu şekilde, kaynak üzerinde eşzamanlı erişim kontrol altına alınır.

## Mutex
Mutex, sadece bir tane thread'in kaynağa erişmesine izin verir. Yani, bir kaynak yalnızca bir thread tarafından kullanılabilir. Bu, veri tutarlılığını sağlamak için kullanılır.

## Kernel Modu ve User Modu

### Kernel Modu
Bir driver'ın veya çekirdej seviyesinde çalışan programların çalıştığı moddur. Kullanıcı, bu modda çalışan yazılımlara kolayca erişemez, çünkü bu modda çalışan yazılımlar tüm sistemin belleğine ve donanımına erişebilir. Bu durum güvenlik endişelerine yol açabilir ve bu moddaki hatalar, sistem çökmelerine veya başka sorunlara yol açabilir; örneğin -> Cr###S####e.

### User Modu
Kullanıcı bazlı uygulamaların çalıştığı moddur. Burada çalışan yazılımlar yalnızca kendi uygulamalarına bağlı hatalarla sınırlıdır. Burada gerçekleşen bu hatalar, sistemin kendi yapısını çok fazla etkilemez.
