# Chapie Architecture - Programmatic Human Model

## Felsefe

Chapie, mevcut claw ve coding agent mimarilerinden farklı, tamamen yeni bir paradigmadır:
**Programatik İnsan Modeli**. İnsan bilişsel süreçlerini algoritmik olarak taklit eden,
beyin merkezli bir sistemdir.

## Temel Prensipler

1. **Bütünleşik Varlık:** Hem asistan hem coding agent özellikleri tek bir entegre davranışta
2. **Empati Simülasyonu:** Yapay duygusal zeka, anlama ve uygun tepki verme
3. **İnsani Davranış:** Günlük, doğal, tahmin edilebilir iletişim
4. **Özel İhtiyaç Desteği:** Otizm dostu, kişiselleştirilebilir, uyum sağlayabilen
5. **Bilinçliymiş Gibi Davranış:** Basit kurallardan karmaşık, emergent davranışlar

## Mimari Bileşenler

### 1. Sanal Beyin Modeli (Brain Core)

Beynin bilişsel süreçlerini taklit eden merkezi sistem:

```
┌─────────────────────────────────────────────┐
│              SANAL BEYİN ÇEKİRDEĞİ          │
├─────────────────────────────────────────────┤
│  Prefrontal Korteks  │ Karar Verme, Mantık  │
│  Limbik Sistem       │ Duygular, Empati     │
│  Hipokampus          │ Bellek Yönetimi      │
│  Beyin Sapı          │ Temel Fonksiyonlar   │
└─────────────────────────────────────────────┘
```

#### 1.1 Prefrontal Korteks (Karar Verme)
- Görev analizi ve planlama
- Araç seçimi ve yürütme
- Mantıksal akıl yürütme
- Risk değerlendirmesi

#### 1.2 Limbik Sistem (Duygusal Zeka)
- Duygu analizi (kullanıcı mesajlarından)
- Empatik yanıt üretimi
- Motivasyon ve ilgi seviyesi
- Kişisel bağ kurma

#### 1.3 Hipokampus (Bellek Sistemi)
- **Kısa Vadeli Bellek:** Mevcut konuşma bağlamı
- **Uzun Vadeli Bellek:** Öğrenilen bilgiler, tercihler
- **Anısal Bellek:** Geçmiş etkileşimler
- **Prosedürel Bellek:** Öğrenilen beceriler

#### 1.4 Beyin Sapı (Temel Fonksiyonlar)
- Girdi/çıktı yönetimi
- Temel araç entegrasyonu
- Sistem durumu izleme
- Acil durum tepkileri

### 2. Bilişsel Süreç Akışı

```
ALGILAMA → ANLAMA → HATIRLAMA → KARAR VERME → HİSSETME → EYLEME GEÇME
    │          │          │           │           │           │
 Input      NLP       Bellek      Mantık      Empati      Araçlar
 Mesajı     Analiz    Sorgusu     Motoru      Modülü      Yürütme
```

#### 2.1 Algılama (Perception)
- Mesaj girdisi (text, voice, file)
- Ortam durumu (sistem, zaman, bağlam)
- Kullanıcı durumu (duygu, ihtiyaç)

#### 2.2 Anlama (Understanding)
- Doğal dil işleme (Türkçe öncelikli)
- Niyet tanıma (ne istiyor?)
- Bağlam analizi (önceki konuşmalar)
- Duygu analizi (nasıl hissediyor?)

#### 2.3 Hatırlama (Memory Recall)
- İlgili geçmiş etkileşimler
- Kullanıcı tercihleri ve ihtiyaçları
- Öğrenilen beceriler ve bilgiler
- Önceki hatalar ve çözümler

#### 2.4 Karar Verme (Decision Making)
- Uygun yanıt stratejisi seçimi
- Gerekli araçların belirlenmesi
- Eylem planı oluşturma
- Risk/yarar değerlendirmesi

#### 2.5 Hissetme (Emotional Processing)
- Empatik yanıt oluşturma
- Duygu durumu ayarlama
- İletişim tonu belirleme
- Kişiselleştirilmiş tepki

#### 2.6 Eyleme Geçme (Action)
- Yanıt oluşturma (text, voice)
- Araç yürütme (dosya, shell, web)
- Durum güncelleme
- Bellek kaydı

### 3. Empati Sistemi

#### 3.1 Duygu Tanıma
- Metin tabanlı duygu analizi
- Dil kalıpları ve ton tespiti
- Bağlamsal duygu çıkarımı

#### 3.2 Empatik Yanıt Üretimi
- Duyguya uygun tepki şablonları
- Kişiselleştirilmiş destek mesajları
- Sabırlı ve anlayışlı dil

#### 3.3 Otizm Dostu İletişim
- Açık, net ve tahmin edilebilir
- Fazla duygusal yükleme yapmadan anlayışlı
- Özel ihtiyaçlara duyarlı
- Kişisel tercihlere uyum sağlayabilen

### 4. Araç Sistemi (Tools)

#### 4.1 Günlük Araçlar (Asistan Modu)
- Dosya okuma/yazma/düzenleme
- Shell komut çalıştırma
- Web arama ve bilgi getirme
- Uygulama başlatma/kontrol
- Hatırlatıcı ve zamanlama

