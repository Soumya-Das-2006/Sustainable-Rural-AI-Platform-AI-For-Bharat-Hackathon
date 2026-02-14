# Design Document: Camera-to-Decision AI for Sustainable Rural Agriculture

## 1. System Architecture Overview

The Camera-to-Decision AI platform is built on a hybrid cloud-edge architecture that prioritizes offline-first functionality while leveraging cloud capabilities for synchronization, analytics, and model updates. The system employs a three-tier architecture:

1. **Mobile Edge Layer**: On-device AI inference, local data storage, and offline-first functionality
2. **Cloud Backend Layer**: Centralized data management, model training, and API services
3. **Integration Layer**: External services for weather, market prices, and government schemes

**Core Architectural Principles:**
- **Offline-First**: All critical features work without internet connectivity
- **Progressive Enhancement**: Cloud features enhance but don't block core functionality
- **Lightweight Design**: Optimized for low-end devices and limited bandwidth
- **Scalable Infrastructure**: Auto-scaling cloud resources based on demand
- **Security by Design**: End-to-end encryption and secure authentication

## 2. High-Level Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                        MOBILE APP (React Native)                 │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          │
│  │   Camera     │  │  Voice UI    │  │  Offline DB  │          │
│  │   Module     │  │   Module     │  │   (SQLite)   │          │
│  └──────────────┘  └──────────────┘  └──────────────┘          │
│  ┌──────────────────────────────────────────────────┐          │
│  │         On-Device AI Model (TensorFlow Lite)      │          │
│  │    CNN: MobileNet/EfficientNet for NPK Detection  │          │
│  └──────────────────────────────────────────────────┘          │
└─────────────────────────────────────────────────────────────────┘
                              ↕ (Sync when online)
┌─────────────────────────────────────────────────────────────────┐
│                      AWS CLOUD BACKEND                           │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          │
│  │  API Gateway │  │   EC2/Lambda │  │   S3 Storage │          │
│  │   (REST)     │  │  (FastAPI)   │  │  (Images)    │          │
│  └──────────────┘  └──────────────┘  └──────────────┘          │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          │
│  │   MongoDB    │  │  SageMaker   │  │   CloudWatch │          │
│  │  (Database)  │  │ (ML Training)│  │  (Monitoring)│          │
│  └──────────────┘  └──────────────┘  └──────────────┘          │
└─────────────────────────────────────────────────────────────────┘
                              ↕
