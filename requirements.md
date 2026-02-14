# Requirements Specification
## Camera-to-Decision AI for Sustainable Rural Agriculture

**Project Name:** The Sensing Squad - Rural Agriculture AI Platform  
**Version:** 1.0  
**Date:** February 12, 2026  
**Team Leader:** Soumya Das  

---

## 1. Project Overview

### 1.1 Purpose
To build a Camera-to-Decision AI platform that delivers expert-level agricultural intelligence directly to every farmer's smartphone, enabling data-driven, climate-smart, and sustainable farming across rural India.

### 1.2 Problem Being Solved
Over 60% of rural farmers face delayed crop diagnosis (7–15 days), leading to:
- 30–40% yield loss
- 20–25% fertilizer wastage
- Lack of expert access in rural areas
- High costs for soil testing (₹300–₹1000) with 10–20 day turnaround
- Limited accessibility due to low literacy and poor internet connectivity

### 1.3 Core Solution Statement
A mobile AI system that uses CNN-based leaf image analysis to detect NPK deficiencies in under 5 seconds, providing actionable fertilizer recommendations directly to farmers' smartphones — even in low or no internet environments.

### 1.4 Goals and Success Criteria

#### Primary Goals
1. Provide instant crop diagnosis (< 5 seconds) using smartphone cameras
2. Deliver actionable fertilizer and irrigation recommendations
3. Enable offline/low-internet operation for rural accessibility
4. Support voice-based, multilingual interaction
5. Create a unified platform for diagnosis, advisory, market access, and sustainability

#### Success Criteria
- **Yield Improvement:** 10–25% increase in crop yield
- **Resource Efficiency:** 20–25% reduction in fertilizer misuse
- **Water Conservation:** 15–30% water savings
- **Cost Reduction:** 15–20% reduction in input costs for small & marginal farmers
- **Early Intervention:** Prevent 30–40% potential yield loss
- **User Adoption:** Deployable for 100–500 farmers in pilot, scalable to 10,000+ farmers
- **Response Time:** Diagnosis delivered in under 5 seconds
- **Accessibility:** Support for illiterate and semi-literate farmers (70%+ of target users)

---

## 2. Stakeholders & Users

### 2.1 Primary Users

#### 2.1.1 Rural Farmers (Primary End Users)
- **Profile:** Small and marginal farmers with low-end smartphones
- **Characteristics:**
  - 70%+ illiterate or semi-literate
  - Limited or no internet connectivity (2G/3G areas)
  - Own Android smartphones (low to mid-range)
  - Regional language speakers
  - Limited technical expertise
- **Needs:**
  - Instant crop health diagnosis without expert dependency
  - Simple, voice-based interface
  - Offline functionality
  - Actionable recommendations in regional languages
  - Cost-effective solution requiring no additional hardware

#### 2.1.2 Agricultural Consultants/Experts
- **Profile:** Agronomists, field advisors, extension workers
- **Needs:**
  - Access to farmer data and trends
  - Ability to provide remote advisory
  - Dashboard for monitoring multiple farmers
  - Data-driven insights for better recommendations

#### 2.1.3 NGOs and Government Bodies
- **Profile:** Agricultural development organizations, policy makers
- **Needs:**
  - Community-level analytics
  - Integration with government schemes and subsidies
  - Impact tracking and reporting
  - Policy-level insights on farming practices

#### 2.1.4 Buyers and Market Participants
- **Profile:** Agricultural produce buyers, FPOs, cooperatives
- **Needs:**
  - Direct farmer connections
  - Crop quality information
  - Supply chain visibility
  - Market price transparency

### 2.2 Secondary Stakeholders

#### 2.2.1 System Administrators
- **Needs:**
  - Platform monitoring and management
  - User management and support
  - System analytics and performance tracking

#### 2.2.2 Equipment Rental Providers
- **Needs:**
  - Listing and booking management
  - Farmer connection
  - Payment processing

