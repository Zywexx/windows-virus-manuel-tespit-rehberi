# Virüsler Nerede ve Nasıl Saklanır?

## Windows’ta Zararlı Yazılımların Saklanma Yöntemleri

Bu doküman, Windows işletim sistemlerinde virüslerin **en sık saklandığı dizinleri**, **kendilerini nasıl gizlediklerini** ve **manuel olarak nasıl tespit edilebileceklerini** detaylı ve profesyonel bir dille açıklar. Amaç, kullanıcıyı antivirüse bağımlı kalmadan **bilinçli analiz yapabilecek seviyeye** çıkarmaktır.

---

## İçindekiler

* Virüsler Neden Gizlenir?
* En Sık Saklanılan Dizinler
* Profesyonel Gizlenme Yöntemleri
* Kolaydan Zora Tespit Seviyeleri
* Manuel Tespit İpuçları

---

## 1. Virüsler Neden Gizlenir?

Modern zararlı yazılımlar:

* Antivirüslerden kaçmak
* Kullanıcı tarafından fark edilmemek
* Uzun süre sistemde kalmak

amacıyla **sistem davranışlarını taklit eder** ve genellikle kullanıcıların kontrol etmediği alanlara yerleşir.

---

## 2. Virüslerin En Sık Saklandığı Dizinler

### 2.1 AppData (EN SIK KULLANILAN)

```
C:\Users\KULLANICI\AppData\Roaming
C:\Users\KULLANICI\AppData\Local
C:\Users\KULLANICI\AppData\Local\Temp
```

**Neden burası seçilir?**

* Kullanıcılar bu klasörü nadiren kontrol eder
* Yazma izni vardır
* Antivirüsler bazen gözden kaçırır

**Nasıl gizlenir?**

* Rastgele isimli klasörler (`ChromeUpdate`, `SystemCache`)
* Anlamsız `.exe` isimleri

---

### 2.2 ProgramData

```
C:\ProgramData
```

**Özellikler:**

* Gizli klasördür
* Tüm kullanıcılar için geçerlidir

**Kullanım şekli:**

* Sahte servis dosyaları
* Otomatik başlatılan bileşenler

---

### 2.3 System32 (İleri Seviye)

```
C:\Windows\System32
```

**Not:**

* Acemi virüsler burada bulunmaz
* Profesyonel zararlılar **orijinal dosya isimlerini taklit eder**

Örnek:

* `svchost.exe` (orijinal)
* `svch0st.exe` (zararlı)

---

### 2.4 Startup (Başlangıç Klasörü)

```
C:\Users\KULLANICI\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup
```

* Windows açılışında otomatik çalışır
* Küçük loader dosyaları bulunur

---

### 2.5 Registry (Kayıt Defteri)

Virüslerin **kalıcılık (persistence)** sağladığı en kritik alan.

Sık kullanılan anahtarlar:

```
HKCU\Software\Microsoft\Windows\CurrentVersion\Run
HKLM\Software\Microsoft\Windows\CurrentVersion\Run
```

Buraya eklenen her değer, Windows açıldığında çalışır.

---

## 3. Profesyonel Gizlenme Yöntemleri

### 3.1 Sahte Sistem İsmi Kullanma

* `RuntimeBroker.exe`
* `WindowsUpdate.exe`

Kullanıcıya sistem dosyası hissi verir.

---

### 3.2 Parent Process Spoofing

Virüs kendini:

* `explorer.exe`
* `svchost.exe`

altından çalıştırır. Process Explorer’da dikkatli incelenmelidir.

---

### 3.3 Scheduled Task ile Gizlenme

```
schtasks
```

* Saatlik / günlük tetikleme
* Virüs silinse bile tekrar indirir

---

### 3.4 Servis Olarak Çalışma

```
sc query
```

* Windows servisi gibi davranır
* Sistem açılışında başlar

---

### 3.5 Loader + Payload Yapısı

* Küçük bir `.exe` (loader)
* Asıl zararlı dosyayı internetten çeker

Bu yapı antivirüsleri atlatmak için sık kullanılır.

---

## 4. Kolaydan Zora Tespit Seviyeleri

### Kolay

* AppData’daki anlamsız `.exe`
* Startup klasörü

### Orta

* Scheduled Tasks
* Registry Run anahtarları

### Zor (Profesyonel)

* System32 taklitleri
* Servis + loader kombinasyonu

---

## 5. Manuel Tespit İpuçları

* **Dosya yolunu her zaman kontrol et**
* Microsoft imzası yoksa şüphelen
* AppData’dan çalışan her `.exe` potansiyel risktir
* CMD + Process Explorer birlikte kullanılmalıdır

---

## 6. Sonuç

Virüsler çoğunlukla **karmaşık değil**, sadece **kontrol edilmeyen yerlerde** saklanır. Bilinçli bir kullanıcı için çoğu zararlı, manuel analizle tespit edilebilir.

> Bu doküman eğitim amaçlıdır. Yanlış müdahaleler sistem kararsızlığına yol açabilir.