┌─────────────────────────────────────────────────────────────────┐
│                    EXTERNAL INTEGRATIONS                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          │
│  │   Weather    │  │    Market    │  │  Government  │          │
│  │     APIs     │  │   Price APIs │  │  Scheme APIs │          │
│  └──────────────┘  └──────────────┘  └──────────────┘          │
└─────────────────────────────────────────────────────────────────┘
```

## 3. Component Breakdown

### 3.1 Frontend - Mobile Application

**Technology**: React Native (Cross-platform iOS/Android)

**Key Modules:**


**1. Camera Module**
- Captures high-quality leaf images using device camera
- Provides image preview and retake functionality
- Implements image preprocessing (resize, normalize, crop)
- Supports batch image capture for multiple leaves
- Includes image quality validation

**2. AI Inference Engine**
- Runs TensorFlow Lite models on-device
- Performs NPK deficiency detection from leaf images
- Executes disease and pest identification
- Provides confidence scores for predictions
- Handles model updates when online

**3. Voice Interface Module**
- Implements speech-to-text for voice commands
- Provides text-to-speech for responses
- Supports 10+ Indian regional languages
- Works offline with on-device speech recognition
- Handles agricultural terminology and local dialects

**4. Offline Data Manager**
- SQLite database for local data persistence
- Stores farmer profiles, crop history, and diagnoses
- Queues actions for sync when online
- Manages conflict resolution for sync
- Implements data compression for storage efficiency

**5. Sync Manager**
- Detects network connectivity changes
- Uploads queued data to cloud when online
- Downloads model updates and new content
- Handles partial sync and resume
- Provides sync status indicators

**6. UI/UX Components**
- Material Design components for consistency
- Icon-driven navigation for low-literacy users
- Multilingual text rendering
- Accessibility features (large fonts, high contrast)
- Contextual help and tutorials

### 3.2 Backend - Cloud Services

**Technology**: Python Django + FastAPI

**Key Services:**

**1. Authentication Service**
- Phone number + OTP based authentication
- JWT token management
- Role-based access control (Farmer, NGO, Admin)
- Session management
- Password reset and account recovery

**2. Crop Diagnosis API**
- Receives leaf images from mobile app
- Performs cloud-based AI inference (backup to on-device)
- Stores diagnosis history
- Generates detailed reports
- Provides confidence scores and explanations

**3. Recommendation Engine**
- Calculates precise fertilizer dosages
- Generates irrigation schedules
- Provides crop-specific advisories
- Considers weather forecasts
- Personalizes based on farmer history

**4. Marketplace Service**
- Manages product listings (crops, equipment, seeds)
- Handles buyer-seller matching
- Processes orders and transactions
- Implements price discovery algorithms
- Tracks transaction history

**5. Analytics Service**
- Aggregates farmer data for insights
- Generates sustainability impact reports
- Provides yield prediction models
- Creates regional trend analysis
- Exports data for government/NGO dashboards

**6. Notification Service**
- Sends push notifications to mobile app
- Implements SMS fallback for offline users
- Schedules alerts for irrigation, fertilization
- Sends weather warnings
- Delivers market price updates

**7. Integration Service**
- Connects to weather APIs
- Fetches market price data
- Integrates government scheme databases
- Manages third-party API credentials
- Handles API rate limiting and caching

### 3.3 Database Layer

**Primary Database**: MongoDB (Cloud)

**Reasons for MongoDB:**
- Flexible schema for diverse crop and farmer data
- Horizontal scalability for growing user base
- Geospatial queries for location-based features
- Rich query capabilities for analytics
- JSON-like documents match mobile app data structure

**Local Database**: SQLite (Mobile)

**Reasons for SQLite:**
- Lightweight and embedded in mobile app
- Zero-configuration for offline functionality
- ACID compliance for data integrity
- Efficient for read-heavy operations
- Easy synchronization with cloud database

### 3.4 External Integrations

**1. Weather APIs**
- OpenWeatherMap or IMD (India Meteorological Department)
- Provides 7-day weather forecasts
- Delivers rainfall predictions
- Sends extreme weather alerts
- Supports location-based queries

**2. Market Price APIs**
- Agmarknet (Government of India)
- Provides real-time mandi prices
- Delivers commodity price trends
- Supports multi-crop price data
- Enables price comparison across regions

**3. Government Scheme APIs**
- PM-KISAN, Soil Health Card, Kisan Credit Card
- Provides scheme eligibility criteria
- Delivers application procedures
- Tracks subsidy disbursement
- Enables direct scheme application

**4. Payment Gateway**
- Razorpay or Paytm for transactions
- Supports UPI, cards, wallets
- Handles escrow for marketplace
- Provides transaction receipts
- Ensures PCI-DSS compliance

## 4. Data Design

### 4.1 Core Entities and Models

**1. User (Farmer)**
```json
{
  "_id": "ObjectId",
  "phone_number": "string (unique)",
  "name": "string",
  "language_preference": "string (enum)",
  "location": {
    "state": "string",
    "district": "string",
    "village": "string",
    "coordinates": {"lat": "float", "lng": "float"}
  },
  "farm_details": {
    "total_area": "float (acres)",
    "soil_type": "string",
    "irrigation_type": "string"
  },
  "created_at": "datetime",
  "last_active": "datetime",
  "profile_complete": "boolean"
}
```

**2. Crop**
```json
{
  "_id": "ObjectId",
  "farmer_id": "ObjectId (ref: User)",
  "crop_type": "string",
  "variety": "string",
  "area": "float (acres)",
  "sowing_date": "date",
  "expected_harvest_date": "date",
  "growth_stage": "string (enum)",
  "status": "string (enum: active, harvested, failed)",
  "created_at": "datetime"
}
```

**3. Diagnosis**
```json
{
  "_id": "ObjectId",
  "farmer_id": "ObjectId (ref: User)",
  "crop_id": "ObjectId (ref: Crop)",
  "image_url": "string (S3 path)",
  "diagnosis_type": "string (enum: npk, disease, pest)",
  "results": {
    "nitrogen_status": "string (enum: deficient, adequate, excess)",
    "phosphorus_status": "string",
    "potassium_status": "string",
    "confidence_score": "float (0-1)",
    "detected_issues": ["array of strings"]
  },
  "recommendations": {
    "fertilizer": {
      "npk_ratio": "string",
      "quantity_per_acre": "float",
      "application_method": "string",
      "timing": "string"
    },
    "irrigation": {
      "frequency": "string",
      "quantity": "float (liters)",
      "next_irrigation_date": "date"
    },
    "preventive_measures": ["array of strings"]
  },
  "diagnosis_date": "datetime",
  "model_version": "string"
}
```

**4. Marketplace Listing**
```json
{
  "_id": "ObjectId",
  "seller_id": "ObjectId (ref: User)",
  "listing_type": "string (enum: produce, equipment, seed)",
  "item_details": {
    "name": "string",
    "category": "string",
    "quantity": "float",
    "unit": "string",
    "quality_grade": "string",
    "images": ["array of S3 URLs"]
  },
  "pricing": {
    "price_per_unit": "float",
    "negotiable": "boolean",
    "minimum_order": "float"
  },
  "location": {
    "district": "string",
    "village": "string",
    "coordinates": {"lat": "float", "lng": "float"}
  },
  "status": "string (enum: active, sold, expired)",
  "created_at": "datetime",
  "expires_at": "datetime"
}
```

**5. Transaction**
```json
{
  "_id": "ObjectId",
  "buyer_id": "ObjectId (ref: User)",
  "seller_id": "ObjectId (ref: User)",
  "listing_id": "ObjectId (ref: Marketplace Listing)",
  "transaction_type": "string (enum: produce_sale, equipment_rental, seed_purchase)",
  "amount": "float",
  "quantity": "float",
  "payment_status": "string (enum: pending, completed, failed, refunded)",
  "payment_method": "string",
  "transaction_date": "datetime",
  "delivery_status": "string (enum: pending, in_transit, delivered)"
}
```

**6. Sustainability Metrics**
```json
{
  "_id": "ObjectId",
  "farmer_id": "ObjectId (ref: User)",
  "period": "string (monthly, seasonal, annual)",
  "metrics": {
    "water_saved": "float (liters)",
    "fertilizer_reduced": "float (kg)",
    "carbon_footprint_reduction": "float (kg CO2)",
    "yield_improvement": "float (percentage)",
    "cost_savings": "float (INR)"
  },
  "calculated_at": "datetime"
}
```

### 4.2 Entity Relationships

```
User (Farmer) 1:N Crop
User (Farmer) 1:N Diagnosis
User (Farmer) 1:N Marketplace Listing
User (Farmer) 1:N Transaction (as buyer or seller)
User (Farmer) 1:1 Sustainability Metrics (per period)
Crop 1:N Diagnosis
Marketplace Listing 1:N Transaction
```

## 5. API Design

### 5.1 Authentication APIs

**POST /api/v1/auth/send-otp**
```json
Request:
{
  "phone_number": "+919876543210"
}