---

## 3. Functional Requirements

### 3.1 Core AI & Diagnosis Features

#### FR-1: AI-Based Crop Nutrient Diagnosis
**Priority:** Critical  
**Description:** Detect NPK (Nitrogen, Phosphorus, Potassium) deficiencies from leaf images in under 5 seconds.

**User Stories:**
- As a farmer, I want to take a photo of my crop leaf, so that I can instantly know if my crop has nutrient deficiencies.
- As a farmer, I want to see a confidence score (0–100%) with the diagnosis, so that I understand how reliable the result is.
- As a farmer, I want the diagnosis to work offline, so that I can use it even without internet access.

**Acceptance Criteria:**
- Image analysis completes in < 5 seconds
- Supports NPK deficiency detection
- Returns confidence score between 0–100%
- Works with smartphone camera images (varying quality and lighting)
- Functions in offline mode with auto-sync when internet available

#### FR-2: Crop Disease & Pest Detection
**Priority:** High  
**Description:** Use image-based AI to detect diseases and pests early to reduce crop damage.

**User Stories:**
- As a farmer, I want to detect crop diseases early, so that I can prevent significant yield loss.
- As a farmer, I want pest identification from leaf images, so that I can take appropriate control measures.

**Acceptance Criteria:**
- Detects common crop diseases from leaf images
- Identifies prevalent pest infestations
- Provides disease/pest confidence scores
- Returns severity assessment (low, medium, high)

#### FR-3: Early Crop Health Monitoring
**Priority:** High  
**Description:** Track crop health trends over time to detect stress early.

**User Stories:**
- As a farmer, I want to monitor my crop health over the season, so that I can identify problems before they become severe.
- As a farmer, I want to see health trends, so that I can understand if my interventions are working.

**Acceptance Criteria:**
- Tracks multiple crop health assessments over time
- Visualizes health trends (improving, stable, declining)
- Provides seasonal productivity insights (10–25% improvement target)
- Alerts on significant health deterioration

### 3.2 Decision Support & Recommendations

#### FR-4: Precision Fertilizer Recommendation System
**Priority:** Critical  
**Description:** Provide exact NPK dosage based on AI analysis of crop nutrient deficiencies.

**User Stories:**
- As a farmer, I want exact fertilizer quantities, so that I don't waste money on unnecessary inputs.
- As a farmer, I want to know which specific fertilizers to use, so that I can address my crop's exact needs.

**Acceptance Criteria:**
- Recommends specific NPK quantities in kg/acre or kg/hectare
- Suggests specific fertilizer products available locally
- Reduces fertilizer misuse by 20–25%
- Provides application timing recommendations

#### FR-5: Smart Irrigation Scheduler
**Priority:** High  
**Description:** Optimize irrigation timing and quantity based on crop stage, weather, and soil conditions.

**User Stories:**
- As a farmer, I want to know when and how much to irrigate, so that I can save water while maintaining crop health.
- As a farmer, I want irrigation alerts, so that I don't forget critical watering schedules.

**Acceptance Criteria:**
- Recommends irrigation schedule (timing and quantity)
- Integrates weather data for decision making
- Targets 15–30% water savings
- Sends timely irrigation reminders

#### FR-6: Crop Advisory & Preventive Measures
**Priority:** High  
**Description:** Deliver actionable post-diagnosis guidance to improve crop resilience.

**User Stories:**
- As a farmer, I want preventive measures after diagnosis, so that I can avoid the same problems in future.
- As a farmer, I want step-by-step action plans, so that I know exactly what to do.

**Acceptance Criteria:**
- Provides actionable next steps after each diagnosis
- Includes preventive measures for common issues
- Offers crop stage-specific guidance
- Reduces repeat stress occurrences

### 3.3 Market Access & Resource Management

#### FR-7: Virtual Mandi (Digital Marketplace)
**Priority:** Medium  
**Description:** Connect farmers directly to buyers for better price discovery and income.