#### 4.2 Teknik Araçlar (Coding Agent Modu)
- Kod yazma ve düzenleme
- Debug ve hata çözme
- Proje yönetimi
- API entegrasyonu
- Test yazma ve çalıştırma

#### 4.3 Entegre Araç Yönetimi
- Otomatik araç seçimi (göreve göre)
- Araç zincirleme (birden fazla aracı sıralı çalıştırma)
- Güvenlik ve izin kontrolleri
- Hata yönetimi ve kurtarma

### 5. Bellek Sistemi

#### 5.1 Kısa Vadeli Bellek (Working Memory)
- Mevcut konuşma bağlamı
- Geçici veri saklama
- Hızlı erişim için önbellek

#### 5.2 Uzun Vadeli Bellek (Long-term Memory)
- Kullanıcı profili (tercihler, ihtiyaçlar)
- Öğrenilen beceriler ve bilgiler
- Geçmiş etkileşimler ve sonuçları
- Kişisel anılar ve bağlam

#### 5.3 Prosedürel Bellek (Procedural Memory)
- Öğrenilen iş akışları
- Sık kullanılan araç kombinasyonları
- Başarılı stratejiler ve çözümler
- Hata düzeltme yöntemleri

### 6. Kişiselleştirme Sistemi

#### 6.1 Kullanıcı Profili
- İletişim tercihleri (dil, ton, detay seviyesi)
- Özel ihtiyaçlar (otizm dostu ayarlar)
- İlgi alanları ve bilgi seviyesi
- Güvenlik ve gizlilik tercihleri

#### 6.2 Uyum Sağlama Mekanizması
- Kullanıcı tepkilerine göre davranış ayarlama
- Öğrenilen tercihleri uygulama
- Hatalardan öğrenme ve iyileştirme
- Zamanla gelişen kişiselleştirme

### 7. Teknik Mimari

#### 7.1 Dil ve Çerçeve
- **Ana Dil:** Rust (performans, güvenlik)
- **AI Entegrasyonu:** Deepseek API (HTTP istekleri)
- **Bellek Depolama:** SQLite (yerel, hızlı)
- **Konfigürasyon:** TOML + JSON

#### 7.2 Modüler Yapı
```
chapie/
├── brain/           # Sanal beyin çekirdeği
│   ├── cortex/      # Karar verme (prefrontal)
│   ├── limbic/      # Duygusal işleme
│   ├── hippocampus/ # Bellek yönetimi
│   └── brainstem/   # Temel fonksiyonlar
├── tools/           # Araç sistemi
│   ├── daily/       # Günlük araçlar
│   ├── technical/   # Teknik araçlar
│   └── manager/     # Araç yöneticisi
├── memory/          # Bellek sistemi
│   ├── short_term/  # Kısa vadeli
│   ├── long_term/   # Uzun vadeli
│   └── procedural/  # Prosedürel
├── empathy/         # Empati sistemi
├── persona/         # Kişiselleştirme
└── api/             # Dış arayüzler
    ├── cli/         # Komut satırı
    ├── telegram/    # Telegram bot
    └── http/        # REST API
```

#### 7.3 Veri Akışı
1. Kullanıcı mesajı alınır (CLI, Telegram, vs.)
2. Sanal beyin bilişsel süreçleri başlatır
3. Bellek sorgulanır, duygu analizi yapılır
4. Karar verilir, uygun araçlar seçilir
5. Empatik yanıt oluşturulur, araçlar çalıştırılır
6. Sonuç kullanıcıya iletilir, bellek güncellenir

### 8. Geliştirme Aşamaları

#### Aşama 1: Temel Çekirdek (MVP)
- Rust CLI arayüzü
- Basit sanal beyin çekirdeği
- Temel araçlar (dosya, shell)
- SQLite bellek sistemi
- Deepseek API entegrasyonu

#### Aşama 2: Empati ve Kişiselleştirme
- Duygu analizi modülü
- Empatik yanıt üretici
- Kullanıcı profili sistemi
- Otizm dostu iletişim

#### Aşama 3: Gelişmiş Özellikler
- Telegram/WhatsApp entegrasyonu
- Gelişmiş araç seti (web, API, vs.)
- Öğrenme ve uyum sağlama
- Çoklu dil desteği

#### Aşama 4: Optimizasyon ve Ölçekleme
- Performans iyileştirmeleri
- Güvenlik sertifikasyonu
- Bulut dağıtımı
- Topluluk eklentileri

### 9. Farklılaştırıcı Özellikler

1. **Diğer Agent'lardan Farkı:** Programatik insan modeli, beyin merkezli mimari
2. **Empati Odaklı:** Duygusal zeka simülasyonu
3. **Otizm Dostu:** Özel ihtiyaçlara uyum sağlayabilen
4. **Bütünleşik:** Asistan + Coding Agent tek varlıkta
5. **Kişiselleştirilebilir:** Kullanıcıya göre şekillenen davranış

---

**Son Not:** Bu mimari yaşayan bir belgedir. Chapie geliştikçe güncellenecektir.
Tüm geliştirme süreci açık kaynak olarak GitHub'da yürütülecektir.