Response:
{
  "success": true,
  "message": "OTP sent successfully",
  "otp_expires_in": 300
}
```

**POST /api/v1/auth/verify-otp**
```json
Request:
{
  "phone_number": "+919876543210",
  "otp": "123456"
}

Response:
{
  "success": true,
  "access_token": "jwt_token_here",
  "refresh_token": "refresh_token_here",
  "user": {
    "id": "user_id",
    "name": "Farmer Name",
    "phone_number": "+919876543210"
  }
}
```

### 5.2 Diagnosis APIs

**POST /api/v1/diagnosis/analyze**
```json
Request (multipart/form-data):
{
  "image": "file (leaf image)",
  "crop_id": "crop_id_here",
  "diagnosis_type": "npk"
}

Response:
{
  "success": true,
  "diagnosis_id": "diagnosis_id_here",
  "results": {
    "nitrogen_status": "deficient",
    "phosphorus_status": "adequate",
    "potassium_status": "deficient",
    "confidence_score": 0.92
  },
  "recommendations": {
    "fertilizer": {
      "npk_ratio": "20-10-20",
      "quantity_per_acre": 25.5,
      "application_method": "Broadcast and incorporate",
      "timing": "Apply within 3 days"
    },
    "irrigation": {
      "frequency": "Every 5 days",
      "quantity": 500,
      "next_irrigation_date": "2026-02-17"
    }
  },
  "processing_time_ms": 4200
}
```

**GET /api/v1/diagnosis/history**
```json
Request Query Params:
{
  "crop_id": "crop_id_here",
  "limit": 10,
  "offset": 0
}

