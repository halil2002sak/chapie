# Chapie Usage - Kullanım Kılavuzu

## Genel Bakış

Chapie, programatik insan modeli üzerine kurulu, empati odaklı bir AI asistan ve coding agent'tır.
Bu kılavuz, Chapie'yi kurma, yapılandırma ve kullanma adımlarını açıklar.

## Hızlı Başlangıç

### 1. Ön Koşullar

Chapie'yi kullanmak için aşağıdaki yazılımların sisteminizde kurulu olması gerekmektedir:

- **Rust:** 1.70+ (https://rustup.rs/)
- **Git:** 2.30+
- **SQLite:** 3.35+ (genellikle sistemde hazırdır)
- **Deepseek API Anahtarı:** https://platform.deepseek.com/api_keys

### 2. Kurulum

#### GitHub'dan Clone Etme
```bash
# Chapie repository'sini klonla
git clone https://github.com/halil2002sak/chapie.git
cd chapie

# Bağımlılıkları yükle
cargo build --release
```

#### Cargo ile Kurulum (Gelecek Sürümlerde)
```bash
cargo install chapie
```

### 3. Yapılandırma

#### API Anahtarını Ayarlama
```bash
# Deepseek API anahtarını ortam değişkeni olarak ayarla
export DEEPSEEK_API_KEY="sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"

# Veya konfigürasyon dosyasına ekle
mkdir -p ~/.chapie
echo 'DEEPSEEK_API_KEY="sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"' > ~/.chapie/.env
```

#### Konfigürasyon Dosyası
`~/.chapie/config.toml` dosyasını oluşturun:

```toml
[user]
name = "Halil"
language = "tr"
timezone = "Europe/Istanbul"

[preferences]
communication_style = "autism_friendly"
detail_level = "normal"
response_speed = "balanced"
autism_support = true

[api]
deepseek_base_url = "https://api.deepseek.com"
timeout_seconds = 30
max_tokens = 4096

[tools]
default_permissions = ["read_file", "execute_shell_low_risk"]
require_approval_for = ["delete_file", "execute_shell_high_risk"]

[memory]
short_term_capacity = 100
long_term_persistence = true
auto_cleanup_days = 30
```

### 4. Başlatma

```bash
# Chapie'yi başlat
chapie start

# Veya interaktif modda başlat
chapie interactive

# Veya tek seferlik komut çalıştır
chapie ask "Merhaba Chapie!"
```

## Temel Kullanım

### CLI Komutları

#### Yardım ve Bilgi
```bash
# Genel yardım
chapie --help

# Komut yardımı
chapie ask --help

# Versiyon bilgisi
chapie --version

# Sistem durumu
chapie status
```

#### Sohbet ve Soru-Cevap
```bash
# Basit soru sorma
chapie ask "Bugün hava durumu nasıl?"

# Dosya hakkında soru sorma
chapie ask "README.md dosyasında ne yazıyor?"

# Kod hakkında soru sorma
chapie ask "Bu Rust kodundaki hatayı bul"
```

#### Dosya İşlemleri
```bash
# Dosya okuma
chapie file read /path/to/file.txt

# Dosya yazma
chapie file write /path/to/file.txt "İçerik"

# Dosya düzenleme
chapie file edit /path/to/file.txt "Yeni içerik"

# Dosya listeleme
chapie file list /path/to/directory

# Dosya arama
chapie file search "pattern" /path/to/directory
```

#### Shell Komutları
```bash
# Shell komutu çalıştırma
chapie shell "ls -la"

# Komut çıktısını analiz etme
chapie shell "ps aux" --analyze

# Güvenli modda komut çalıştırma
chapie shell "rm -rf /" --safe-mode
```

#### Bellek İşlemleri
```bash
# Bellek durumunu görüntüle
chapie memory status

# Bellek kayıtlarını listele
chapie memory list --type long_term --limit 10

# Bellek kaydı ekle
chapie memory add "Önemli not: Yarın toplantı var"

# Bellek kaydı sil
chapie memory delete memory_id

# Bellek temizle
chapie memory cleanup --days-old 30
```

#### Araç Yönetimi
```bash
# Kullanılabilir araçları listele
chapie tools list

# Araç bilgisi görüntüle
chapie tools info file_read

# Araç çalıştır
chapie tools execute file_read --path /path/to/file.txt

# Özel araç kaydet
chapie tools register --name custom_tool --handler /path/to/handler.py
```

#### Profil Yönetimi
```bash
# Profil bilgisi görüntüle
chapie profile show

# Profil güncelle
chapie profile update --detail-level high --response-speed fast

# Tercihleri sıfırla
chapie profile reset

# Profil dışa aktar
chapie profile export --format json
```

### İnteraktif Mod

```bash
# İnteraktif modda başlat
chapie interactive

# İnteraktif mod komutları:
#   /help       - Yardım göster
#   /exit       - Çıkış yap
#   /clear      - Ekranı temizle
#   /status     - Sistem durumu
#   /memory     - Bellek yönetimi
#   /tools      - Araç listesi
#   /profile    - Profil ayarları
```

## Gelişmiş Kullanım

### Otizm Dostu Mod

Chapie, otizmli kullanıcılar için özel iletişim modları sunar:

```bash
# Otizm dostu modda başlat
chapie start --autism-friendly

# Açık ve net iletişim
chapie ask "Bana açık ve net şekilde anlat" --explicit

# Tahmin edilebilir yanıtlar
chapie ask "Soru" --predictable

# Sabırlı mod
chapie ask "Kompleks soru" --patient
```

### Empati Modülü

```bash
# Duygu analizi etkin
chapie ask "Kendimi kötü hissediyorum" --emotion-aware

# Empatik yanıtlar
chapie ask "Zor bir gün geçirdim" --empathetic

# Duygusal destek
chapie ask "Yardıma ihtiyacım var" --supportive
```

### Kodlama ve Teknik Görevler

```bash
# Kod analizi
chapie code analyze /path/to/code.rs

# Hata ayıklama
chapie code debug /path/to/code.rs --error "error message"

# Test yazma
chapie code test /path/to/code.rs --framework pytest

# Refactoring
chapie code refactor /path/to/code.rs --pattern "improve_performance"

# Dokümantasyon oluşturma
chapie code document /path/to/code.rs --format markdown
```

### Web ve API İşlemleri

```bash
# Web arama
chapie web search "Rust programming language"

# Sayfa okuma
chapie web fetch https://example.com

# API çağrısı
chapie api call https://api.example.com/data --method GET

# JSON işleme
chapie json process data.json --query ".items[0].name"
```

## Telegram Bot Kullanımı

### Bot Kurulumu
1. Telegram'da @BotFather ile yeni bot oluştur
2. API token'ını al
3. Chapie'yi Telegram modunda başlat:

```bash
chapie telegram --token YOUR_BOT_TOKEN
```

### Telegram Komutları
```
/start - Chapie'yi başlat
/help - Yardım menüsü
/status - Sistem durumu
/tools - Kullanılabilir araçlar
/profile - Profil bilgisi
/memory - Bellek yönetimi
/settings - Ayarlar
```

### Örnek Kullanım
```
Kullanıcı: /start
Chapie: Merhaba! Ben Chapie. Nasıl yardımcı olabilirim?

Kullanıcı: Bugün hava nasıl?
Chapie: İstanbul'da hava 18°C ve güneşli. Dışarı çıkmak için harika bir gün! ☀️

Kullanıcı: README.md dosyasını oku
Chapie: Dosya okunuyor... İçerik: "# Workspace Organization..."
```

## Web Arayüzü Kullanımı

### Yerel Geliştirme Sunucusu
```bash
# Web arayüzünü başlat
chapie web --port 3000

# Tarayıcıda aç
open http://localhost:3000
```

### Web Arayüzü Özellikleri
1. **Chat Interface:** Gerçek zamanlı sohbet
2. **File Manager:** Dosya yönetimi
3. **Tool Dashboard:** Araç kontrol paneli
4. **Memory Browser:** Bellek görüntüleyici
5. **Settings Panel:** Ayarlar yönetimi

## Güvenlik ve İzin Yönetimi

### İzin Seviyeleri
```bash
# İzin durumunu görüntüle
chapie permissions status

# İzin ver
chapie permissions grant read_file

# İzin kaldır
chapie permissions revoke execute_shell

# İzin listesini görüntüle
chapie permissions list
```

### Onay Mekanizması
```bash
# Onay gerektiren komut
chapie shell "sudo apt update" --require-approval

# Onay geçmişi
chapie approvals list

# Onay ver
chapie approvals approve request_id

# Onay reddet
chapie approvals deny request_id
```

### Güvenli Mod
```bash
# Güvenli modda başlat
chapie start --safe-mode

# Sadece okuma izinleri
chapie start --read-only

# Sandbox modu
chapie start --sandbox
```

## Sorun Giderme

### Sık Karşılaşılan Sorunlar

#### 1. API Anahtar Hatası
```
Error: Deepseek API key not found
```
**Çözüm:**
```bash
export DEEPSEEK_API_KEY="sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
# veya
echo 'DEEPSEEK_API_KEY="sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"' > ~/.chapie/.env
```

#### 2. Bellek Veritabanı Hatası
```
Error: Cannot open database file
```
**Çözüm:**
```bash
# Bellek dizinini oluştur
mkdir -p ~/.chapie/memory

# İzinleri ayarla
chmod 700 ~/.chapie
```

#### 3. Araç İzin Hatası
```
Error: Permission denied for tool execution
```
**Çözüm:**
```bash
# İzin ver
chapie permissions grant tool_name

# Veya onay iste
chapie tools execute tool_name --require-approval
```

### Log Kayıtları
```bash
# Log dosyasını görüntüle
tail -f ~/.chapie/logs/chapie.log

# Hata loglarını görüntüle
chapie logs --level error

# Detaylı log modu
chapie start --log-level debug
```

### Sistem Tanılama
```bash
# Sistem tanılama raporu oluştur
chapie diagnose

# Performans testi
chapie benchmark

# Bağımlılık kontrolü
chapie dependencies check
```

## En İyi Uygulamalar

### 1. Güvenlik
- API anahtarlarını asla commit etmeyin
- .env dosyasını .gitignore'a ekleyin
- Düzenli olarak izinleri gözden geçirin
- Şüpheli komutlar için onay isteyin

### 2. Performans
- Büyük dosyaları parçalı okuyun
- Sık kullanılan verileri önbelleğe alın
- Gereksiz bellek kullanımından kaçının
- Düzenli olarak bellek temizliği yapın

### 3. Kullanıcı Deneyimi
- Otizm dostu modu tercih edin
- Açık ve net iletişim kurun
- Kullanıcı tercihlerini öğrenin
- Düzenli geri bildirim alın

### 4. Bakım
- Düzenli yedekleme yapın
- Logları izleyin
- Güncellemeleri takip edin
- Topluluk katkılarını değerlendirin

## Örnek Kullanım Senaryoları

### Senaryo 1: Günlük Asistan
```bash
# Sabah rutini
chapie ask "Bugün hava durumu nasıl?"
chapie ask "Takvimimde bugün ne var?"
chapie ask "Önemli emailler var mı?"

# Çalışma zamanı
chapie file edit proje/plan.md "Yeni görevler ekle"
chapie shell "git status"
chapie web search "Rust async programming"

# Akşam rutini
chapie ask "Yarın için hatırlatıcı oluştur"
chapie memory add "Bugün projede ilerleme kaydedildi"
chapie ask "Yarın ne yapmalıyım?"
```

### Senaryo 2: Kod Geliştirme
```bash
# Proje başlatma
chapie code new rust_project --template basic

# Kod yazma
chapie code write src/main.rs "fn main() { println!(\"Hello, Chapie!\"); }"

# Hata ayıklama
chapie code debug src/main.rs --error "compilation error"

# Test yazma
chapie code test src/lib.rs --unit-tests

# Dokümantasyon
chapie code document . --format markdown

# Deployment
chapie shell "cargo build --release"
chapie shell "scp target/release/app server:/opt/app"
```

### Senaryo 3: Otizm Desteği
```bash
# Sosyal durum analizi
chapie ask "Toplantıda nasıl davranmalıyım?" --autism-friendly

# Duygu yönetimi
chapie ask "Stresli hissediyorum, ne yapmalıyım?" --empathetic

# Rutin planlama
chapie ask "Günlük rutinimi planla" --explicit

# Sosyal ipuçları
chapie ask "İnsanlarla nasıl sohbet edilir?" --step-by-step
```

## Geliştirici Dokümantasyonu

### API Kullanımı
```rust
use chapie::prelude::*;

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    // Chapie client oluştur
    let mut chapie = ChapieClient::new()
        .with_api_key("sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")
        .with_preferences(UserPreferences {
            language: "tr".to_string(),
            autism_friendly: true,
            ..Default::default()
        })
        .build()?;

    // Mesaj gönder
    let response = chapie.process_message("Merhaba Chapie!").await?;
    println!("Yanıt: {}", response.text);

    // Araç çalıştır
    let result = chapie.execute_tool("file_read", json!({"path": "test.txt"})).await?;
    println!("Sonuç: {:?}", result);

    Ok(())
}
```

### Plugin Geliştirme
```rust
use chapie::prelude::*;

#[derive(Debug)]
struct CustomTool;

#[async_trait]
impl Tool for CustomTool {
    fn name(&self) -> &str {
        "custom_tool"
    }

    fn description(&self) -> &str {
        "Özel kullanıcı aracı"
    }

    async fn execute(&self, params: Value) -> Result<Value, ToolError> {
        // Özel iş mantığı
        Ok(json!({"result": "success"}))
    }
}

// Plugin kaydet
chapie.register_tool(Box::new(CustomTool));
```

## SSS (Sık Sorulan Sorular)

### 1. Chapie ücretsiz mi?
Evet, Chapie tamamen açık kaynak ve ücretsizdir. MIT l