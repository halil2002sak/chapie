# Chapie Data Models - Veri Modelleri

## Genel Bakış

Chapie'nin programatik insan modeli, çeşitli veri yapıları ve modeller üzerine kuruludur.
Bu belge, Chapie'nin kullandığı tüm veri modellerini tanımlar.

## Temel Veri Tipleri

### 1. BrainState - Beyin Durumu

```rust
struct BrainState {
    // Bilişsel durum
    cognitive_state: CognitiveState,
    
    // Duygusal durum
    emotional_state: EmotionalState,
    
    // Bellek durumu
    memory_state: MemoryState,
    
    // Karar verme durumu
    decision_state: DecisionState,
    
    // Araç durumu
    tool_state: ToolState,
    
    // Sistem durumu
    system_state: SystemState,
    
    // Zaman damgası
    timestamp: DateTime<Utc>,
    
    // Oturum bilgisi
    session_id: String,
    
    // Kullanıcı bağlamı
    user_context: UserContext,
}
```

### 2. CognitiveState - Bilişsel Durum

```rust
struct CognitiveState {
    // Aktif bilişsel süreç
    active_process: CognitiveProcess,
    
    // Dikkat seviyesi (0-100)
    attention_level: u8,
    
    // Odaklanma seviyesi (0-100)
    focus_level: u8,
    
    // Yorgunluk seviyesi (0-100)
    fatigue_level: u8,
    
    // Öğrenme modu
    learning_mode: LearningMode,
    
    // Problem çözme modu
    problem_solving_mode: ProblemSolvingMode,
    
    // Yaratıcılık seviyesi (0-100)
    creativity_level: u8,
    
    // Mantıksal akıl yürütme seviyesi (0-100)
    logical_reasoning_level: u8,
}

enum CognitiveProcess {
    Perception,      // Algılama
    Understanding,   // Anlama
    MemoryRecall,    // Hatırlama
    DecisionMaking,  // Karar Verme
    EmotionalProcessing, // Duygusal İşleme
    ActionExecution, // Eyleme Geçme
    Idle,           // Boşta
}

enum LearningMode {
    Passive,     // Pasif öğrenme
    Active,      // Aktif öğrenme
    Reinforcement, // Pekiştirmeli öğrenme
    Experiential, // Deneyimsel öğrenme
}

enum ProblemSolvingMode {
    Analytical,   // Analitik
    Creative,     // Yaratıcı
    Systematic,   // Sistematik
    Intuitive,    // Sezgisel
}
```

### 3. EmotionalState - Duygusal Durum

```rust
struct EmotionalState {
    // Temel duygu
    primary_emotion: Emotion,
    
    // İkincil duygular
    secondary_emotions: Vec<Emotion>,
    
    // Duygu yoğunluğu (0-100)
    intensity: u8,
    
    // Duygu süresi (saniye)
    duration_seconds: u32,
    
    // Duygu tetikleyicisi
    trigger: Option<String>,
    
    // Empati seviyesi (0-100)
    empathy_level: u8,
    
    // Motivasyon seviyesi (0-100)
    motivation_level: u8,
    
    // Stres seviyesi (0-100)
    stress_level: u8,
}

enum Emotion {
    // Pozitif duygular
    Happy,      // Mutlu
    Excited,    // Heyecanlı
    Content,    // Memnun
    Proud,      // Gururlu
    Hopeful,    // Umutlu
    Grateful,   // Minnettar
    
    // Negatif duygular
    Sad,        // Üzgün
    Angry,      // Sinirli
    Anxious,    // Endişeli
    Frustrated, // Hayal kırıklığı
    Lonely,     // Yalnız
    Tired,      // Yorgun
    
    // Nötr duygular
    Neutral,    // Nötr
    Curious,    // Meraklı
    Confused,   // Kafası karışık
    Surprised,  // Şaşkın
    Bored,      // Sıkılmış
}
```

### 4. MemoryState - Bellek Durumu

