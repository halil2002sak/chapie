# Chapie API Design - API Tasarımı

## Genel Bakış

Chapie, çoklu arayüz ve iletişim yöntemlerini destekleyen bir API mimarisine sahiptir.
Tüm API'ler RESTful prensiplere uygun olarak tasarlanmıştır.

## API Katmanları

### 1. Çekirdek API (Core API)
- Sanal beyin çekirdeği ile doğrudan iletişim
- Bilişsel süreç yönetimi
- Bellek ve öğrenme işlemleri

### 2. Araç API (Tools API)
- Araç yürütme ve yönetimi
- Güvenlik ve izin kontrolleri
- Araç zincirleme ve paralel çalıştırma

### 3. İletişim API (Communication API)
- Çoklu giriş/çıkış yöntemleri
- Protokol dönüşümleri
- Format ve kodlama işlemleri

### 4. Yönetim API (Management API)
- Sistem durumu ve monitoring
- Konfigürasyon yönetimi
- Log ve audit kayıtları

## REST API Endpoints

### Temel Endpoints

#### `POST /api/v1/process`
**Açıklama:** Kullanıcı mesajını işle ve yanıt oluştur

**Request Body:**
```json
{
  "message": "Bugün hava durumu nasıl?",
  "context": {
    "session_id": "session-123",
    "user_id": "user-456",
    "preferences": {
      "language": "tr",
      "detail_level": "normal",
      "autism_friendly": true
    }
  },
  "options": {
    "include_emotion": true,
    "include_memory": false,
    "tool_execution": "auto"
  }
}
```

**Response Body:**
```json
{
  "response": {
    "text": "Bugün İstanbul'da hava 18°C ve güneşli. Hafif rüzgar var.",
    "emotion": {
      "detected": "neutral",
      "response_tone": "informative",
      "empathy_level": "medium"
    },
    "actions": [
      {
        "type": "tool_execution",
        "tool": "weather_check",
        "result": "success",
        "data": {
          "temperature": 18,
          "condition": "sunny",
          "location": "Istanbul"
        }
      }
    ],
    "memory_updates": {
      "last_weather_check": "2026-04-04T21:48:00Z",
      "user_interests": ["weather"]
    }
  },
  "metadata": {
    "processing_time_ms": 245,
    "brain_components_used": ["prefrontal", "brainstem"],
    "tools_executed": ["weather_check"],
    "session_id": "session-123"
  }
}
```

#### `GET /api/v1/status`
**Açıklama:** Sistem durumunu ve sağlık bilgilerini getir

**Response Body:**
```json
{
  "status": "healthy",
  "components": {
    "brain_core": {
      "prefrontal": "active",
      "limbic": "active",
      "hippocampus": "active",
      "brainstem": "active"
    },
    "memory": {
      "short_term": "85%",
      "long_term": "42%",
      "procedural": "23%"
    },
    "tools": {
      "available": 24,
      "active": 3,
      "healthy": true
    }
  },
  "performance": {
    "avg_response_time_ms": 320,
    "requests_processed": 1245,
    "uptime_hours": 48.5
  },
  "version": "0.1.0"
}
```

#### `GET /api/v1/memory/{memory_type}`
**Açıklama:** Bellek içeriğini sorgula

**Path Parameters:**
- `memory_type`: `short_term`, `long_term`, `procedural`, `user_profile`

**Query Parameters:**
- `user_id`: Kullanıcı ID (opsiyonel)
- `session_id`: Oturum ID (opsiyonel)
- `limit`: Sonuç sayısı (varsayılan: 10)
- `offset`: Başlangıç offset'i (varsayılan: 0)

**Response Body:**
```json
{
  "memory_type": "long_term",
  "entries": [
    {
      "id": "mem-001",
      "timestamp": "2026-04-03T14:30:00Z",
      "content": "Kullanıcı Rust projesinde hata ayıklama yardımı istedi",
      "tags": ["coding", "rust", "debug"],
      "relevance_score": 0.92
    },
    {
      "id": "mem-002",
      "timestamp": "2026-04-02T10:15:00Z",
      "content": "Kullanıcı otizm dostu iletişim tercih etti",
      "tags": ["preference", "autism_friendly", "communication"],
      "relevance_score": 0.87
    }
  ],
  "total_count": 45,
  "page_info": {
    "limit": 10,
    "offset": 0,
    "has_more": true
  }
}
```

#### `POST /api/v1/tools/execute`
**Açıklama:** Belirli bir aracı doğrudan çalıştır