**User Stories:**
- As a farmer, I want to sell my produce directly to buyers, so that I can get better prices.
- As a buyer, I want to connect directly with farmers, so that I can source quality produce.

**Acceptance Criteria:**
- Lists farmer produce with quantity, quality, and location
- Enables buyer-farmer communication
- Supports price negotiation
- Targets 10–20% income increase through better pricing

#### FR-8: Agri-Equipment Rental System
**Priority:** Medium  
**Description:** Enable on-demand access to farm machinery without ownership costs.

**User Stories:**
- As a farmer, I want to rent equipment only when needed, so that I can avoid high ownership costs.
- As an equipment owner, I want to list my machinery for rent, so that I can generate additional income.

**Acceptance Criteria:**
- Lists available equipment with rental rates
- Supports booking and scheduling
- Includes location-based search
- Targets 40–60% cost reduction vs. ownership

#### FR-9: Seed Quality Verification System
**Priority:** Medium  
**Description:** Verify seed authenticity digitally to prevent fake seeds.

**User Stories:**
- As a farmer, I want to verify seed quality before purchase, so that I don't lose my investment on fake seeds.

**Acceptance Criteria:**
- Supports seed batch verification via code/QR scan
- Connects to government/manufacturer databases
- Provides authenticity status and quality ratings
- Improves crop success rates

#### FR-10: Supply Chain & Storage Intelligence
**Priority:** Low  
**Description:** Monitor storage conditions to reduce post-harvest losses.

**User Stories:**
- As a farmer, I want storage recommendations, so that I can minimize post-harvest losses.

**Acceptance Criteria:**
- Provides storage best practices
- Monitors storage conditions (if data available)
- Targets 10–15% reduction in post-harvest losses

### 3.4 Sustainability Features

#### FR-11: Stubble Burning Alternatives
**Priority:** Medium  
**Description:** Suggest eco-friendly residue management and biomass linkages.

**User Stories:**
- As a farmer, I want alternatives to burning crop residue, so that I can comply with regulations and reduce pollution.

**Acceptance Criteria:**
- Lists alternative residue management methods
- Connects to biomass collection/buying services
- Provides economic comparison vs. burning
- Reduces air pollution from stubble burning

#### FR-12: Sustainability Impact Tracking
**Priority:** Medium  
**Description:** Track AI-driven reductions in water and fertilizer use with measurable climate impact.

**User Stories:**
- As a farmer, I want to see my environmental impact, so that I can understand my contribution to sustainability.
- As an NGO, I want aggregated sustainability metrics, so that I can report impact to stakeholders.

**Acceptance Criteria:**
- Tracks water savings per farmer and in aggregate
- Tracks fertilizer reduction
- Visualizes environmental impact (CO2 equivalent, water saved)
- Provides farmer and community-level dashboards

### 3.5 User Experience & Accessibility

#### FR-13: Voice-First Agri Bot
**Priority:** Critical  
**Description:** Provide hands-free, regional-language guidance for illiterate/semi-literate farmers.

**User Stories:**
- As an illiterate farmer, I want to use voice commands, so that I can access the system without reading.
- As a farmer who speaks only regional language, I want voice support in my language, so that I can understand all features.

**Acceptance Criteria:**
- Supports Speech-to-Text (STT) and Text-to-Speech (TTS)
- Covers major regional languages (Hindi, Bengali, Telugu, Tamil, Marathi, Gujarati, Punjabi, Kannada, Malayalam, Odia)
- Provides voice navigation through all key features
- Works in offline mode with on-device processing

#### FR-14: Multilingual Interface
**Priority:** Critical  
**Description:** Simple, icon-driven UI in regional languages for better adoption.

**User Stories:**
- As a farmer, I want the app in my regional language, so that I can understand all information clearly.

