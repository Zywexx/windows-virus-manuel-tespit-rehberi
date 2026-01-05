# Windows’ta Virüs Tespiti (Manuel Analiz Rehberi)

Bu doküman, Windows işletim sisteminde **antivirüs yazılımlarına ek olarak** manuel yöntemlerle virüs, trojan, RAT, miner ve benzeri zararlı yazılımların nasıl tespit edileceğini anlatır. Rehber özellikle **Process Explorer** ve **CMD (Komut İstemi)** üzerinden yapılan kontrolleri kapsar.

> ⚠️ Bu repo bir antivirüs alternatifi değildir. Amaç, kullanıcıya **manuel analiz bilinci** kazandırmaktır.

---

## İçindekiler

* Virüs Nedir?
* Yaygın Virüs Belirtileri
* Kullanılan Araçlar
* Process Explorer ile Detaylı Analiz
* CMD Komutları ile Virüs Tespiti
* Sık Görülen Zararlı Türleri
* Şüpheli Dosya Bulunduğunda Ne Yapılmalı?
* Bu Repo Kimler İçin?

---

## 1. Virüs Nedir?

Virüsler, kullanıcının bilgisi dışında çalışan ve genellikle aşağıdaki amaçlarla kullanılan zararlı yazılımlardır:

* Bilgi hırsızlığı
* Uzaktan kontrol (RAT)
* Kripto para madenciliği (Miner)
* Reklam ve yönlendirme (Adware)

Modern zararlılar kendilerini gizlemek için **sistem dosyası gibi davranır**, imzasız çalışır ve arka planda sessizce işlem yapar.

---

## 2. Virüs Belirtileri

Aşağıdaki belirtilerden biri veya birkaçı varsa manuel kontrol önerilir:

* Bilgisayar boştayken CPU veya RAM kullanımı yüksek
* İnternet sürekli aktif (özellikle upload)
* Bilinmeyen işlemler çalışıyor
* Tarayıcı kendi kendine sekme açıyor
* Oyunlarda ani FPS düşüşleri
* Fan sürekli yüksek hızda çalışıyor
* Antivirüs devre dışı kalıyor

---

## 3. Kullanılan Araçlar

### Process Explorer

Microsoft Sysinternals tarafından geliştirilen, Görev Yöneticisi’nin gelişmiş versiyonudur.

Öne çıkan özellikler:

* Dijital imza kontrolü
* Gerçek dosya yolu görüntüleme
* DLL ve alt işlem analizi
* VirusTotal entegrasyonu

### CMD (Komut İstemi)

Windows’un yerleşik komut satırı aracıdır. Ağ bağlantıları, servisler ve başlangıç girdileri buradan analiz edilir.

---

## 4. Process Explorer ile Virüs Tespiti

https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer

### 4.1 Yönetici Olarak Çalıştırma

* `procexp64.exe` → Sağ tık → **Yönetici olarak çalıştır**
* Yönetici izni olmadan bazı sistem işlemleri görünmez

---

### 4.2 Şüpheli İşlem Kriterleri

Aşağıdaki durumlar **yüksek risk** kabul edilir:

**1. Dijital imza yok**

* `Verified Signer: Unable to Verify`

**2. Anlamsız veya taklit isimler**

* `svchosts.exe` (svchost değil)
* `servicehost.exe`
* `xj29kd.exe`

**3. Şüpheli dosya konumu**

* `AppData\\Roaming`
* `AppData\\Local\\Temp`
* `ProgramData`

Normal sistem dosyaları genellikle:

* `C:\\Windows\\System32` içindedir

---

### 4.3 İşlem Detay İncelemesi

Şüpheli işleme çift tıkla:

**Image sekmesi:**

* Dosya yolu
* İmza durumu
* Parent Process (başlatan işlem)

**Strings sekmesi (ileri seviye):**

* Discord webhook
* IP adresleri
* URL veya token değerleri

Bu veriler varsa büyük ihtimalle zararlıdır.

---

### 4.4 VirusTotal Kontrolü

Process Explorer menüsünden:

* `Options → VirusTotal.com → Check VirusTotal.com`
* `Options → VirusTotal.com → Submit Unknown Executables`

Sonuç örneği:

* `0/70` → Temiz
* `5/70+` → Şüpheli / Zararlı

---

## 5. CMD Komutları ile Virüs Tespiti

### 5.1 Aktif Ağ Bağlantıları

```
netstat -ano
```

Kontrol edilmesi gerekenler:

* Sürekli açık **ESTABLISHED** bağlantılar
* Bilinmeyen dış IP adresleri

PID ile işlem eşleştirme:

* PID → Process Explorer’da kontrol edilir

---

### 5.2 Çalışan Servisler

```
sc query state= all
```

* Açıklaması olmayan
* Anlamsız isimli
* AppData’dan çalışan servisler risklidir

---

### 5.3 Başlangıç Programları

```
wmic startup get caption,command
```

* AppData veya Temp dizininden çalışanlar şüphelidir

---

### 5.4 Görev Zamanlayıcı Kontrolü

```
schtasks
```

Virüsler genellikle kendini saatlik/günlük çalışacak şekilde buraya ekler.

---

## 6. Sık Görülen Zararlı Türleri

### Miner (Kripto Madenci)

* CPU/GPU sürekli %70–100
* Oyunlarda FPS düşüşü
* Sürekli çalışan işlem

### RAT / Trojan

* Sürekli internet bağlantısı
* Uzaktan kontrol
* Discord / Telegram altyapısı kullanımı

### Adware

* Tarayıcı reklamları
* Bilinmeyen eklentiler

---

## 7. Şüpheli Dosya Bulunduğunda Ne Yapılmalı?

❌ Direkt silme (kendini geri yükleyebilir)

✅ Önerilen adımlar:

1. İnternet bağlantısını kes
2. Process Explorer’dan işlemi **Suspend** et
3. Dosya yolunu not al
4. Güvenli Mod’da sil
5. Windows Defender Offline Scan çalıştır

---

## 8. Bu Repo Kimler İçin?

* Oyun sunucusu yöneticileri (FiveM, MTA, vb.)
* Oyuncular (FPS düşüşü / cheat kontrolü)
* Discord bot geliştiricileri
* Anti-cheat veya güvenlik projesi geliştirmek isteyenler

---

## 9. Lisans ve Sorumluluk Reddi

Bu doküman yalnızca **eğitim amaçlıdır**. Yanlış kullanım sonucu oluşabilecek veri kayıplarından kullanıcı sorumludur.