Response:
{
  "success": true,
  "total_count": 45,
  "diagnoses": [
    {
      "id": "diagnosis_id",
      "diagnosis_date": "2026-02-10T10:30:00Z",
      "diagnosis_type": "npk",
      "results": {...},
      "image_url": "https://s3.amazonaws.com/..."
    }
  ]
}
```

### 5.3 Crop Management APIs

**POST /api/v1/crops**
```json
Request:
{
  "crop_type": "wheat",
  "variety": "HD-2967",
  "area": 2.5,
  "sowing_date": "2025-11-15"
}

Response:
{
  "success": true,
  "crop": {
    "id": "crop_id_here",
    "crop_type": "wheat",
    "variety": "HD-2967",
    "area": 2.5,
    "sowing_date": "2025-11-15",
    "expected_harvest_date": "2026-04-15",
    "growth_stage": "vegetative"
  }
}
```

**GET /api/v1/crops/{crop_id}/health-trends**
```json
Response:
{
  "success": true,
  "crop_id": "crop_id_here",
  "health_trends": [
    {
      "date": "2026-01-15",
      "health_score": 85,
      "nitrogen_level": "adequate",
      "phosphorus_level": "adequate",
      "potassium_level": "adequate"
    },
    {
      "date": "2026-02-01",
      "health_score": 72,
      "nitrogen_level": "deficient",
      "phosphorus_level": "adequate",
      "potassium_level": "deficient"
    }
  ],
  "current_health_score": 72,
  "trend": "declining"
}
```

### 5.4 Marketplace APIs

**POST /api/v1/marketplace/listings**
```json
Request:
{
  "listing_type": "produce",
  "item_details": {
    "name": "Wheat",
    "category": "grain",
    "quantity": 500,
    "unit": "kg",
    "quality_grade": "A"
  },
  "pricing": {
    "price_per_unit": 25.50,
    "negotiable": true,
    "minimum_order": 50
  }
}

Response:
{
  "success": true,
  "listing": {
    "id": "listing_id_here",
    "status": "active",
    "created_at": "2026-02-12T14:30:00Z",
    "expires_at": "2026-03-12T14:30:00Z"
  }
}
```

**GET /api/v1/marketplace/listings**
```json
Request Query Params:
{
  "listing_type": "produce",
  "category": "grain",
  "location": "district_name",
  "max_distance_km": 50,
  "limit": 20,
  "offset": 0
}

Response:
{
  "success": true,
  "total_count": 156,
  "listings": [
    {
      "id": "listing_id",
      "seller_name": "Farmer Name",
      "item_details": {...},
      "pricing": {...},
      "distance_km": 12.5,
      "created_at": "2026-02-10T10:00:00Z"
    }
  ]
}
```

### 5.5 Sustainability APIs

**GET /api/v1/sustainability/metrics**
```json
Request Query Params:
{
  "period": "seasonal"
}