```rust
struct MemoryState {
    // Kısa vadeli bellek durumu
    short_term: ShortTermMemoryState,
    
    // Uzun vadeli bellek durumu
    long_term: LongTermMemoryState,
    
    // Prosedürel bellek durumu
    procedural: ProceduralMemoryState,
    
    // Çalışma belleği durumu
    working: WorkingMemoryState,
    
    // Bellek kullanım yüzdesi (0-100)
    usage_percentage: u8,
    
    // Bellek temizleme durumu
    cleanup_status: CleanupStatus,
}

struct ShortTermMemoryState {
    // Aktif öğe sayısı
    active_items: u32,
    
    // Maksimum kapasite
    capacity: u32,
    
    // Ortalama saklama süresi (saniye)
    average_retention_seconds: u32,
    
    // En son erişim zamanı
    last_access_time: DateTime<Utc>,
}

struct LongTermMemoryState {
    // Toplam kayıt sayısı
    total_records: u64,
    
    // Kategori sayısı
    category_count: u32,
    
    // Ortalama erişim süresi (milisaniye)
    average_access_time_ms: u32,
    
    // En sık erişilen kategori
    most_accessed_category: String,
    
    // En eski kayıt tarihi
    oldest_record_date: DateTime<Utc>,
}

struct ProceduralMemoryState {
    // Öğrenilen prosedür sayısı
    learned_procedures: u32,
    
    // Başarı oranı (0-100)
    success_rate: u8,
    
    // Ortalama yürütme süresi (milisaniye)
    average_execution_time_ms: u32,
    
    // En sık kullanılan prosedür
    most_used_procedure: String,
}

struct WorkingMemoryState {
    // Aktif görev sayısı
    active_tasks: u32,
    
    // Görev öncelikleri
    task_priorities: Vec<TaskPriority>,
    
    // Bağlam bilgisi
    context: WorkingMemoryContext,
    
    // Geçici veri boyutu (byte)
    temporary_data_size: u64,
}

enum CleanupStatus {
    Idle,           // Boşta
    InProgress,     // Devam ediyor
    Scheduled,      // Planlanmış
    Paused,         // Duraklatılmış
}
```

## Kullanıcı Modelleri

### 1. UserProfile - Kullanıcı Profili