**Request Body:**
```json
{
  "tool_name": "file_read",
  "parameters": {
    "path": "/home/halil/workspace/README.md",
    "encoding": "utf-8"
  },
  "context": {
    "user_id": "user-456",
    "session_id": "session-123"
  },
  "permissions": {
    "require_approval": false,
    "timeout_ms": 5000
  }
}
```

**Response Body:**
```json
{
  "tool_execution": {
    "tool_name": "file_read",
    "status": "success",
    "execution_time_ms": 42,
    "result": {
      "content": "# Workspace Organization\n\nThis workspace has been organized automatically...",
      "metadata": {
        "file_size_bytes": 24179,
        "lines": 58,
        "encoding": "utf-8"
      }
    },
    "logs": [
      "Tool initialized",
      "File opened successfully",
      "Content read (24179 bytes)",
      "Tool completed"
    ]
  },
  "security": {
    "permissions_checked": true,
    "risk_level": "low",
    "approval_required": false,
    "approval_granted": true
  }
}
```

### Araç Yönetimi Endpoints

#### `GET /api/v1/tools`
**Açıklama:** Kullanılabilir araçları listele

**Response Body:**
```json
{
  "tools": [
    {
      "name": "file_read",
      "description": "Dosya okuma aracı",
      "category": "daily",
      "permissions_required": ["read_file"],
      "risk_level": "low",
      "parameters": [
        {
          "name": "path",
          "type": "string",
          "required": true,
          "description": "Okunacak dosya yolu"
        }
      ]
    },
    {
      "name": "shell_execute",
      "description": "Shell komutu çalıştırma",
      "category": "technical",
      "permissions_required": ["execute_shell"],
      "risk_level": "medium",
      "parameters": [
        {
          "name": "command",
          "type": "string",
          "required": true,
          "description": "Çalıştırılacak shell komutu"
        }
      ]
    }
  ],
  "total_tools": 24,
  "categories": {
    "daily": 12,
    "technical": 8,
    "communication": 4
  }
}
```

#### `POST /api/v1/tools/register`
**Açıklama:** Yeni araç kaydet (plugin sistemi)

**Request Body:**
```json
{
  "tool": {
    "name": "custom_tool",
    "description": "Özel kullanıcı aracı",
    "category": "custom",
    "execution_handler": "python:/path/to/handler.py",
    "parameters": [
      {
        "name": "input",
        "type": "string",
        "required": true
      }
    ]
  },
  "permissions": {
    "user_id": "user-456",
    "trust_level": "high"
  }
}
```

### Kullanıcı ve Kişiselleştirme Endpoints

#### `GET /api/v1/user/profile`
**Açıklama:** Kullanıcı profilini getir

**Response Body:**
```json
{
  "profile": {
    "user_id": "user-456",
    "preferences": {
      "language": "tr",
      "communication_style": "autism_friendly",
      "detail_level": "normal",
      "response_speed": "balanced",
      "humor_level": "low",
      "formality": "casual"
    },
    "needs": {
      "autism_support": true,
      "explicit_instructions": true,
      "predictable_responses": true,
      "patience_level": "high"
    },
    "interests": ["technology", "coding", "gaming"],
    "knowledge_level": {
      "technology": "advanced",
      "coding": "intermediate",
      "general": "basic"
    },
    "created_at": "2026-04-01T10:00:00Z",
    "last_updated": "2026-04-04T15:30:00Z",
    "interaction_count": 124
  }
}
```

#### `PUT /api/v1/user/profile`
**Açıklama:** Kullanıcı profilini güncelle

**Request Body:**
```json
{
  "updates": {
    "preferences": {
      "detail_level": "high",
      "response_speed": "fast"
    },
    "needs": {
      "explicit_instructions": false
    },
    "interests": ["technology", "coding", "gaming", "ai"]
  }
}
```

### Sistem Yönetimi Endpoints

#### `POST /api/v1/system/learn`
**Açıklama:** Sistemin öğrenme sürecini tetikle

**Request Body:**
```json
{
  "learning_type": "from_interaction",
  "data": {
    "interaction_id": "int-789",
    "success": true,
    "user_feedback": "positive",
    "improvement_suggestions": "Daha hızlı yanıt verebilirsin"
  }
}
```

#### `GET /api/v1/system/logs`
**Açıklama:** Sistem loglarını getir

**Query Parameters:**
- `level`: `error`, `warning`, `info`, `debug` (opsiyonel)
- `since`: ISO timestamp (opsiyonel)
- `limit`: Sonuç sayısı (varsayılan: 50)

## CLI API (Komut Satırı Arayüzü)

### Temel Komutlar

