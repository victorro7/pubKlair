# Klair Backend Service
---

## 📖 Overview

The Klair backend is a sophisticated, enterprise-grade Python application built with FastAPI that powers AI-driven video content analysis. It features a microservices architecture designed for scalability, real-time processing, and seamless integration with cloud services.

### 🏗️ Architecture Principles

- **Async-First**: Built entirely on async/await for maximum performance
- **Microservices**: Modular services for video, audio, queue management, and AI processing
- **Cloud-Native**: Designed for containerized deployment and auto-scaling
- **Event-Driven**: Redis-based queue system for decoupled processing
- **Type-Safe**: Comprehensive type hints with Pydantic models

---

## 🛠️ Technology Stack

### Core Framework
- **FastAPI 0.115+**: Modern, fast web framework with automatic API documentation
- **Uvicorn**: Lightning-fast ASGI server
- **Pydantic**: Data validation and settings management with type safety
- **Python 3.11+**: Latest Python features and performance improvements

### Database & Storage
- **PostgreSQL 15+**: Primary database with ACID compliance
- **SQLAlchemy 2.0**: Modern async ORM with declarative syntax
- **Asyncpg**: High-performance PostgreSQL adapter
- **Alembic**: Database migration management
- **Google Cloud Storage**: Scalable object storage for video assets

### Queue & Processing
- **Redis 7+**: Message broker and caching layer
- **Custom Queue Manager**: Tier-based job prioritization
- **Async Workers**: Concurrent video processing pipeline
- **Rate Limiting**: API quota management and burst protection

### AI & Media Processing
- **Google Vertex AI**: Gemini 2.5 Pro integration for multimodal analysis
- **FFmpeg**: Professional video/audio processing and transcoding
- **yt-dlp**: Universal video downloader supporting 1000+ sites
- **Sieve API**: Specialized video autocropping and enhancement

### Authentication & Security
- **Clerk**: Enterprise-grade authentication and user management
- **JWT**: Secure token-based authentication
- **CORS**: Configurable cross-origin resource sharing
- **Input Validation**: Comprehensive request/response validation

### Monitoring & Logging
- **Structlog**: Structured JSON logging for observability
- **Custom Error Handling**: Detailed error tracking and reporting
- **Health Checks**: Application and dependency monitoring
- **Performance Metrics**: Request timing and throughput analysis

---

## 📂 Project Structure

```
backend/
├── main.py                    # Application entry point & FastAPI setup
├── requirements.txt           # Python dependencies
├── alembic.ini               # Database migration configuration
├── Dockerfile                # Container image definition
│
├── api/                      # API layer
│   ├── models/              # Pydantic request/response models
│   │   ├── auth.py         # Authentication models
│   │   ├── klair.py        # Core video analysis models
│   │   ├── upload.py       # File upload models
│   │   └── user.py         # User management models
│   └── routes/              # API route definitions
│       ├── audio_routes.py  # Audio analysis endpoints
│       ├── job_routes.py    # Job management endpoints
│       ├── user_routes.py   # User profile endpoints
│       ├── video_routes.py  # Video analysis endpoints
│       └── webhook_routes.py # External webhook handlers
│
├── agents/                   # AI processing agents
│   ├── base_agent.py        # Abstract base agent class
│   ├── video_agent.py       # Video analysis with Gemini AI
│   └── audio_agent.py       # Audio transcription & analysis
│
├── core/                     # Core application components
│   ├── config.py            # Application configuration
│   ├── auth.py              # Authentication middleware
│   ├── exceptions.py        # Custom exception classes
│   └── middleware.py        # Request/response middleware
│
├── db/                       # Database layer
│   ├── base.py              # Database connection management
│   ├── models/              # SQLAlchemy model definitions
│   │   ├── clips.py        # Video clips data model
│   │   ├── jobs.py         # Processing jobs model
│   │   └── users.py        # User data model
│   └── repositories/        # Data access layer
│       ├── clips_repository.py
│       ├── jobs_repository.py
│       └── users_repository.py
│
├── services/                 # Business logic layer
│   ├── agent_service.py     # AI agent coordination
│   ├── audio_service.py     # Audio processing pipeline
│   ├── video_service.py     # Video processing pipeline
│   ├── video_worker.py      # Async job processor
│   ├── sieve_service.py     # External API integration
│   ├── queue/               # Queue management system
│   │   ├── manager.py      # Job queue orchestration
│   │   ├── tier_manager.py # Subscription tier handling
│   │   └── usage_tracker.py # Usage analytics & limits
│   └── video/               # Video-specific services
│       ├── processor/       # Core video processing
│       ├── ai_client/       # AI model integration
│       ├── metadata.py      # Video metadata extraction
│       └── sanitizer.py     # URL/URI sanitization
│
├── utils/                    # Utility functions
│   ├── logging.py           # Structured logging setup
│   ├── errors.py            # Error handling utilities
│   └── gcp.py               # Google Cloud Platform helpers
│
├── migrations/               # Database migrations
│   └── versions/            # Alembic migration files
│
```

