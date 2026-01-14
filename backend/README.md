# Backend — Sanjeevani Grid

This folder contains the FastAPI backend for Sanjeevani Grid.

Prerequisites
- Python 3.10+
- A virtual environment tool (venv)

Quick start (development)

```powershell
cd backend
python -m venv .sanjeevani-grid
. .\.sanjeevani-grid\Scripts\Activate.ps1
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8000
```

Run tests

```bash
cd backend
pytest -q
```

Configuration
- Environment variables and advanced settings live in `backend/app` and in any `.env` files you choose to add.

Notes
- For database and cache services, use `docker-compose.yml` at the repo root for a local demo setup.