```rust
struct UserProfile {
    // Temel bilgiler
    basic_info: BasicUserInfo,
    
    // Tercihler
    preferences: UserPreferences,
    
    // İhtiyaçlar
    needs: UserNeeds,
    
    // İlgi alanları
    interests: UserInterests,
    
    // Bilgi seviyesi
    knowledge_level: KnowledgeLevel,
    
    // Etkileşim geçmişi
    interaction_history: InteractionHistory,
    
    // Güvenlik ayarları
    security_settings: SecuritySettings,
    
    // Meta veriler
    metadata: UserMetadata,
}

struct BasicUserInfo {
    user_id: String,
    username: Option<String>,
    display_name: String,
    language: String,  // "tr", "en", etc.
    timezone: String,
    created_at: DateTime<Utc>,
    last_active: DateTime<Utc>,
}

struct UserPreferences {
    // İletişim tercihleri
    communication_style: CommunicationStyle,
    detail_level: DetailLevel,
    response_speed: ResponseSpeed,
    humor_level: HumorLevel,
    formality: FormalityLevel,
    
    // Görsel tercihler
    visual_preferences: VisualPreferences,
    
    // Ses tercihleri
    audio_preferences: AudioPreferences,
    
    // Etkileşim tercihleri
    interaction_preferences: InteractionPreferences,
}

enum CommunicationStyle {
    Direct,          // Doğrudan
    Detailed,        // Detaylı
    Concise,         // Kısa ve öz
    AutismFriendly,  // Otizm dostu
    Technical,       // Teknik
    Casual,          // Gündelik
}

enum DetailLevel {
    Minimal,     // Minimal
    Normal,      // Normal
    Detailed,    // Detaylı
    Comprehensive, // Kapsamlı
}

enum ResponseSpeed {
    Slow,        // Yavaş
    Balanced,    // Dengeli
    Fast,        // Hızlı
    Realtime,    // Gerçek zamanlı
}

struct UserNeeds {
    // Özel ihtiyaçlar
    autism_support: bool,
    explicit_instructions: bool,
    predictable_responses: bool,
    patience_level: PatienceLevel,
    
    // Erişilebilirlik ihtiyaçları
    accessibility_needs: AccessibilityNeeds,
    
    // Öğrenme ihtiyaçları
    learning_needs: LearningNeeds,
    
    // Teknik ihtiyaçlar
    technical_needs: TechnicalNeeds,
}

enum PatienceLevel {
    Low,     // Düşük
    Medium,  // Orta
    High,    // Yüksek
    VeryHigh, // Çok yüksek
}

struct UserInterests {
    // Ana ilgi alanları
    primary_interests: Vec<String>,  // ["technology", "coding", "gaming"]
    
    // İkincil ilgi alanları
    secondary_interests: Vec<String>,
    
    // Öğrenmek istedikleri
    learning_interests: Vec<String>,
    
    // Kaçınılan konular
    avoided_topics: Vec<String>,
}

struct KnowledgeLevel {
    // Genel bilgi seviyesi
    general: KnowledgeRating,
    
    // Teknoloji bilgisi
    technology: KnowledgeRating,
    
    // Kodlama bilgisi
    coding: KnowledgeRating,
    
    // Diğer alanlar
    other_fields: HashMap<String, KnowledgeRating>,
}

enum KnowledgeRating {
    Beginner,     // Başlangıç
    Intermediate, // Orta
    Advanced,     // İleri
    Expert,       // Uzman
}
```

### 2. UserContext - Kullanıcı Bağlamı

```rust
struct UserContext {
    // Mevcut durum
    current_state: UserCurrentState,
    
    // Ortam bilgisi
    environment: EnvironmentInfo,
    
    // Cihaz bilgisi
    device: DeviceInfo,
    
    // Zaman bilgisi
    time: TimeContext,
    
    // Sosyal bağlam
    social_context: SocialContext,
    
    // Görev bağlamı
    task_context: TaskContext,
    
    // Duygusal bağlam
    emotional_context: EmotionalContext,
}

struct UserCurrentState {
    // Fiziksel durum
    physical_state: PhysicalState,
    
    // Zihinsel durum
    mental_state: MentalState,
    
    // Duygusal durum
    emotional_state: UserEmotionalState,
    
    // Sosyal durum
    social_state: SocialState,
}

enum PhysicalState {
    Resting,      // Dinleniyor
    Working,      // Çalışıyor
    Moving,       // Hareket halinde
    Sleeping,     // Uyuyor
    Eating,       // Yemek yiyor
    Exercising,   // Egzersiz yapıyor
}

enum MentalState {
    Focused,      // Odaklanmış
    Distracted,   // Dikkati dağılmış
    Creative,     // Yaratıcı
    Analytical,   // Analitik
    Tired,        // Yorgun
    Energetic,    // Enerjik
}

struct EnvironmentInfo {
    location: Option<String>,
    temperature: Option<f32>,
    noise_level: Option<NoiseLevel>,
    lighting: Option<LightingLevel>,
    weather: Option<WeatherCondition>,
}

enum NoiseLevel {
    Silent,       // Sessiz
    Quiet,        // Sakin
    Moderate,     // Orta
    Loud,         // Gürültülü
    VeryLoud,     // Çok gürültülü
}

struct TimeContext {
    time_of_day: TimeOfDay,
    day_of_week: DayOfWeek,
    is_weekend: bool,
    is_holiday: bool,
    season: Season,
}

enum TimeOfDay {
    Morning,      // Sabah
    Afternoon,    // Öğleden sonra
    Evening,      // Akşam
    Night,        // Gece
    LateNight,    // Gece geç
}
```

