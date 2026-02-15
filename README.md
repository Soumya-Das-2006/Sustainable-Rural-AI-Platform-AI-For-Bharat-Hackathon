# Sustainable Rural AI Platform (Camera-to-Decision)

Hackathon project by The Sensing Squad to deliver instant, offline-first crop diagnosis and actionable recommendations to rural farmers using smartphone cameras and on-device AI.

## Problem
- Delayed crop diagnosis (7-15 days) causes yield loss and input waste.
- Limited expert access, low literacy, and poor connectivity block timely decisions.
- Soil testing is costly and slow for small and marginal farmers.

## Solution
A mobile AI system that analyzes leaf images in under 5 seconds to detect nutrient deficiencies, disease, and pests, then delivers clear fertilizer and irrigation guidance. It works offline and syncs when online.

## Key Features
- On-device AI diagnosis for NPK deficiencies, disease, and pests.
- Precision fertilizer and irrigation recommendations.
- Voice-first, multilingual interface for low-literacy users.
- Offline-first data capture with automatic sync.
- Market access, equipment rental, and sustainability tracking (roadmap).

## Architecture (High Level)
- Mobile edge layer: React Native app with TensorFlow Lite inference and SQLite.
- Cloud backend: API services, data storage, model updates, analytics.
- Integrations: weather, market prices, government schemes.

See the full design in [design.md](design.md).

## Tech Stack (Planned)
- Mobile: React Native, TensorFlow Lite, SQLite
- Backend: Python (Django + FastAPI)
- Cloud: AWS (API Gateway, EC2/Lambda, S3, SageMaker, CloudWatch)
- Data: MongoDB
- Integrations: Weather APIs, Agmarknet, government scheme APIs

## Repository Structure
- [design.md](design.md): System architecture and data design
- [requirements.md](requirements.md): Functional requirements and user stories
- [Diagram/](Diagram/): Diagrams and visuals
- Hackathon_Documentation_Complete.docx: Consolidated documentation

## How It Works (User Flow)
1. Farmer captures leaf image in the app.
2. On-device AI analyzes the image and returns a diagnosis with confidence.
3. The app generates fertilizer and irrigation recommendations.
4. Data syncs to the cloud when connectivity is available.

## Impact Targets
- 10-25% yield improvement
- 20-25% reduction in fertilizer misuse
- 15-30% water savings
- Faster intervention to prevent 30-40% potential yield loss

## Roadmap
- Pilot with 100-500 farmers
- Expand to 10,000+ farmers with multi-crop and multi-region models
- Integrate marketplace, equipment rental, and sustainability dashboards

## Team
- Team Lead: Soumya Das
- Team: The Sensing Squad

## License
Not specified yet.

## References
- Requirements and user stories: [requirements.md](requirements.md)
- System design: [design.md](design.md)
