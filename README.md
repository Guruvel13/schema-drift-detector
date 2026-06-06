# Schema Drift Detector

An AI-powered full-stack web application that monitors database schema changes, detects drift, and uses an LLM (via OpenRouter) to analyze impact, classify risk, and generate mitigation recommendations.

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React + Vite + Tailwind CSS + Recharts |
| Backend | FastAPI + SQLAlchemy |
| AI Layer | LangChain + OpenRouter (GPT-3.5-turbo) |
| Databases Supported | PostgreSQL, SQLite |

## Features

- Connect to PostgreSQL or SQLite databases
- Take schema snapshots on demand
- Deterministic diff engine detects exact changes
- LLM agent classifies each change as **Breaking / Additive / Potentially Breaking**
- Assigns **Low / Medium / High** risk levels
- Explains downstream impact (ETL, APIs, analytics, ML pipelines)
- Generates mitigation recommendations
- Dashboard with risk distribution charts
- Full drift report history with AI Executive Summary

## Project Structure

```
Schema_Drift_Detector/
├── backend/
│   ├── app/
│   │   ├── agents/         # LLM drift analyzer
│   │   ├── api/            # FastAPI routes
│   │   ├── models/         # SQLAlchemy models
│   │   └── services/       # Schema extractor, diff engine, snapshot service
│   ├── .env.example
│   └── requirements.txt
├── frontend/
│   ├── src/
│   │   ├── components/     # Sidebar, Badges
│   │   └── pages/          # Dashboard, ConnectDB, Scan, Reports, Snapshots
│   └── .env
└── docker-compose.yml
```

## Setup

### 1. Clone the repo
```bash
git clone https://github.com/yourusername/schema-drift-detector.git
cd schema-drift-detector
```

### 2. Backend setup
```bash
cd backend
pip install -r requirements.txt
cp .env.example .env
# Edit .env and add your OpenRouter API key and DB credentials
uvicorn app.main:app --reload
```

### 3. Frontend setup
```bash
cd frontend
npm install
npm run dev
```

Open `http://localhost:5173`

### 4. Or run with Docker
```bash
docker-compose up --build
```

## Usage

1. Go to **Connect DB** → enter your PostgreSQL or SQLite connection details
2. Go to **Run Scan** → click **Run AI Scan** to take the first snapshot
3. Make schema changes in your database
4. Run scan again → LLM analyzes the drift
5. View full reports on **Drift Reports** page
6. Check **Dashboard** for risk distribution charts

## Environment Variables

| Variable | Description |
|---|---|
| `OPENROUTER_API_KEY` | Your OpenRouter API key |
| `OPENROUTER_BASE_URL` | `https://openrouter.ai/api/v1` |
| `LLM_MODEL` | e.g. `openai/gpt-3.5-turbo` |
| `DATABASE_URL` | PostgreSQL or SQLite connection string |
"# schema-drift-detector" 