## Mesaj ve İletişim Modelleri

### 1. Message - Mesaj

```rust
struct Message {
    // Mesaj kimliği
    id: String,
    
    // İçerik
    content: MessageContent,
    
    // Gönderen
    sender: SenderInfo,
    
    // Alıcı
    receiver: ReceiverInfo,
    
    // Zaman damgası
    timestamp: DateTime<Utc>,
    
    // Bağlam
    context: MessageContext,
    
    // Meta veriler
    metadata: MessageMetadata,
}

struct MessageContent {
    // Metin içeriği
    text: String,
    
    // Format
    format: MessageFormat,
    
    // Dil
    language: String,
    
    // Duygu analizi
    emotion_analysis: Option<EmotionAnalysis>,
    
    // Niyet analizi
    intent_analysis: Option<IntentAnalysis>,
    
    // Ek medya
    media: Vec<MediaAttachment>,
}

enum MessageFormat {
    PlainText,    // Düz metin
    Markdown,     // Markdown
    HTML,         // HTML
    JSON,         // JSON
    Custom(String), // Özel format
}

struct SenderInfo {
    type: SenderType,
    id: String,
    name: String,
    platform: Platform,
    is_bot: bool,
}

enum SenderType {
    User,         // Kullanıcı
    Assistant,    // Asistan
    System,       // Sistem
    Tool,         // Araç
    ThirdParty,   // Üçüncü parti
}

struct MessageContext {
    // Konuşma bağlamı
    conversation_id: String,
    
    // Önceki mesajlar
    previous_messages: Vec<MessageReference>,
    
    // Konu
    topic: Option<String>,
    
    // Amaç
    purpose: MessagePurpose,
    
    // Beklentiler
    expectations: Vec<Expectation>,
}

enum MessagePurpose {
    Question,      // Soru
    Command,       // Komut
    Statement,     // İfade
    Request,       // İstek
    Feedback,      // Geri bildirim
    Social,        // Sosyal
    Technical,     // Teknik
}
```

### 2. Response - Yanıt

```rust
struct Response {
    // Yanıt kimliği
    id: String,
    
    // İçerik
    content: ResponseContent,
    
    // Kaynak mesaj
    source_message_id: String,
    
    // Üretim bilgisi
    generation_info: GenerationInfo,
    
    // Eylemler
    actions: Vec<Action>,
    
    // Bellek güncellemeleri
    memory_updates: Vec<MemoryUpdate>,
    
    // Meta veriler
    metadata: ResponseMetadata,
}

struct ResponseContent {
    // Ana yanıt
    primary: PrimaryResponse,
    
    // Alternatif yanıtlar
    alternatives: Vec<AlternativeResponse>,
    
    // Açıklamalar
    explanations: Vec<Explanation>,
    
    // Öneriler
    suggestions: Vec<Suggestion>,
    
    // Sorular
    follow_up_questions: Vec<Question>,
}

struct PrimaryResponse {
    text: String,
    format: ResponseFormat,
    emotion: ResponseEmotion,
    tone: ResponseTone,
    complexity: ComplexityLevel,
}

enum ResponseFormat {
    TextOnly,     // Sadece metin
    TextWithMedia, // Metin + medya
    Interactive,  // Etkileşimli
    Structured,   // Yapılandırılmış
}

struct ResponseEmotion {
    primary: Emotion,
    intensity: u8,
    expression: EmotionalExpression,
    appropriateness: AppropriatenessLevel,
}

enum EmotionalExpression {
    Neutral,      // Nötr
    Empathetic,   // Empatik
    Encouraging,  // Teşvik edici
    Professional, // Profesyonel
    Friendly,     // Dostane
    Humorous,     // Mizahi
}

struct GenerationInfo {
    // Üretim süresi (milisaniye)
    generation_time_ms: u32,
    
    // Kullanılan beyin bileşenleri