**Acceptance Criteria:**
- Supports 10+ regional Indian languages
- Icon-driven interface for intuitive navigation
- Simple text with minimal jargon
- Language selection on first launch

#### FR-15: Offline / Low-Internet Mode
**Priority:** Critical  
**Description:** Works fully offline with auto-sync when connectivity returns.

**User Stories:**
- As a farmer in a remote area, I want the app to work without internet, so that I can use it anytime.
- As a farmer with intermittent connectivity, I want my data to sync automatically, so that I don't lose any information.

**Acceptance Criteria:**
- Core AI inference works offline (on-device models)
- Stores data locally in SQLite
- Auto-syncs to cloud when internet available
- Handles 2G/3G connectivity gracefully
- Queue-based sync for failed operations

#### FR-16: Farmer Profile Management
**Priority:** High  
**Description:** Store crop history and land data for personalized farming planning.

**User Stories:**
- As a farmer, I want my crop history saved, so that I can track my farm's performance over seasons.
- As a farmer, I want personalized recommendations, so that they are specific to my land and crops.

**Acceptance Criteria:**
- Stores farmer profile (name, contact, location)
- Records land details (area, soil type, water source)
- Maintains crop history across seasons
- Enables personalized recommendations based on history

#### FR-17: Alerts & Notifications
**Priority:** High  
**Description:** Send real-time alerts on crop health, irrigation, weather, and market risks.

**User Stories:**
- As a farmer, I want weather alerts, so that I can protect my crops from adverse conditions.
- As a farmer, I want market price alerts, so that I can sell at the best time.

**Acceptance Criteria:**
- Weather risk alerts (rain, drought, extreme temperature)
- Crop health deterioration alerts
- Irrigation schedule reminders
- Market price update notifications
- Targets 10–20% productivity improvement through timely alerts

### 3.6 Analytics & Insights

#### FR-18: Data Analytics Dashboard
**Priority:** Medium  
**Description:** Visualize yield trends and input efficiency for data-driven decisions.

**User Stories:**
- As a farmer, I want to see my farm performance trends, so that I can make better decisions.
- As an agricultural consultant, I want analytics on multiple farmers, so that I can provide better advisory services.
- As an NGO, I want community-level insights, so that I can design better interventions.

**Acceptance Criteria:**
- Farmer-level dashboard (yield, inputs, costs, savings)
- Expert dashboard (multiple farmer monitoring)
- Admin/NGO dashboard (community-level analytics)
- Visualizations: charts, graphs, trend lines
- Exportable reports (PDF, CSV)

### 3.7 Multi-Crop & Regional Expansion

#### FR-19: Multi-Crop & Multi-Region Support
**Priority:** High  
**Description:** Adapt AI models for different crops and regions using climate and soil-specific data.

**User Stories:**
- As a farmer growing wheat, I want wheat-specific diagnosis, so that recommendations are accurate for my crop.
- As a farmer in a different state, I want region-specific recommendations, so that they match my local climate and soil.

**Acceptance Criteria:**
- Support for multiple crops (wheat, rice, cotton, maize, pulses, vegetables)
- Regional model variations based on climate zones
- Soil-type specific recommendations
- Expandable model architecture for new crops

#### FR-20: Government & NGO Integration
**Priority:** Medium  
**Description:** Integrate schemes and subsidies directly into the platform.

**User Stories:**
- As a farmer, I want to know about relevant government schemes, so that I can access benefits I'm eligible for.
- As a government body, I want to distribute scheme information, so that more farmers can benefit.

**Acceptance Criteria:**
- Lists relevant central and state government schemes
- Filters schemes by farmer eligibility
- Provides application guidance and links
- Integrates with PM-KISAN, soil health card programs, etc.

---

## 4. Non-Functional Requirements

### 4.1 Performance

#### NFR-1: Response Time
- AI diagnosis must complete within 5 seconds
- App launch time < 3 seconds on low-end Android devices
- API response time < 2 seconds for 95% of requests
- Offline mode operates without latency

