# Project Structure

This document outlines the recommended project structure for the SDR Enhancement System.

```
sdr-enhancement-system/
├── README.md
├── IMPLEMENTATION_PLAN.md
├── LICENSE
├── .gitignore
├── .env.example
├── docker-compose.yml
├── package.json
├── requirements.txt
│
├── docs/                           # Documentation
│   ├── api.md                     # API documentation
│   ├── architecture.md            # System architecture
│   ├── deployment.md              # Deployment guide
│   └── user-guide.md              # User guide
│
├── backend/                        # Backend services
│   ├── api/                       # REST API
│   │   ├── __init__.py
│   │   ├── main.py                # FastAPI application
│   │   ├── routes/                # API routes
│   │   │   ├── __init__.py
│   │   │   ├── auth.py
│   │   │   ├── leads.py
│   │   │   ├── scoring.py
│   │   │   ├── battlecards.py
│   │   │   └── transcripts.py
│   │   ├── models/                # Data models
│   │   │   ├── __init__.py
│   │   │   ├── user.py
│   │   │   ├── lead.py
│   │   │   ├── score.py
│   │   │   └── transcript.py
│   │   ├── services/              # Business logic
│   │   │   ├── __init__.py
│   │   │   ├── auth_service.py
│   │   │   ├── scoring_service.py
│   │   │   ├── llm_service.py
│   │   │   └── battlecard_service.py
│   │   └── utils/                 # Utilities
│   │       ├── __init__.py
│   │       ├── database.py
│   │       ├── security.py
│   │       └── validators.py
│   │
│   ├── agents/                    # AI Agents
│   │   ├── __init__.py
│   │   ├── scoring_agent.py       # EV, Risk, Urgency scoring
│   │   ├── routing_agent.py       # SDR assignment
│   │   ├── research_agent.py      # Company research
│   │   └── assistant_agent.py     # Real-time assistance
│   │
│   ├── ml/                        # Machine Learning
│   │   ├── __init__.py
│   │   ├── models/                # ML models
│   │   │   ├── __init__.py
│   │   │   ├── scoring_model.py
│   │   │   ├── risk_model.py
│   │   │   └── urgency_model.py
│   │   ├── training/              # Training scripts
│   │   │   ├── __init__.py
│   │   │   ├── train_scoring.py
│   │   │   └── train_risk.py
│   │   └── inference/             # Inference engines
│   │       ├── __init__.py
│   │       └── predictor.py
│   │
│   ├── processors/                # Data processors
│   │   ├── __init__.py
│   │   ├── speech_processor.py    # Speech-to-text
│   │   ├── transcript_processor.py # Live transcript analysis
│   │   ├── data_processor.py      # Data ETL
│   │   └── realtime_processor.py  # Real-time data processing
│   │
│   ├── integrations/              # External integrations
│   │   ├── __init__.py
│   │   ├── crm/                   # CRM integrations
│   │   │   ├── __init__.py
│   │   │   ├── salesforce.py
│   │   │   └── hubspot.py
│   │   ├── communications/        # Communication platforms
│   │   │   ├── __init__.py
│   │   │   ├── zoom.py
│   │   │   └── teams.py
│   │   ├── external_apis/         # External APIs
│   │   │   ├── __init__.py
│   │   │   ├── companies_house.py
│   │   │   ├── openai_client.py
│   │   │   └── speech_api.py
│   │   └── databases/             # Database connections
│   │       ├── __init__.py
│   │       ├── postgresql.py
│   │       └── redis.py
│   │
│   └── config/                    # Configuration
│       ├── __init__.py
│       ├── settings.py
│       ├── database.py
│       └── logging.py
│
├── frontend/                      # Frontend application
│   ├── package.json
│   ├── tsconfig.json
│   ├── public/
│   │   ├── index.html
│   │   └── favicon.ico
│   ├── src/
│   │   ├── components/            # React components
│   │   │   ├── common/            # Common components
│   │   │   │   ├── Header.tsx
│   │   │   │   ├── Sidebar.tsx
│   │   │   │   └── Loading.tsx
│   │   │   ├── dashboard/         # Dashboard components
│   │   │   │   ├── Dashboard.tsx
│   │   │   │   ├── LiveCall.tsx
│   │   │   │   ├── Transcript.tsx
│   │   │   │   └── Battlecard.tsx
│   │   │   ├── leads/             # Lead management
│   │   │   │   ├── LeadList.tsx
│   │   │   │   ├── LeadCard.tsx
│   │   │   │   └── LeadDetails.tsx
│   │   │   └── admin/             # Admin components
│   │   │       ├── UserManagement.tsx
│   │   │       ├── SystemConfig.tsx
│   │   │       └── Analytics.tsx
│   │   ├── pages/                 # Page components
│   │   │   ├── LoginPage.tsx
│   │   │   ├── DashboardPage.tsx
│   │   │   ├── LeadsPage.tsx
│   │   │   └── AdminPage.tsx
│   │   ├── services/              # API services
│   │   │   ├── api.ts
│   │   │   ├── auth.ts
│   │   │   ├── leads.ts
│   │   │   ├── scoring.ts
│   │   │   └── websocket.ts
│   │   ├── hooks/                 # Custom hooks
│   │   │   ├── useAuth.ts
│   │   │   ├── useWebSocket.ts
│   │   │   └── useRealTime.ts
│   │   ├── store/                 # State management
│   │   │   ├── index.ts
│   │   │   ├── authSlice.ts
│   │   │   ├── leadsSlice.ts
│   │   │   └── callSlice.ts
│   │   ├── utils/                 # Utilities
│   │   │   ├── constants.ts
│   │   │   ├── helpers.ts
│   │   │   └── formatters.ts
│   │   └── styles/                # Styling
│   │       ├── globals.css
│   │       ├── components.css
│   │       └── themes.ts
│   └── build/                     # Build output
│
├── mobile/                        # Mobile application
│   ├── package.json
│   ├── App.tsx
│   ├── src/
│   │   ├── components/            # Mobile components
│   │   ├── screens/               # Mobile screens
│   │   ├── navigation/            # Navigation
│   │   ├── services/              # API services
│   │   └── utils/                 # Utilities
│   └── assets/                    # Mobile assets
│
├── infrastructure/                # Infrastructure as Code
│   ├── terraform/                 # Terraform configurations
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   ├── outputs.tf
│   │   ├── modules/
│   │   │   ├── vpc/
│   │   │   ├── rds/
│   │   │   ├── eks/
│   │   │   └── redis/
│   │   └── environments/
│   │       ├── dev/
│   │       ├── staging/
│   │       └── production/
│   ├── kubernetes/                # Kubernetes manifests
│   │   ├── namespaces/
│   │   ├── deployments/
│   │   ├── services/
│   │   ├── configmaps/
│   │   └── secrets/
│   └── helm/                      # Helm charts
│       ├── Chart.yaml
│       ├── values.yaml
│       └── templates/
│
├── scripts/                       # Utility scripts
│   ├── setup.sh                  # Environment setup
│   ├── deploy.sh                 # Deployment script
│   ├── migrate.py                # Database migration
│   ├── seed_data.py              # Seed data script
│   └── backup.sh                 # Backup script
│
├── tests/                         # Test suites
│   ├── unit/                     # Unit tests
│   │   ├── test_api/
│   │   ├── test_agents/
│   │   ├── test_ml/
│   │   └── test_services/
│   ├── integration/              # Integration tests
│   │   ├── test_api_integration.py
│   │   ├── test_agent_integration.py
│   │   └── test_data_pipeline.py
│   ├── e2e/                      # End-to-end tests
│   │   ├── test_user_journey.py
│   │   └── test_call_flow.py
│   ├── performance/              # Performance tests
│   │   ├── load_tests.py
│   │   └── stress_tests.py
│   └── fixtures/                 # Test data
│       ├── sample_transcripts.json
│       ├── sample_leads.json
│       └── sample_scores.json
│
├── data/                          # Data files
│   ├── raw/                      # Raw data
│   ├── processed/                # Processed data
│   ├── models/                   # Trained models
│   └── exports/                  # Data exports
│
├── monitoring/                    # Monitoring and observability
│   ├── prometheus/               # Prometheus configs
│   ├── grafana/                  # Grafana dashboards
│   ├── alerting/                 # Alert configurations
│   └── logs/                     # Log configurations
│
└── .github/                      # GitHub workflows
    ├── workflows/
    │   ├── ci.yml                # Continuous Integration
    │   ├── cd.yml                # Continuous Deployment
    │   ├── security.yml          # Security scanning
    │   └── tests.yml             # Test automation
    ├── ISSUE_TEMPLATE/
    ├── PULL_REQUEST_TEMPLATE.md
    └── dependabot.yml
```

