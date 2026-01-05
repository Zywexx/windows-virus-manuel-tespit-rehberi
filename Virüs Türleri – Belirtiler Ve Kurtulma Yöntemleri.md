# Windows’ta Virüs Türleri

## Belirtiler ve Kurtulma Yöntemleri

Bu doküman, Windows işletim sistemlerinde karşılaşılan **tüm yaygın zararlı yazılım türlerini**, bu zararlıların **belirtilerini** ve **nasıl temizlenebileceklerini** detaylı ve anlaşılır şekilde açıklar. Bu rehber, manuel analiz yapan kullanıcılar ve güvenlik projeleri için referans olarak hazırlanmıştır.

---

## İçindekiler

* Zararlı Yazılım Nedir?
* Virüs Türleri ve Belirtileri
* Kurtulma ve Temizleme Yöntemleri
* Hangi Durumda Format Atılmalı?

---

## 1. Zararlı Yazılım (Malware) Nedir?

Zararlı yazılım; kullanıcının bilgisi dışında çalışan, sisteme zarar veren veya kullanıcıdan fayda sağlayan tüm yazılımların genel adıdır.

Amaçları:

* Bilgi çalmak
* Sistemi uzaktan kontrol etmek
* Donanımı izinsiz kullanmak
* Reklam ve yönlendirme yapmak

---

## 2. Virüs Türleri ve Belirtileri

### 2.1 Klasik Virüs

**Tanım:**
Dosyalara bulaşarak yayılan zararlılardır.

**Belirtiler:**

* Dosyalar bozulur veya silinir
* Programlar açılmaz
* Sistem hataları artar

**Kurtulma:**

* Windows Defender Tam Tarama
* Güvenli Mod’da antivirüs taraması
* Sistem geri yükleme

---

### 2.2 Trojan (Truva Atı)

**Tanım:**
Masum program gibi görünen ama arka planda zararlı işlem yapan yazılımlar.

**Belirtiler:**

* Bilinmeyen işlemler çalışır
* İnternet trafiği artar
* Sistem yavaşlar

**Kurtulma:**

* Process Explorer ile işlem tespiti
* Malwarebytes taraması
* Şüpheli dosyaların silinmesi

---

### 2.3 RAT (Remote Access Trojan)

**Tanım:**
Sistemi uzaktan kontrol etmeye yarayan zararlılar.

**Belirtiler:**

* Fare kendi kendine hareket eder
* Kamera / mikrofon ışığı yanar
* Sürekli aktif internet bağlantısı

**Kurtulma:**

* İnternet bağlantısını kes
* Güvenli Mod
* Defender Offline Scan
* Gerekirse format

---

### 2.4 Keylogger

**Tanım:**
Klavye girdilerini kaydeden zararlılar.

**Belirtiler:**

* Hesap çalınmaları
* Şifrelerin ele geçirilmesi
* Arka planda gizli çalışan servisler

**Kurtulma:**

* Tüm şifreleri başka cihazdan değiştir
* Tam sistem taraması
* Temiz kurulum önerilir

---

### 2.5 Crypto Miner (Madenci Virüs)

**Tanım:**
CPU/GPU kullanarak kripto para kazanır.

**Belirtiler:**

* CPU/GPU sürekli yüksek
* Fan sesi artar
* Oyunlarda FPS düşüşü

**Kurtulma:**

* Process Explorer ile tespit
* Görev zamanlayıcı temizliği
* Antivirüs + manuel silme

---

### 2.6 Adware

**Tanım:**
Reklam gösteren ve yönlendirme yapan yazılımlar.

**Belirtiler:**

* Tarayıcıda reklamlar
* Yeni sekmeler açılır
* Ana sayfa değişir

**Kurtulma:**

* Tarayıcı sıfırlama
* Eklentileri kaldırma
* AdwCleaner kullanımı

---

### 2.7 Spyware

**Tanım:**
Kullanıcıyı izleyen zararlılar.

**Belirtiler:**

* Veri sızıntısı
* Sistem performans düşüşü
* Bilinmeyen servisler

**Kurtulma:**

* Güvenli Mod
* Anti-spyware taraması
* Gerekirse format

---

### 2.8 Worm (Solucan)

**Tanım:**
Ağ üzerinden kendini yayan zararlılar.

**Belirtiler:**

* Ağ trafiği aşırı artar
* Diğer bilgisayarlara bulaşma

**Kurtulma:**

* Ağ bağlantısını kes
* Güvenlik güncellemeleri
* Antivirüs taraması

---

## 3. Genel Kurtulma Yöntemleri

Önerilen sıra:

1. İnterneti kes
2. Güvenli Mod’a gir
3. Antivirüs tam tarama
4. Process Explorer manuel kontrol
5. CMD ile başlangıç ve servis kontrolü

---

## 4. Ne Zaman Format Atılmalı?

Aşağıdaki durumlarda **temiz Windows kurulumu** önerilir:

* RAT veya keylogger tespit edildiyse
* Sistem dosyaları bozulduysa
* Virüs sürekli geri geliyorsa
* Banka / e-posta hesapları çalındıysa

---

## 5. Sonuç

Bu rehber, zararlı yazılımları tanımak ve doğru tepki vermek için hazırlanmıştır. Bilinçli kullanıcı, en güçlü güvenlik katmanıdır.

> Eğitim amaçlıdır. Yanlış işlemlerden kullanıcı sorumludur.
