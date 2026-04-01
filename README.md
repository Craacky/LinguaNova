# 🌟 LinguaNova

<div align="center">

**Modern English Learning Platform**

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.109+-green.svg)](https://fastapi.tiangolo.com/)
[![Next.js](https://img.shields.io/badge/Next.js-14+-black.svg)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-blue.svg)](https://www.typescriptlang.org/)

[Features](#-features) • [Tech Stack](#-tech-stack) • [Getting Started](#-getting-started) • [Documentation](#-documentation) • [License](#-license)

</div>

---

## 📖 About

**LinguaNova** is a comprehensive web platform designed to help learners master English from beginner (A1) to advanced (C2) levels. Built with modern technologies and AI integration, it provides a complete learning cycle: theory, practice, testing, listening comprehension, and vocabulary building.

### 🎯 Key Objectives

- **Progressive Learning:** Structured path from A1 to C2 (CEFR levels)
- **AI-Powered:** Personalized explanations, recommendations, and content moderation
- **Complete Cycle:** Theory → Exercises → Tests → Real-world application
- **Spaced Repetition:** FSRS algorithm for vocabulary retention
- **Gamification:** Streaks, achievements, leaderboards, and progress tracking

---

## ✨ Features

### 🎓 Learning System

- **Structured Curriculum:** Organized by levels (A1-C2), modules (Grammar, Vocabulary, Listening, Writing), and topics
- **Interactive Exercises:** Multiple choice, fill-in-the-blanks, matching, ordering, writing with AI feedback
- **Comprehensive Tests:** Level assessment tests with question pools and unlimited retakes
- **Progress Tracking:** Linear progression with adaptive recommendations

### 📚 Vocabulary System

- **Spaced Repetition:** FSRS algorithm (modern Anki alternative)
- **Flashcards:** Word → Translation → Usage examples
- **Smart Scheduling:** Optimal review intervals based on performance
- **Progress Metrics:** Track learned words and retention rates

### 🎧 Listening Comprehension

- **Interactive Audio Player:** Variable playback speed (0.75x - 1.25x)
- **Interactive Transcripts:** Click words for instant translation
- **Comprehension Questions:** Test understanding after listening
- **Level-Appropriate Content:** AI-recommended materials

### 🎮 Gamification

- **Streak System:** Daily learning streaks
- **XP & Points:** Earn rewards for completing exercises
- **Achievements:** Unlock badges for milestones
- **Leaderboard:** Global ranking system
- **Progress Visualization:** Heatmaps, charts, and statistics

### 👥 Social Features

- **Comments:** Discuss topics with other learners
- **Study Buddy:** Find language partners at your level
- **Public Profiles:** Share progress and achievements
- **Progress Sharing:** Celebrate milestones with the community

### 📊 Personal Dashboard

- **Detailed Analytics:** Progress by level, time spent, strengths/weaknesses
- **Activity Heatmap:** GitHub-style learning calendar
- **Skill Radar Chart:** Visualize grammar, vocabulary, listening, writing skills
- **Smart Recommendations:** AI-powered suggestions for improvement
- **Level Forecast:** Predict when you'll reach the next level

### 🤖 AI Integration

- **Error Explanations:** Detailed AI-generated feedback on mistakes
- **Content Recommendations:** Personalized listening materials
- **Comment Moderation:** Automatic filtering with blacklist
- **Future:** AI-generated exercises and personalized learning paths

---

## 🛠️ Tech Stack

### Backend

- **Framework:** [FastAPI](https://fastapi.tiangolo.com/) - Modern, fast Python web framework
- **Database:** [PostgreSQL](https://www.postgresql.org/) - Robust relational database
- **ORM:** [SQLAlchemy](https://www.sqlalchemy.org/) - Python SQL toolkit
- **Migrations:** [Alembic](https://alembic.sqlalchemy.org/) - Database migration tool
- **Validation:** [Pydantic](https://docs.pydantic.dev/) - Data validation
- **Authentication:** JWT + OAuth (Google)
- **Background Tasks:** [Celery](https://docs.celeryq.dev/) + Redis
- **Web Scraping:** httpx + BeautifulSoup4/Scrapy
- **AI:** [OpenRouter](https://openrouter.ai/) - Free AI models

### Frontend

- **Framework:** [Next.js 14](https://nextjs.org/) - React framework with App Router & SSR
- **Language:** [TypeScript](https://www.typescriptlang.org/) - Type-safe JavaScript
- **Styling:** [Tailwind CSS](https://tailwindcss.com/) + [shadcn/ui](https://ui.shadcn.com/)
- **State Management:** [Zustand](https://zustand-demo.pmnd.rs/) - Lightweight state management
- **Data Fetching:** [TanStack Query](https://tanstack.com/query/latest) - Powerful async state management
- **Forms:** React Hook Form + Zod validation
- **Charts:** [Recharts](https://recharts.org/) - Composable charting library
- **Audio:** [Howler.js](https://howlerjs.com/) - Audio library

### Infrastructure

- **Containerization:** Docker + Docker Compose
- **CI/CD:** GitHub Actions
- **Hosting:** VPS (Self-hosted)
- **Reverse Proxy:** Nginx + Let's Encrypt (SSL)
- **Storage:** Cloudflare R2 (S3-compatible)
- **CDN:** Cloudflare CDN
- **Cache:** Redis
- **Monitoring:** Sentry + UptimeRobot

---

## 🚀 Getting Started

### Prerequisites

- Docker & Docker Compose
- Node.js 18+ (for local frontend development)
- Python 3.11+ (for local backend development)

### Quick Start with Docker

```bash
# Clone the repository
git clone https://github.com/yourusername/linguanova.git
cd linguanova

# Copy environment variables
cp .env.example .env

# Edit .env with your configuration
nano .env

# Start all services
docker-compose up -d

# Run database migrations
docker-compose exec backend alembic upgrade head

# Create admin user
docker-compose exec backend python scripts/create_admin.py
```

The application will be available at:
- **Frontend:** http://localhost:3000
- **Backend API:** http://localhost:8000
- **API Docs:** http://localhost:8000/docs

### Local Development

#### Backend

```bash
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run migrations
alembic upgrade head

# Start development server
uvicorn app.main:app --reload
```

#### Frontend

```bash
cd frontend

# Install dependencies
npm install

# Start development server
npm run dev
```

---

## 📁 Project Structure

```
linguanova/
├── backend/                 # FastAPI backend
│   ├── app/
│   │   ├── api/            # API endpoints
│   │   ├── core/           # Core configuration
│   │   ├── models/         # SQLAlchemy models
│   │   ├── schemas/        # Pydantic schemas
│   │   ├── services/       # Business logic
│   │   └── utils/          # Utility functions
│   ├── alembic/            # Database migrations
│   ├── tests/              # Backend tests
│   └── requirements.txt
├── frontend/               # Next.js frontend
│   ├── app/               # App Router pages
│   ├── components/        # React components
│   ├── lib/              # Utilities & helpers
│   ├── store/            # Zustand stores
│   └── types/            # TypeScript types
├── docker-compose.yml     # Docker services
├── nginx/                 # Nginx configuration
└── docs/                  # Documentation
```

---

## 📚 Documentation

- [API Documentation](http://localhost:8000/docs) - Interactive API docs (Swagger UI)
- [Database Schema](./docs/database-schema.md) - Database structure and relationships
- [Deployment Guide](./docs/deployment.md) - Production deployment instructions
- [Contributing Guide](./CONTRIBUTING.md) - How to contribute to the project

---

## 🗺️ Roadmap

### Current Phase: MVP Development

- [x] Project specification
- [x] Technology stack selection
- [ ] Backend API & Database
- [ ] Frontend basic structure
- [ ] Authentication system
- [ ] Content management & scraping
- [ ] Learning system (theory + exercises)
- [ ] Vocabulary & spaced repetition
- [ ] Listening comprehension
- [ ] Level tests
- [ ] Social features
- [ ] Dashboard & analytics
- [ ] AI integration
- [ ] Deployment & CI/CD

### Post-MVP Features

- Speech practice with AI (speech-to-text + text-to-speech)
- Mobile application (React Native)
- External dictionary integration (Cambridge, Oxford)
- Podcasts and video materials
- Live group sessions
- Certificates for level completion
- Teacher marketplace
- Advanced gamification (badges, quests, tournaments)
- AI-generated personalized exercises
- Anki integration (card export)

---

## 🤝 Contributing

We welcome contributions! However, please note that this project is licensed under AGPL v3, which means:

- Any modifications must be open-sourced
- Commercial use requires compliance with AGPL terms
- Network use requires source code disclosure

Please read [CONTRIBUTING.md](./CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

---

## 📄 License

This project is licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0)**.

**What this means:**
- ✅ You can use, study, and modify the code
- ✅ You can distribute modified versions
- ❌ You cannot use it commercially without open-sourcing your changes
- ❌ If you run a modified version on a server, you must provide the source code to users

See the [LICENSE](./LICENSE) file for full details.

**Why AGPL?** This license ensures that improvements to LinguaNova remain open and accessible to the community, preventing proprietary forks while still allowing learning and non-commercial use.

---

## 🙏 Acknowledgments

- Content sources: BBC Learning English, British Council, Cambridge English, Oxford
- Inspired by modern language learning platforms
- Built with amazing open-source technologies

---

## 📞 Contact & Support

- **Issues:** [GitHub Issues](https://github.com/yourusername/linguanova/issues)
- **Discussions:** [GitHub Discussions](https://github.com/yourusername/linguanova/discussions)
- **Email:** support@linguanova.com (coming soon)
- **Discord:** [Join our community](https://discord.gg/linguanova) (coming soon)

---

<div align="center">

**Made with ❤️ for language learners worldwide**

⭐ Star us on GitHub if you find this project useful!

</div>