#### NFR-2: Throughput
- Support 10,000+ concurrent users during peak seasons
- Handle 100,000+ daily diagnoses at scale
- Process image uploads efficiently (< 5 MB each)

#### NFR-3: Resource Efficiency
- Mobile app size < 50 MB
- On-device AI models < 20 MB
- Low battery consumption (< 5% per hour of active use)
- Minimal data usage in online mode (< 10 MB per day)

### 4.2 Scalability

#### NFR-4: User Scalability
- Phase 1: Support 100–500 farmers (pilot)
- Phase 2: Support 10,000+ farmers
- Phase 3: Scale to 100,000+ farmers across multiple states

#### NFR-5: Geographic Scalability
- Start with 1–2 states in pilot
- Expand to 5–10 states in Phase 2
- Pan-India coverage in Phase 3

#### NFR-6: Feature Scalability
- Modular architecture for easy feature additions
- Support for new crops without major system changes
- Pluggable AI model architecture

### 4.3 Reliability

#### NFR-7: Availability
- 99.5% uptime for cloud services
- 100% availability for offline features
- Graceful degradation when services are unavailable

#### NFR-8: Data Integrity
- Zero data loss during sync operations
- Automatic conflict resolution for offline edits
- Regular automated backups

#### NFR-9: Fault Tolerance
- Auto-retry for failed API calls
- Queue-based sync for offline operations
- Fallback to cached data when APIs fail

### 4.4 Usability

#### NFR-10: Accessibility
- Support for illiterate users (70%+ of target audience)
- Voice-based navigation for all core features
- Icon-driven UI with minimal text
- Consistent with Android Material Design guidelines

#### NFR-11: Learning Curve
- New users can perform core diagnosis within 5 minutes
- Voice tutorial on first launch
- Contextual help throughout the app

#### NFR-12: Language Support
- Minimum 10 regional Indian languages
- Seamless language switching
- Culturally appropriate translations and terminology

### 4.5 Security

#### NFR-13: Authentication & Authorization
- Secure JWT-based authentication
- OAuth support for future integrations
- Role-based access control (Farmer, Expert, Admin, NGO)
- Session management with automatic timeout

#### NFR-14: Data Protection
- Encrypted data storage (AES-256)
- HTTPS for all network communications
- Secure API endpoints
- Farmer data ownership and privacy controls

#### NFR-15: Compliance
- GDPR-like data protection principles
- Farmer consent for data usage
- Right to data deletion
- Transparent data usage policies

### 4.6 Maintainability

#### NFR-16: Code Quality
- Modular, well-documented codebase
- Automated testing (unit, integration, E2E)
- Code coverage > 80%
- CI/CD pipelines for automated deployment

#### NFR-17: Monitoring & Logging
- Application performance monitoring
- Error tracking and alerts
- User analytics (privacy-preserving)
- System health dashboards

#### NFR-18: Updateability
- Over-the-air (OTA) updates for mobile app
- Zero-downtime backend deployments
- AI model updates without app updates

### 4.7 Portability

#### NFR-19: Platform Support
- Android 8.0+ (API level 26+)
- Low to mid-range Android devices (2GB+ RAM)
- Web portal for admins/experts (Chrome, Firefox, Safari)

#### NFR-20: Network Support
- 2G/3G/4G network compatibility
- Offline-first architecture
- Bandwidth optimization (< 10 MB/day in online mode)

---

## 5. Assumptions

### 5.1 User & Environment Assumptions
1. **Device Access:** Target farmers own or have access to Android smartphones (even low-end models)
2. **Camera Quality:** Smartphone cameras are sufficient for leaf image capture (minimum 5MP)
3. **Literacy:** Majority of users (70%+) are illiterate or semi-literate
4. **Internet:** Connectivity is intermittent or limited (2G/3G in most areas)
5. **Language:** Users prefer regional languages over English/Hindi
6. **Trust:** Farmers are willing to trust AI recommendations if explained clearly
7. **Adoption:** Voice-based and icon-driven UI will significantly improve adoption

