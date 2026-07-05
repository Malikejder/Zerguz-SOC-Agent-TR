# 🛡️ Zerguz SOCAgent

> **Python ile geliştirilmiş, NIDS (Network Intrusion Detection System) ve EDR (Endpoint Detection & Response) özelliklerini tek bir araçta birleştiren hafif bir SOC izleme uygulaması.**

Zerguz SOCAgent, Blue Team çalışmaları, SOC laboratuvarları ve siber güvenlik eğitimleri için geliştirilmiş gerçek zamanlı bir güvenlik izleme aracıdır.

Uygulama yalnızca ağ trafiğini analiz etmekle kalmaz; aynı zamanda sistem üzerinde çalışan süreçleri de sürekli takip ederek şüpheli davranışları tespit eder, alarm üretir ve adli analiz (forensic) için kanıt toplar.

---

# 🚀 Özellikler

## 🌐 NIDS (Network Intrusion Detection System)

Scapy kullanılarak gerçek zamanlı ağ trafiği analiz edilir ve aşağıdaki saldırılar tespit edilir:

* TCP Port Tarama (Port Scan)
* UDP Port Tarama
* ICMP Flood / Ping Sweep
* DNS Tunneling Şüphesi
* Aşırı Yoğun DNS Trafiği
* Anormal Uzunlukta DNS Sorguları

Bir saldırı tespit edildiğinde sistem otomatik olarak:

* Gerçek zamanlı alarm üretir.
* İlgili paketleri PCAP formatında kaydeder.
* JSON formatında olay kaydı oluşturur.
* Olayın ayrıntılarını raporlar.

---

## 🖥️ EDR (Endpoint Detection & Response)

SOCAgent yalnızca ağ trafiğini izlemez.

Aynı zamanda sistem üzerinde çalışan süreçleri analiz ederek şüpheli davranışları tespit eder.

Mevcut tespit yetenekleri:

* Şüpheli dizinlerden çalışan uygulamalar
* Web sunucusu tarafından başlatılan Shell süreçleri
* Olası WebShell davranışları
* Sürekli çalışan süreç izleme

Desteklenen web sunucuları:

* Apache
* Nginx
* HTTPD
* Tomcat
* IIS (w3wp)

İzlenen komut satırı uygulamaları:

* cmd.exe
* PowerShell
* Bash
* Sh
* Zsh
* Dash
* Ash

---

# 📦 Kanıt Toplama (Evidence Collection)

Bir ağ saldırısı tespit edildiğinde SOCAgent otomatik olarak aşağıdaki bilgileri kaydeder.

## PCAP Dosyası

Saldırıya ait paketler otomatik olarak kaydedilir.

Örnek:

```text
zerguz_evidence_PORT_SCAN_192.168.1.15_20260705_213500.pcap
```

## JSON Alarm Kaydı

Her alarm aşağıdaki bilgileri içerir.

* Tarih
* Saat
* Tespit Modülü
* Saldırı Türü
* Kaynak IP
* Hedef IP
* Açıklama
* PCAP Kanıtı

Bu kayıtlar SIEM sistemlerine veya diğer analiz araçlarına kolayca aktarılabilir.

---

# 🔍 Desteklenen Tespitler

## Ağ Güvenliği

* Port Scan Detection
* ICMP Flood Detection
* Ping Sweep Detection
* DNS Tunneling Detection
* DNS Frekans Analizi
* DNS Uzunluk Analizi
* Paket Geçmişi (Packet History)
* Alarm Cooldown Mekanizması

## Uç Nokta Güvenliği

* Şüpheli Dizin Analizi
* Parent Process Analizi
* WebShell Davranışı Tespiti
* Canlı Süreç İzleme

---

# 📂 Proje Yapısı

```text
Zerguz-SOCAgent-TR.py
zerguz_soc_alerts.json
zerguz_evidence_*.pcap
```

---

# 🛠️ Kullanılan Teknolojiler

* Python 3
* Scapy
* psutil
* Colorama
* JSON
* Multithreading
* Packet Capture (PCAP)

---

# ⚙️ Kurulum

Projeyi indiriniz.

```bash
git clone https://github.com/Malikejder/Zerguz-SOCAgent-TR.git
cd Zerguz-SOCAgent
```

Gerekli kütüphaneleri yükleyiniz.

```bash
pip install scapy psutil colorama
```

Linux kullanıcıları ayrıca aşağıdaki pakete ihtiyaç duyabilir.

```bash
sudo apt install libpcap-dev
```

---

# ▶️ Kullanım

Linux

```bash
sudo python3 Zerguz-SOCAgent-TR.py
```

Windows (Yönetici Yetkisi)

```bash
python Zerguz-SOCAgent-TR.py
```

---

# 📋 Örnek Alarm

### NIDS

```text
[ALARM - NIDS]

Saldırı Türü : PORT_SCAN_DETECTED

Kaynak IP : 192.168.1.50

Hedef IP : 192.168.1.10

PCAP Kanıtı Kaydedildi
```

### EDR

```text
[ALARM - EDR]

Saldırı Türü : WEBSHELL_ANOMALY_DETECTED

Process : cmd.exe

Parent : w3wp.exe
```

---

# 📁 Oluşturulan Dosyalar

## JSON Alarm Dosyası

```text
zerguz_soc_alerts.json
```

Tespit edilen tüm olaylar JSON formatında saklanır.

## PCAP Kanıt Dosyaları

```text
zerguz_evidence_<attack>_<ip>_<timestamp>.pcap
```

Her saldırı için ağ trafiğinin kanıtı ayrı olarak kaydedilir.

---

# 🎯 Projenin Amacı

Bu proje aşağıdaki alanlarda pratik kazanmak amacıyla geliştirilmiştir.

* SOC Operasyonları
* Blue Team Çalışmaları
* Ağ Güvenliği İzleme
* Endpoint Detection & Response (EDR)
* Olay Müdahalesi (Incident Response)
* Packet Analysis
* Python ile Güvenlik Otomasyonu
* Dijital Delil Toplama (Forensics)
* Siber Tehdit Analizi

---

# ⚠️ Yasal Uyarı

Bu proje yalnızca eğitim, laboratuvar ortamları, Blue Team çalışmaları ve yetkili güvenlik testleri amacıyla geliştirilmiştir.

Yetkisiz sistemlerde veya izin alınmamış ağlarda kullanılması önerilmez.

Kullanımdan doğabilecek tüm sorumluluk kullanıcıya aittir.

---

# 👨‍💻 Geliştirici

**Malikejder Durgun**

Bilgisayar Programcısı | Siber Güvenlik | Blue Team | SOC Analisti | Python Güvenlik Araçları Geliştiricisi
