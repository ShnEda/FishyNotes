# Daemon & Registry Keys
Daemon, Unix tabanlı sistemlerde sürekli çalışan bir *arka plan süreci*dir ve genellikle sistem açıldığında başlar. Günlük kaydı yapma isteklerini işleme ve yazıcıları yönetme gibi görevleri yerine getirir ve kullanıcı ile doğrudan etkileşimde bulunmaz.

**Reg Keys**, Wnd'de OS ve uygulamalar için *düşük seviyeli ayarların* saklandığı hiyerarşik veri tabanıdır. Sistem donanımı, yazılım ayarları, kullanıcı tercihleri ve servis yapılandırmaları gibi birçok bilgiyi içerir.

**RegCreateKeyExA**:Belirtilen kayıt defteri anahtarını oluşturur. Eğer anahtar zaten mevcutsa, fonksiyon onu açar. Anahtar isimlerinin büyük/küçük harf duyarlı olmadığını unutmayın.

## HKEY Nedir?

**HKEY (Handle to Registry Key)**, Windows Registry'de bir anahtara erişim sağlayan **handle** (tanımlayıcı) türüdür. Registry üzerinde işlem yapmak için mutlaka bir HKEY değişkeni kullanılır.

```c
HKEY hKey;  // Registry handle tanımlaması
```

---

## Registry Writer: Parametre Yapısı

Windows API kullanarak registry'ye veri yazarken **key**, **value** ve **subkey** yapıları parametre olarak fonksiyonlara geçilir.

### Parametre Yapısı ve İlişkileri:

**1. Ana Anahtar (Root Key):**
```c
HKEY_CURRENT_USER  // Kullanıcı bazlı ayarlar
HKEY_LOCAL_MACHINE // Sistem bazlı ayarlar
```

**2. Subkey (Alt Anahtar) Yolu:**
```c
"Software\\MyApp\\Config"  // Hiyerarşik yol yapısı
```

**3. Value (Değer) İsmi:**
```c
"Username"    // Anahtar içindeki değer adı
"Timeout"     // Başka bir değer adı
```

**4. Value Data (Değer Verisi):**
```c
"admin"       // String veri
300           // DWORD veri
```

### Pratik Gösterim:

```
Registry Yapısı:
HKEY_CURRENT_USER                    ← Ana anahtar (parametre 1)
    └── Software                      
        └── MyApp                     
            └── Config                ← Subkey yolu (parametre 2)
                ├── Username = "admin"    ← Value name + data (parametre 3,4)
                └── Timeout = 300         ← Value name + data (parametre 3,4)
```

---

## Windows API ile Parametre Kullanımı

### RegSetValueExA Fonksiyonu:

```c
RegSetValueExA(
    hKey,              // Parametre 1: HKEY handle
    "Username",        // Parametre 2: Value ismi (key içindeki değer)
    0,                 // Parametre 3: Reserved
    REG_SZ,           // Parametre 4: Veri tipi
    (BYTE*)data,      // Parametre 5: Yazılacak veri
    dataSize          // Parametre 6: Veri boyutu
);
```

### Parametre Grupları:

**Hedef Tanımlama Parametreleri:**
- `hKey`: Hangi anahtara yazılacak?
- `"Username"`: Hangi değer yazılacak?

**Veri Tanımlama Parametreleri:**
- `REG_SZ`: Ne tür veri? (String, DWORD, Binary)
- `(BYTE*)data`: Gerçek veri nedir?
- `dataSize`: Verinin boyutu ne kadar?

---

## Key, Value, Subkey İlişkisi

### Kavramsal Yapı:

```
Key (Anahtar):
    └── Registry'deki bir konum (klasör gibi)
    
Subkey (Alt Anahtar):
    └── Ana anahtarın altındaki yol (alt klasör)
    
Value (Değer):
    └── Anahtar içindeki veri (dosya gibi)
```

### Örnek Senaryo:

```c
// Hedef: HKCU\Software\MyApp altında "Version" değeri oluştur

RegSetValueExA(
    hKey,                    // HKCU\Software\MyApp handle'ı
    "Version",               // Value name (değer ismi)
    0,
    REG_SZ,                 // String tipi
    (BYTE*)"1.0.5",        // Value data (değer verisi)
    6                       // Boyut
);
```

**Sonuç Registry Yapısı:**
```
HKEY_CURRENT_USER
    └── Software
        └── MyApp              ← Key (ana konum)
            └── Version = "1.0.5"  ← Value (veri)
```

---

## Veri Tipleri Parametreleri

**REG_SZ (String):**
```c
const char* username = "admin";
RegSetValueExA(hKey, "User", 0, REG_SZ, 
               (BYTE*)username, strlen(username) + 1);
```

**REG_DWORD (32-bit Sayı):**
```c
DWORD timeout = 300;
RegSetValueExA(hKey, "Timeout", 0, REG_DWORD, 
               (BYTE*)&timeout, sizeof(DWORD));
```

**REG_BINARY (Ham Veri):**
```c
BYTE key[16] = {0x1A, 0x2B, 0x3C, ...};
RegSetValueExA(hKey, "EncKey", 0, REG_BINARY, 
               key, sizeof(key));
```

---

## Özet: Parametre Akışı

```
Windows API Registry Writer Akışı:

HKEY handle -> Hangi anahtara?
                    ↓
Subkey yolu -> Hangi alt konuma?
                    ↓
Value name  -> Hangi değer adıyla?
                    ↓
Value type  -> Ne tür veri? (REG_SZ, REG_DWORD)
                    ↓
Value data  -> Gerçek veri nedir?
                    ↓
Registry'ye yazıldı ✓
```

Bu yapı sayesinde Windows API, esnek ve hiyerarşik bir şekilde registry'ye parametre bazlı veri yazma imkanı sağlar.