### 5.2 Technical Assumptions
1. **AI Accuracy:** CNN models can achieve 85%+ accuracy for NPK deficiency detection with sufficient training data
2. **Model Size:** Lightweight models (< 20 MB) can perform on-device inference on low-end devices
3. **Data Availability:** Sufficient labeled crop image datasets are available or can be created
4. **API Access:** Weather, soil, and market data APIs are accessible and reliable
5. **Cloud Infrastructure:** AWS or equivalent cloud services provide sufficient scalability
6. **Open Source:** TensorFlow Lite, PyTorch Mobile, or similar frameworks support on-device inference

### 5.3 Business Assumptions
1. **Funding:** MVP and pilot can be funded through hackathon prizes, AWS credits, government grants, or CSR
2. **Partnerships:** NGOs, FPOs, and government bodies are willing to partner for farmer outreach
3. **Market Demand:** There is sufficient demand for such a solution among small and marginal farmers
4. **Monetization:** Freemium model with premium features or B2B partnerships can sustain operations post-pilot
5. **Expert Availability:** Agricultural experts are available for model validation and continuous improvement
6. **Government Support:** Integration with government schemes and databases is feasible

### 5.4 Data Assumptions
1. **Image Quality:** Farmers can capture reasonably clear leaf images despite varying lighting and camera quality
2. **Regional Variation:** AI models can be adapted for different crops and regions with transfer learning
3. **Data Privacy:** Farmers are comfortable sharing crop data if privacy is assured and benefits are clear
4. **Ground Truth:** Expert validation or lab tests can provide ground truth for model training and improvement

---

## 6. Constraints

### 6.1 Technical Constraints
1. **Device Limitations:** Must work on low-end Android devices with limited RAM (2GB) and storage
2. **Network Constraints:** Must function in 2G/3G areas with intermittent connectivity
3. **Model Size:** AI models must be < 20 MB for on-device inference
4. **Battery:** Cannot drain battery excessively (< 5% per hour of active use)
5. **Offline Requirement:** Core features must work completely offline

### 6.2 User Constraints
1. **Literacy:** Cannot rely on text-heavy interfaces
2. **Language:** Must support regional languages, not just English/Hindi
3. **Technical Expertise:** UI must be extremely simple for users with minimal smartphone experience
4. **Smartphone Access:** Not all farmers may have individual smartphone access

### 6.3 Budget Constraints
1. **MVP Budget:** ₹1.45 – ₹2.30 Lakhs
2. **Pilot Budget:** ₹1.20 – ₹2.00 Lakhs (additional)
3. **Annual Operating Cost:** ₹4 – ₹6 Lakhs at scale
4. **Hardware-Free:** Solution must not require additional hardware purchases by farmers

### 6.4 Time Constraints
1. **Hackathon Timeline:** MVP must be demonstrable within hackathon timeframe
2. **Pilot Deployment:** 3–6 months for initial pilot with 100–500 farmers
3. **Seasonal Dependency:** Must align with crop cycles for meaningful testing

### 6.5 Regulatory Constraints
1. **Data Privacy:** Must comply with Indian data protection regulations
2. **Agricultural Regulations:** Fertilizer and pesticide recommendations must align with government guidelines
3. **Market Operations:** Virtual Mandi must comply with APMC and e-NAM regulations

### 6.6 Resource Constraints
1. **Training Data:** Limited availability of labeled crop disease and nutrient deficiency images
2. **Expert Access:** Limited availability of agricultural experts for model validation
3. **Field Testing:** Access to diverse geographic and crop conditions for testing
4. **Infrastructure:** Rural areas may lack reliable internet infrastructure

---

## 7. Out of Scope

