# Sanjeevani Grid

Emergency medical resource availability & routing intelligence — non-diagnostic coordination for faster response.

Summary: Sanjeevani Grid helps first-responders and hospitals find and route to available critical resources (ICU beds, ventilators, blood units, ambulances) in real time. It focuses on logistics and coordination — not medical diagnosis or treatment.

---

## Table of Contents

- [Why this project](#why-this-project)
- [Features](#features)
- [Repository layout](#repository-layout)
- [Quick start (development)](#quick-start-development)
- [Docker / Compose](#docker--compose)
- [Running services (overview)](#running-services-overview)
- [Testing](#testing)
- [Contributing](#contributing)
- [License & contact](#license--contact)

---

## Why this project

- Emergency outcomes often hinge on reaching available resources quickly. Sanjeevani Grid reduces delays by connecting facilities, ambulances, and dispatchers with verified availability and ETA-based routing.
- Designed for demos, hackathons, and pilot programs; built responsibly with privacy and misuse-prevention in mind.

---

## Features

- Real-time resource availability (hospitals, blood banks, ambulances)
- Emergency search by resource type (ICU, ventilator, blood group, equipment)
- ETA-aware routing and ranking
- WebSocket-based live updates for dispatch UIs
- Role-based access and audit logging
- Optional ML modules: forecasting, anomaly detection, shortage alerts

---

## Repository layout

- `backend/` — API, services, models, tests
- `frontend/` — React app and UI components
- `ml-pipeline/` — training, inference, model artifacts
- `data-pipeline/` — Airflow DAGs and ETL plugins
- `infrastructure/` — docker-compose, Kubernetes manifests, Terraform
- `monitoring/` — ELK/Grafana/Prometheus configs

Refer to these folders for implementation details and deployment manifests.

---

## Quick start (development)

Prerequisites: Python 3.10+, Node.js 18+, Docker (optional).

1. Backend (venv + dependencies)

```powershell
# from repo root
cd backend
python -m venv .sanjeevani-grid
. .\.sanjeevani-grid\Scripts\Activate.ps1
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8000
```

2. Frontend

```bash
cd frontend
npm install
npm run dev
# or: npm start
```

3. Open the frontend (usually `http://localhost:3000` or as printed by the dev server)

Notes: Backend defaults and ports are configured in `backend/app` and environment variables. See `backend/README.md` (if present) for advanced settings.

---

## Docker / Compose

Start the system using Docker Compose (simple local demo):

```powershell
docker-compose up --build
```

This brings up backend, frontend, and required services (Postgres, Redis) as defined in `docker-compose.yml`.

---

## Running services (overview)

- Backend: FastAPI (REST + WebSocket) with Postgres (PostGIS) and Redis for caching/pubsub.
- Frontend: React app that subscribes to live updates via WebSocket.
- ML: Optional training and inference pipelines under `ml-pipeline/`.

If you plan to run only a specific service, consult the corresponding folder for environment variables and run instructions.

---

## Testing

Backend tests are under `backend/tests`. Run them using `pytest` from `backend/`:

```bash
cd backend
pytest -q
```

Frontend tests (if present) can be run with `npm test` under `frontend/`.

---

## Contributing

- Open an issue for discussion before major changes.
- Fork the repo, create a feature branch, and submit a pull request.
- Keep changes scoped and include tests for backend logic where applicable.

Security & ethics: the project intentionally avoids storing patient-identifiable data. Any extension that handles sensitive data must include a data protection design and approval.

---

## License & contact

This repository is provided under the MIT License (for demo, research, and educational use). See `LICENSE` for details.

For questions or collaboration, open an issue or contact the maintainers via the repository.

---