## Key Directories Explained

### `/backend`
Contains all server-side code including APIs, AI agents, ML models, and data processors.

### `/frontend`
React-based web application for SDR dashboard and admin interface.

### `/mobile`
React Native or Flutter application for mobile SDR access.

### `/infrastructure`
Infrastructure as Code (IaC) using Terraform, Kubernetes manifests, and Helm charts.

### `/agents`
AI agents that handle different aspects of the system:
- **Scoring Agent**: Calculates EV, Risk, and Urgency scores
- **Routing Agent**: Determines optimal SDR assignment
- **Research Agent**: Automates company research
- **Assistant Agent**: Provides real-time call assistance

### `/integrations`
Handles all external system integrations including CRMs, communication platforms, and third-party APIs.

### `/ml`
Machine learning components including model training, inference engines, and ML utilities.

### `/processors`
Data processing components for real-time and batch data processing.

## Development Workflow

1. **Feature Development**: Create feature branches from `main`
2. **Testing**: All code must have unit tests and integration tests
3. **Code Review**: Pull requests require at least two reviewers
4. **CI/CD**: Automated testing and deployment through GitHub Actions
5. **Documentation**: Update relevant documentation with each change

## Environment Structure

- **Development**: Local development environment
- **Staging**: Pre-production testing environment
- **Production**: Live production environment

Each environment has its own configuration and infrastructure setup.