### 7.1 Features Explicitly Not Included in MVP/Pilot

1. **Advanced Predictive Analytics:**
   - Yield prediction models (deferred to post-hackathon roadmap)
   - Insurance advisory and claim support
   - Long-term climate impact modeling

2. **Hardware Integration:**
   - Soil sensors or IoT devices
   - Weather stations
   - Automated irrigation systems
   - Drone integration

3. **Financial Services:**
   - Microfinance or loan processing
   - Insurance product sales
   - Payment gateway integration (for MVP; may add in pilot)

4. **Advanced Market Features:**
   - Real-time commodity trading
   - Futures and options
   - International market access
   - Complex supply chain management

5. **Extensive Disease Library:**
   - Comprehensive coverage of all crop diseases (start with top 10–15 per crop)
   - Rare or exotic pests

6. **Advanced Sustainability Features:**
   - Carbon credit calculations
   - Detailed life cycle assessments
   - Biodiversity impact tracking

7. **Social Features:**
   - Farmer community forums
   - Social networking capabilities
   - Gamification and rewards

8. **Non-Agricultural Extensions:**
   - Livestock management
   - Poultry farming
   - Fisheries

### 7.2 Geographic/Crop Limitations in MVP/Pilot

1. **Crops:** Start with 3–5 major crops (wheat, rice, cotton, maize, pulses)
2. **Languages:** Start with 5–7 regional languages, expand later
3. **Geography:** Pilot in 1–2 states, expand based on results
4. **Diseases:** Cover top 10–15 diseases per crop in MVP

### 7.3 Future Enhancements (Post-Hackathon Roadmap)

1. **Advanced AI Features:**
   - Yield prediction
   - Price forecasting
   - Automated irrigation scheduling based on sensors

2. **Expanded Integrations:**
   - Government scheme direct applications
   - Bank account integration for subsidies
   - Insurance claim processing

3. **Community Features:**
   - Farmer-to-farmer knowledge sharing
   - Best practice videos and tutorials
   - Success story showcases

4. **Enterprise Features:**
   - Corporate buyer dashboards
   - Bulk procurement systems
   - Contract farming management

---

## 8. Success Metrics & KPIs

### 8.1 User Adoption Metrics
- Number of registered farmers
- Daily active users (DAU) and Monthly active users (MAU)
- User retention rate (weekly, monthly)
- Feature usage rates (diagnosis, advisory, market access)
- Geographic penetration

### 8.2 Performance Metrics
- Average diagnosis time (target: < 5 seconds)
- AI model accuracy (target: > 85%)
- App crash rate (target: < 1%)
- API uptime (target: 99.5%+)
- Offline functionality success rate (target: 100% for core features)

### 8.3 Impact Metrics
- Yield improvement per farmer (target: 10–25%)
- Fertilizer reduction (target: 20–25%)
- Water savings (target: 15–30%)
- Cost savings per farmer (target: 15–20%)
- Prevented yield loss (target: 30–40% of potential loss)

### 8.4 User Satisfaction Metrics
- Net Promoter Score (NPS)
- User satisfaction ratings (target: > 4/5)
- Feature satisfaction scores
- Support ticket volume and resolution time

### 8.5 Business Metrics
- Cost per farmer acquisition
- Customer lifetime value (LTV)
- Operational costs per active user
- Revenue per user (if monetization implemented)

---

## 9. Compliance & Standards

### 9.1 Data Privacy
- Compliance with Indian data protection regulations
- Farmer data ownership principles
- Transparent data usage policies
- Right to data access, correction, and deletion

### 9.2 Agricultural Standards
- Fertilizer recommendations aligned with Indian Council of Agricultural Research (ICAR) guidelines
- Pesticide recommendations compliant with Central Insecticides Board & Registration Committee (CIBRC)
- Organic farming certifications (if applicable)