Response:
{
  "success": true,
  "period": "seasonal",
  "metrics": {
    "water_saved": 15000,
    "fertilizer_reduced": 125.5,
    "carbon_footprint_reduction": 450.2,
    "yield_improvement": 18.5,
    "cost_savings": 8500
  },
  "badges_earned": ["Water Warrior", "Eco Farmer"],
  "regional_rank": 45,
  "total_farmers": 2500
}
```

## 6. Technology Stack

### 6.1 Mobile Application

**Framework**: React Native 0.72+
- **Justification**: Cross-platform development (iOS/Android), large community, excellent performance, hot reload for faster development

**UI Library**: React Native Paper (Material Design)
- **Justification**: Consistent Material Design components, accessibility support, customizable theming

**State Management**: Redux Toolkit
- **Justification**: Predictable state management, excellent DevTools, middleware support for async operations

**Local Database**: SQLite with react-native-sqlite-storage
- **Justification**: Lightweight, ACID compliant, excellent offline support, zero configuration

**AI/ML**: TensorFlow Lite for React Native
- **Justification**: On-device inference, optimized for mobile, supports quantized models, <50MB model size

**Camera**: react-native-camera
- **Justification**: Full camera control, image preprocessing, barcode scanning for seed verification

**Voice**: react-native-voice + react-native-tts
- **Justification**: Offline speech recognition, multilingual support, text-to-speech for accessibility

**Maps**: react-native-maps
- **Justification**: Location-based features, marketplace distance calculation, farm boundary mapping

### 6.2 Backend Services

**Framework**: FastAPI (Python 3.10+)
- **Justification**: High performance, async support, automatic API documentation, type hints, easy integration with ML models

**ORM**: Motor (async MongoDB driver)
- **Justification**: Async operations for better performance, native MongoDB support, Pythonic API

**Authentication**: PyJWT + Twilio (OTP)
- **Justification**: Secure JWT tokens, reliable OTP delivery, phone number authentication for rural users

**Image Processing**: Pillow + OpenCV
- **Justification**: Image preprocessing, quality validation, format conversion, thumbnail generation

**ML Framework**: TensorFlow 2.x + Keras
- **Justification**: Industry standard, excellent documentation, model optimization tools, TensorFlow Lite export

**Task Queue**: Celery + Redis
- **Justification**: Async task processing, scheduled jobs (alerts, sync), distributed task execution

**API Documentation**: Swagger/OpenAPI (auto-generated by FastAPI)
- **Justification**: Interactive API testing, automatic documentation, client SDK generation

### 6.3 Cloud Infrastructure (AWS)

**Compute**: 
- EC2 t3.medium instances (API servers)
- Lambda functions (serverless tasks)
- **Justification**: Cost-effective, auto-scaling, pay-per-use for Lambda

**Storage**:
- S3 (image storage, model files)
- EBS (database volumes)
- **Justification**: Durable, scalable, low-cost for large files

**Database**:
- MongoDB Atlas (managed MongoDB)
- **Justification**: Managed service, automatic backups, global clusters, built-in monitoring

**ML Services**:
- SageMaker (model training and deployment)
- **Justification**: Managed Jupyter notebooks, distributed training, model hosting, A/B testing

**Networking**:
- API Gateway (REST API management)
- CloudFront (CDN for static assets)
- **Justification**: Rate limiting, caching, DDoS protection, global content delivery

**Monitoring**:
- CloudWatch (logs and metrics)
- X-Ray (distributed tracing)
- **Justification**: Centralized logging, performance monitoring, alerting, debugging

**Security**:
- IAM (access management)
- Secrets Manager (API keys, credentials)
- **Justification**: Fine-grained permissions, encrypted secrets, audit trails

### 6.4 DevOps & Deployment

**Containerization**: Docker
- **Justification**: Consistent environments, easy deployment, microservices architecture

**Orchestration**: Docker Compose (MVP), Kubernetes (production)
- **Justification**: Service orchestration, auto-scaling, self-healing, rolling updates

**CI/CD**: GitHub Actions
- **Justification**: Integrated with GitHub, free for open source, easy configuration, parallel jobs

**Version Control**: Git + GitHub
- **Justification**: Industry standard, collaboration features, issue tracking, code review

**Monitoring**: Prometheus + Grafana
- **Justification**: Time-series metrics, custom dashboards, alerting, open source

## 7. Security Considerations

### 7.1 Authentication & Authorization

**Phone Number + OTP Authentication**:
- Implements rate limiting (max 3 OTP requests per hour)
- OTP expires after 5 minutes
- Uses Twilio for reliable SMS delivery
- Stores phone numbers in hashed format

**JWT Token Management**:
- Access tokens expire after 1 hour
- Refresh tokens expire after 30 days
- Tokens include user role and permissions
- Implements token blacklisting for logout

**Role-Based Access Control (RBAC)**:
- Farmer: Access to own data, marketplace, diagnosis
- NGO: Access to farmer data (with consent), analytics
- Admin: Full system access, user management
- Implements least privilege principle

### 7.2 Data Protection

**Encryption at Rest**:
- MongoDB encryption enabled
- S3 bucket encryption (AES-256)
- SQLite database encryption on mobile
- Secrets Manager for API keys

**Encryption in Transit**:
- TLS 1.3 for all API communications
- Certificate pinning in mobile app
- HTTPS only, no HTTP fallback

**Data Privacy**:
- Farmer data anonymized for analytics
- Implements data retention policies (7 years)
- Provides data export and deletion (GDPR-like)
- Consent management for data sharing

### 7.3 API Security

**Rate Limiting**:
- 100 requests per minute per user
- 1000 requests per hour per IP
- Stricter limits for OTP and authentication endpoints

**Input Validation**:
- Schema validation for all API requests
- Image file type and size validation
- SQL injection prevention (NoSQL, but still validates)
- XSS prevention in user-generated content

**API Authentication**:
- Bearer token authentication for all protected endpoints
- API key authentication for external integrations
- Implements CORS with whitelist

### 7.4 Mobile App Security

**Code Obfuscation**:
- ProGuard for Android
- Hermes bytecode for React Native
- Prevents reverse engineering

**Secure Storage**:
- Keychain (iOS) / Keystore (Android) for sensitive data
- Encrypted SQLite database
- No sensitive data in logs

**Certificate Pinning**:
- Pins SSL certificates to prevent MITM attacks
- Validates server certificates

## 8. Scalability & Performance Strategy

### 8.1 Horizontal Scaling

**API Servers**:
- Stateless design for easy horizontal scaling
- Load balancer distributes traffic across instances
- Auto-scaling based on CPU and memory metrics
- Target: Support 10,000+ concurrent users

**Database Scaling**:
- MongoDB sharding for horizontal partitioning
- Read replicas for read-heavy operations
- Indexes on frequently queried fields
- Target: Handle 1 million+ farmer profiles

### 8.2 Caching Strategy

**Application-Level Caching**:
- Redis for session data and frequently accessed data
- Cache weather forecasts (1 hour TTL)
- Cache market prices (15 minutes TTL)
- Cache government schemes (24 hours TTL)

**CDN Caching**:
- CloudFront for static assets (images, models)
- Edge caching for API responses (where appropriate)
- Reduces latency for global users

### 8.3 Performance Optimization

**Mobile App**:
- Lazy loading for screens and components
- Image compression before upload
- Pagination for large lists
- Background sync for non-critical data
- Target: <3 second app launch time

**AI Model**:
- Quantized TensorFlow Lite models (<50MB)
- On-device inference (<5 seconds)
- Model caching to avoid re-downloads
- Batch processing for cloud inference

**API Response Times**:
- Database query optimization with indexes
- Async processing for heavy operations
- Response compression (gzip)
- Target: <500ms for 95th percentile

### 8.4 Offline Functionality

**Offline-First Architecture**:
- All core features work without internet
- Local SQLite database for data persistence
- On-device AI model for diagnosis
- Queue-based sync when online

**Sync Strategy**:
- Incremental sync (only changed data)
- Conflict resolution (last-write-wins with user prompt)
- Background sync when app is idle
- Retry mechanism for failed syncs

## 9. Deployment Architecture

### 9.1 Environment Setup

**Development Environment**:
- Local Docker containers for backend services
- MongoDB local instance
- React Native development server
- Hot reload for rapid development

**Staging Environment**:
- AWS EC2 instances (t3.small)
- MongoDB Atlas (M10 cluster)
- Mirrors production architecture
- Used for testing and QA

**Production Environment**:
- AWS EC2 instances (t3.medium, auto-scaling)
- MongoDB Atlas (M30 cluster, multi-region)
- CloudFront CDN
- Load balancer with health checks

### 9.2 Deployment Pipeline

**CI/CD Workflow**:
1. Developer pushes code to GitHub
2. GitHub Actions triggers automated tests
3. Build Docker images for backend services
4. Build React Native APK/IPA for mobile app
5. Run integration tests
6. Deploy to staging environment
7. Manual approval for production deployment
8. Deploy to production with rolling updates
9. Monitor deployment with CloudWatch

**Rollback Strategy**:
- Blue-green deployment for zero-downtime
- Automated rollback on health check failures
- Database migration rollback scripts
- Mobile app version compatibility checks

### 9.3 Monitoring & Alerting

**Application Monitoring**:
- CloudWatch for logs and metrics
- Custom metrics for business KPIs
- Error tracking with Sentry
- Performance monitoring with X-Ray

**Infrastructure Monitoring**:
- EC2 instance health checks
- Database performance metrics
- API response time monitoring
- Disk space and memory alerts

**Alerting**:
- PagerDuty for critical alerts
- Slack notifications for warnings
- Email alerts for daily summaries
- SMS alerts for production outages

### 9.4 Disaster Recovery

**Backup Strategy**:
- MongoDB automated daily backups (7-day retention)
- S3 versioning for image storage
- Database point-in-time recovery
- Configuration backups in Git

**Recovery Plan**:
- RTO (Recovery Time Objective): 4 hours
- RPO (Recovery Point Objective): 24 hours
- Documented recovery procedures
- Quarterly disaster recovery drills

---

**Document Version**: 1.0  
**Last Updated**: February 12, 2026  
**Project**: Camera-to-Decision AI for Sustainable Rural Agriculture  
**Team**: The Sensing Squad  
**Hackathon**: AWS AI for Bharat