```bash
# Chapie'yi başlat
chapie start

# Mesaj gönder ve yanıt al
chapie ask "Bugün hava nasıl?"

# Dosya işlemi
chapie file read /path/to/file.txt
chapie file edit /path/to/file.txt "yeni içerik"

# Shell komutu çalıştır
chapie shell "ls -la"

# Sistem durumunu kontrol et
chapie status

# Bellek sorgula
chapie memory list --type long_term --limit 5

# Araçları listele
chapie tools list

# Kullanıcı profilini göster
chapie profile show

# Profili güncelle
chapie profile update --detail-level high
```

### CLI Konfigürasyon Dosyası

`~/.chapie/config.toml`:
```toml
[user]
id = "user-456"
name = "Halil"
language = "tr"

[preferences]
communication_style = "autism_friendly"
detail_level = "normal"
response_speed = "balanced"
autism_support = true

[api]
base_url = "http://localhost:8080"
timeout_seconds = 30

[tools]
default_permissions = ["read_file", "execute_shell_low_risk"]
require_approval_for = ["delete_file", "execute_shell_high_risk"]

[memory]
short_term_capacity = 100
long_term_persistence = true
auto_cleanup_days = 30
```

## Telegram Bot API

### Webhook Endpoint

`POST /api/v1/telegram/webhook`

**Telegram'dan gelen mesaj formatı:**
```json
{
  "update_id": 123456,
  "message": {
    "message_id": 789,
    "from": {
      "id": 8229309018,
      "is_bot": false,
      "first_name": "Halil",
      "username": "halil2002sak"
    },
    "chat": {
      "id": 8229309018,
      "first_name": "Halil",
      "username": "halil2002sak",
      "type": "private"
    },
    "date": 1743796800,
    "text": "Merhaba Chapie"
  }
}
```

**Chapie'den Telegram'a yanıt:**
```json
{
  "method": "sendMessage",
  "chat_id": 8229309018,
  "text": "Merhaba Halil! Nasılsın?",
  "parse_mode": "Markdown",
  "reply_markup": {
    "inline_keyboard": [
      [
        {
          "text": "Dosya Oku",
          "callback_data": "tool:file_read"
        },
        {
          "text": "Kod Yaz",
          "callback_data": "tool:code_write"
        }
      ]
    ]
  }
}
```

### Telegram Bot Komutları

```
/start - Chapie'yi başlat
/help - Yardım menüsü
/status - Sistem durumu
/tools - Kullanılabilir araçlar
/profile - Profil bilgisi
/memory - Bellek yönetimi
/settings - Ayarlar
```

## WebSocket API (Gerçek Zamanlı İletişim)

### Bağlantı Endpoint

`WS /api/v1/ws`

**Bağlantı açıldığında:**
```json
{
  "type": "connection_established",
  "session_id": "ws-session-123",
  "timestamp": "2026-04-04T21:48:00Z"
}
```

**Mesaj gönderme:**
```json
{
  "type": "user_message",
  "message": "Bugün ne yapalım?",
  "session_id": "ws-session-123",
  "timestamp": "2026-04-04T21:48:05Z"
}
```

**Mesaj alma:**
```json
{
  "type": "assistant_response",
  "response": {
    "text": "Önerilerim: 1) Chapie dokümantasyonuna devam et 2) Rust projesinde hata ayıkla 3) Yeni özellik ekle",
    "emotion": "helpful",
    "suggestions": [
      {
        "text": "Dokümantasyona devam et",
        "action": "continue_documentation"
      },
      {
        "text": "Kod yazmaya başla",
        "action": "start_coding"
      }
    ]
  },
  "session_id": "ws-session-123",
  "timestamp": "2026-04-04T21:48:07Z"
}
```

## HTTP Headers ve Authentication

### Authentication Headers

```
Authorization: Bearer chapie_token_xyz123
X-User-ID: user-456
X-Session-ID: session-123
```

### Rate Limiting Headers

```
X-RateLimit-Limit: 100
X-RateLimit-Remaining: 95
X-RateLimit-Reset: 1743797100
```

### Response Headers

```
Content-Type: application/json; charset=utf-8
X-Request-ID: req-789
X-Processing-Time-MS: 245
X-Chapie-Version: 0.1.0
```

## Hata Yönetimi

### Hata Response Formatı

```json
{
  "error": {
    "code": "TOOL_EXECUTION_FAILED",
    "message": "Dosya okuma işlemi başarısız",
    "details": {
      "tool": "file_read",
      "reason": "File not found",
      "suggestion": "Dosya yolunu kontrol edin"
    },
    "timestamp": "2026-04-04T21:48:00Z",
    "request_id": "req-789"
  }
}
```

### Hata Kodları

- `AUTH_REQUIRED`: Authentication gerekiyor
- `INVALID_INPUT`: Ge