### 9.3 Accessibility Standards
- Web Content Accessibility Guidelines (WCAG) 2.1 Level AA for web portal
- Android accessibility best practices for mobile app
- Voice interaction standards

### 9.4 Security Standards
- OWASP Mobile Security guidelines
- ISO 27001 principles for information security
- Regular security audits and penetration testing

---

## 10. Risk Assessment

### 10.1 Technical Risks

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| AI model accuracy insufficient | Medium | High | Extensive training data collection, expert validation, continuous model improvement |
| On-device inference too slow | Medium | High | Model optimization, quantization, use of lightweight architectures |
| Offline sync failures | Medium | Medium | Robust queue-based sync, conflict resolution, user feedback |
| Poor image quality from farmers | High | Medium | Image quality validation, user guidance, preprocessing algorithms |

### 10.2 User Adoption Risks

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Low farmer adoption | Medium | High | Voice-first design, NGO partnerships, field demonstrations, farmer training |
| Trust in AI recommendations | Medium | High | Confidence scores, expert validation, success stories, gradual trust building |
| Limited smartphone access | Medium | Medium | Community smartphone sharing, partnerships with extension workers |

### 10.3 Operational Risks

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Insufficient funding | Medium | High | Phased rollout, grant applications, CSR partnerships, freemium model |
| Lack of training data | Medium | High | Partnerships with research institutions, crowdsourcing, synthetic data generation |
| Expert unavailability | Low | Medium | Build expert network early, remote expert engagement |

### 10.4 External Risks

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Regulatory changes | Low | Medium | Legal consultation, compliance monitoring, flexible architecture |
| Competitor emergence | Medium | Medium | Rapid innovation, user lock-in through value, network effects |
| Poor internet infrastructure | High | Low | Offline-first design already addresses this |

---

## 11. Glossary

| Term | Definition |
|------|------------|
| **NPK** | Nitrogen, Phosphorus, Potassium - three primary macronutrients required by plants |
| **CNN** | Convolutional Neural Network - deep learning architecture for image analysis |
| **FPO** | Farmer Producer Organization - collective of farmers for better market access |
| **APMC** | Agricultural Produce Market Committee - regulated markets for agricultural produce |
| **e-NAM** | National Agriculture Market - online trading platform for agricultural commodities |
| **ICAR** | Indian Council of Agricultural Research - apex body for agriculture research |
| **STT** | Speech-to-Text - converting spoken language to written text |
| **TTS** | Text-to-Speech - converting written text to spoken language |
| **JWT** | JSON Web Token - standard for secure authentication |
| **OTA** | Over-The-Air - remote software updates without physical connection |
| **DAU/MAU** | Daily Active Users / Monthly Active Users - user engagement metrics |
| **LTV** | Lifetime Value - total revenue expected from a user over their lifetime |
| **NPS** | Net Promoter Score - customer satisfaction and loyalty metric |

---

## 12. Appendices

### Appendix A: User Story Mapping
(To be developed in detailed design phase)

### Appendix B: Wireframe References
See Slide 8 of original presentation for wireframe concepts:
- Login & Language Selection Screen
- Farmer Dashboard (Home Screen)
- Crop Diagnosis Screen
- Decision Support Screen
- Alerts & Notifications Screen
- Market & Services Screen
- Sustainability & Impact Screen
- Admin & Analytics Dashboard

### Appendix C: Estimated Costs
Detailed cost breakdown provided in Slide 11 of original presentation:
- **MVP Phase (0–3 months):** ₹1.45 – ₹2.30 Lakhs
- **Pilot Phase (3–6 months, 100–500 farmers):** ₹1.20 – ₹2.00 Lakhs
- **Annual Operating Cost (10,000+ farmers):** ₹4 – ₹6 Lakhs

---

**Document Version:** 1.0  
**Last Updated:** February 12, 2026  
**Next Review:** Upon completion of MVP or major milestone  
**Document Owner:** The Sensing Squad Team