---


### Prerequisites

- **Python 3.11+** with pip
- **PostgreSQL 15+** (local or cloud)
- **Redis 7+** (local or cloud)
- **FFmpeg** installed and in PATH
- **Google Cloud SDK**

## 🔌 API Endpoints

### Core Video Analysis

```http
POST /api/klair/analyze
```
Submit video for AI analysis with optional parameters:

```http
GET /api/klair/status/{task_id}
```
Get real-time processing status with progress updates.

```http
GET /api/klair/results/{task_id}
```
Retrieve analysis results with generated clips and insights.

### Audio Analysis

```http
POST /api/klair/analyze/audio
```
Analyze audio content with transcription and insights.

### Job Management

```http
GET /api/klair/jobs
```
List user's analysis jobs with filtering and pagination.

```http
DELETE /api/klair/jobs/{job_id}
```
Delete analysis job and associated data.

### User Management

```http
GET /api/klair/user/usage
```
Get usage statistics and tier information.

```http
GET /api/klair/user/stats
```
Comprehensive user analytics and activity.

### File Operations

```http
POST /api/upload-url
```
Generate presigned URLs for direct file uploads.

```http
POST /api/klair/export
```
Export clips with custom formatting options.

### Webhooks

```http
POST /webhooks/sieve/autocrop
```
Handle Sieve processing completion callbacks.

```http
POST /webhooks/clerk
```
Process Clerk authentication events.

---

## 🔧 Core Services

### Video Processing Pipeline

```python
# services/video_service.py
class VideoService:
    async def process_video(self, video_url: str, context: Dict) -> Dict:
        """Complete video processing workflow"""
        # 1. Download/validate video
        # 2. Extract metadata
        # 3. Upload to cloud storage
        # 4. Queue for AI analysis
        # 5. Generate clips
        # 6. Apply enhancements
```

### AI Agent Coordination

```python
# agents/video_agent.py
class VideoAgent(BaseAgent):
    async def analyze(self, video_uri: str, metadata: Dict) -> Dict:
        """Multimodal video analysis with Gemini AI"""
        # 1. Chunk video for processing
        # 2. Analyze visual content
        # 3. Extract audio for transcription
        # 4. Generate insights and clip recommendations
```

### Queue Management

```python
# services/queue/manager.py
class QueueManager:
    async def enqueue_job(self, job_data: JobData) -> QueuePosition:
        """Add job to tier-based priority queue"""
        # 1. Validate user limits
        # 2. Calculate priority score
        # 3. Enqueue with metadata
        # 4. Return position estimate
```

### Usage Tracking

```python
# services/queue/usage_tracker.py
class UsageTracker:
    def check_usage_limit(self, user_id: str, duration: int) -> Tuple[bool, Dict]:
        """Enforce tier-based usage limits"""
        # 1. Check current usage
        # 2. Validate against tier limits
        # 3. Update usage statistics
        # 4. Return availability status
```