<div align="center">

# 🎓 Autonomous AI Research University

**AI professors. AI students. Zero humans. One autonomous university.**

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com)
[![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![SQLite](https://img.shields.io/badge/SQLite-07405E?style=for-the-badge&logo=sqlite&logoColor=white)](https://sqlite.org)
[![Gemini API](https://img.shields.io/badge/Google%20Gemini-8E75B2?style=for-the-badge&logo=google&logoColor=white)](https://deepmind.google/technologies/gemini/)

> A fully autonomous multi-agent simulation where AI professors teach AI students, assign and evaluate projects, generate research papers, and design new curricula — all powered by Google Gemini, FastAPI, and React.

</div>

---

## 📖 About The Project

**Autonomous AI Research University** is a full-stack, multi-agent AI simulation that models a self-operating academic institution. In this system, every actor — professor, student, and evaluator — is an autonomous AI agent powered by Google Gemini. 

Once a "Cycle" is triggered from the UI, the agents collaborate end-to-end without any human intervention:
1. **AI Professors** design and assign academic projects in their domain of expertise.
2. **AI Students** autonomously interpret assignments, research topics, and submit structured project deliverables.
3. **AI Evaluators** (professors acting as graders) assess student submissions, assign grades, and provide detailed feedback.
4. **The System** synthesizes learning outcomes into publishable-format research papers.
5. **The System** then autonomously designs new courses and curricula based on emerging gaps in the academic program.

The entire pipeline is **fully autonomous** — a single "Run Cycle" button in the dashboard triggers the whole academic workflow, and users can observe each step live via an interactive activity timeline.

---

## ✨ Key Features

- **🧑‍🏫 AI Professors Module:** Domain-specific AI personas (e.g., Computer Science, Physics) that generate assignments and evaluate work.
- **🧑‍🎓 AI Students Module:** Students with different skill levels and learning profiles that autonomously complete projects.
- **📝 Autonomous Project Workflow:** End-to-end project assignment, submission, and evaluation.
- **📄 Research Paper Generation:** AI synthesizes the semester's work into structured academic papers (Abstract, Methodology, Conclusion).
- **📚 Curriculum Design:** AI continuously suggests new courses based on student performance and emerging trends.
- **⚡ One-Click "Run Cycle":** A glowing dashboard button that triggers the entire multi-agent orchestration.
- **🎨 Modern UI/UX:** Dark-mode, glassmorphism design with live activity feeds and charts.

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
| :--- | :--- | :--- |
| **Frontend** | React 18, Vite, TailwindCSS | Fast, modern, responsive UI |
| **Backend** | Python 3.10+, FastAPI | High-performance async REST API |
| **Database** | SQLite, SQLAlchemy | Zero-config, lightweight relational storage |
| **AI Engine** | Google Gemini API (`gemini-1.5-flash`) | LLM powering the autonomous agents |
| **Styling** | TailwindCSS, Framer Motion | Beautiful animations and layouts |
| **Charts** | Recharts | Dashboard analytics |

---

## 🏗️ Architecture & Data Flow

```text
[ User clicks "Run Cycle" on React UI ]
                  │
                  ▼
      [ POST /api/cycles/run ]
                  │
                  ▼
      [ FastAPI CycleOrchestrator ]
                  │
        ┌─────────┴─────────┐
        ▼                   ▼
 [ ProfessorAgent ]   [ StudentAgent ]
        │                   │
        └─────────┬─────────┘
                  ▼
         [ EvaluatorAgent ]
                  │
                  ▼
      [ PaperService & CurriculumService ]
                  │
                  ▼
          [ SQLite Database ]
                  │
                  ▼
        [ UI Updates via Axios ]


        autonomous-ai-university/
├── backend/               # FastAPI Application
│   ├── app/
│   │   ├── agents/        # AI Agent logic (Professor, Student)
│   │   ├── prompts/       # Structured LLM Prompts
│   │   ├── routes/        # API Endpoints
│   │   ├── services/      # Business logic & Orchestrator
│   │   ├── database.py    # DB Connection
│   │   └── models.py      # SQLAlchemy Models
│   └── requirements.txt
├── frontend/              # React + Vite Application
│   ├── src/
│   │   ├── components/    # Reusable UI Components
│   │   ├── pages/         # Dashboard, Papers, Cycles etc.
│   │   └── api/           # Axios API calls
│   └── package.json
├── database/              # SQLite DB & Schemas
├── docs/                  # Documentation & Demo Scripts
└── README.md


cd backend
python -m venv venv

# Windows
venv\Scripts\activate
# Mac/Linux
source venv/bin/activate

pip install -r requirements.txt

# Create .env file and add your API key
echo "GEMINI_API_KEY=your_api_key_here" > .env

# Run the server
uvicorn app.main:app --reload


cd frontend
npm install
npm run dev