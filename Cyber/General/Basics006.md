## Virtual Memory nedir?
Bilgisayarın RAM yetersiz olduğunda disk alanında bir yer açıp orada geçici bir alan oluşturup yetersiz alanın büyük programlar için çalışmasını sağlattırır.

- **Disk Desteği**: RAM yetmezse diskten alıyor.
- **Paging**: Bellek küçük parçalara bölünerek sadece ihtiyaç duyulan parçaların RAM'de çalışması sağlanarak gereksiz kısımların diskteki virtual memory'e aktarılması sağlanır.
- **Adres Dönüşümü**: Programların kullanıldığı adresler, gerçek bellek adreslerine dönüştürülür.
- **Koruma**: Her işlemin (process) kendi sanal adres alanı vardır. Bu, işlemlerin birbirlerinin belleğine erişmesini engelleyerek bellek izolasyonu ve güvenliği sağlar.
sağlanır. Sistem performansının artırılması için kullanılan bir yöntemdir.
- **MMU (Memory Management Unit)**: Sanal adresleri fiziksel adreslere dönüştüren donanım birimidir. Paging ve koruma işlemlerini de destekler.
