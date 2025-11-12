# 🚀 SILFP — Smart Intelligent Live Face Presence

[![Status](https://img.shields.io/badge/Status-Active-brightgreen)](#)
[![Build](https://img.shields.io/github/actions/workflow/status/<your-org>/silfp/ci.yml?label=Build&logo=github)](#)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)](#)
[![Frontend](https://img.shields.io/badge/Frontend-React%20%7C%20Tailwind-orange?logo=react)](#)
[![Backend](https://img.shields.io/badge/Backend-FastAPI-green?logo=fastapi)](#)

---

<p align="center">
  <img src="docs/assets/hero-banner.png" width="850" alt="SILFP System Overview" />
</p>

> **SILFP (Smart Intelligent Live Face Presence)** is a next-generation **AI-powered attendance management system** that uses real-time **face recognition**, **edge computing**, and **secure cloud synchronization** to automate student attendance seamlessly — built for universities, colleges, and smart campuses.

---

## 📘 Table of Contents
- [🎯 Overview](#-overview)
- [🧩 Key Features](#-key-features)
- [⚙️ System Architecture](#️-system-architecture)
- [🧠 Technology Stack](#-technology-stack)
- [🏗️ Project Structure](#️-project-structure)
- [🧰 Setup & Installation](#-setup--installation)
- [🧾 API Overview](#-api-overview)
- [🎥 Demo & Screenshots](#-demo--screenshots)
- [🔒 Security & Privacy](#-security--privacy)
- [🧪 Testing](#-testing)
- [🚀 Roadmap](#-roadmap)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)
- [👥 Team](#-team)
- [📞 Contact](#-contact)

---

## 🎯 Overview

SILFP transforms traditional attendance systems into **smart, contactless, and automated** solutions through advanced **face recognition** and **IoT integration**.

It is designed with **global-grade scalability and data security**, capable of managing **10,000+ students** across multiple classrooms.

### 💡 Vision
> “A seamless, zero-intervention attendance ecosystem where technology enhances classroom experience, not interrupts it.”

---

## 🧩 Key Features

| Category | Features |
|-----------|-----------|
| 🎓 **Students** | Real-time face-based attendance, dashboard view of history & attendance %, secure login |
| 👩‍🏫 **Faculty** | Class-wise attendance overview, reports, manual overrides (with audit logs) |
| 🛠️ **Admin** | Device management, analytics dashboard, model update monitoring |
| 🤖 **Hardware** | Edge device with camera + embedded AI (Raspberry Pi 5 / Jetson Nano / Coral) |
| 🔐 **Security** | End-to-end encryption, liveness detection, audit trails, role-based access |
| 📊 **Analytics** | Attendance trends, absentee heatmaps, device uptime metrics |

---

## ⚙️️ System Architecture

<p align="center">
  <img src="docs/assets/architecture.png" alt="System Architecture" width="800"/>
</p>

### **Flow Summary**
1. Student enters classroom → camera captures live face.
2. Edge device runs **local face recognition & liveness check**.
3. Match found → **attendance event** created.
4. Event securely synced to **Backend API → PostgreSQL**.
5. Dashboards update instantly for faculty & admin.

### **Core Modules**
- **Edge Module** — runs on Raspberry Pi / Jetson, local FR inference.
- **Backend API** — FastAPI service handling auth, attendance, analytics.
- **Frontend** — React + Tailwind web dashboard.
- **Database** — PostgreSQL + pgVector (for embeddings).
- **Monitoring** — Prometheus / Grafana stack.

---

## 🧠 Technology Stack

| Layer | Technology |
|--------|-------------|
| **Edge AI** | Python · OpenCV · FaceNet / InsightFace · TensorFlow Lite |
| **Backend** | FastAPI · PostgreSQL · Redis · SQLAlchemy |
| **Frontend** | React · Tailwind CSS · Axios · Chart.js |
| **Infra / DevOps** | Docker · GitHub Actions · Render / Vercel |
| **AI / MLOps** | MLflow · ONNX · PyTorch · OpenVINO (optional) |
| **Security** | OAuth2 JWT · TLS · Hashed Embeddings |

---

## 🏗️ Project Structure
```bash
silfp/
├─ README.md
├─ docs/
│ ├─ assets/
│ │ ├─ architecture.png
│ │ ├─ demo.gif
│ │ └─ hero-banner.png
│ ├─ api.md
│ ├─ architecture.md
│ └─ privacy.md
├─ backend/
│ ├─ app/
│ │ ├─ main.py
│ │ ├─ api/
│ │ ├─ models/
│ │ └─ db/
│ ├─ tests/
│ ├─ requirements.txt
│ └─ Dockerfile
├─ frontend/
│ ├─ src/
│ ├─ public/
│ ├─ package.json
│ └─ Dockerfile
├─ edge/
│ ├─ device_app/
│ ├─ models/
│ ├─ main.py
│ └─ requirements.txt
├─ infra/
│ ├─ docker-compose.yml
│ ├─ k8s/
│ └─ terraform/
└─ scripts/
├─ init_db.sql
└─ demo_seed.py

```
---

## 🧰 Setup & Installation

### 🔹 1. Clone Repository
```bash
git clone https://github.com/<your-org>/silfp.git
cd silfp
```


---

## 🚀 Quickstart (Local POC)

> Prereqs: Python 3.10+, Node.js 18+, Docker (optional)

### 1) Clone
```bash
git clone https://github.com/<your-org>/silfp.git
cd silfp
```
### 2) Backend (FastAPI)
```bash
cd backend
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
# Copy env.example -> .env and fill
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```
### 3) Frontend (React
```bash
cd frontend
npm install
npm run dev
# open http://localhost:3000
```
### 4) Edge (Local simulation)
```bash
cd edge
python main.py --simulate --server http://localhost:8000
```
🧾 API Overview

| Method | Endpoint                       | Description                  |
| :----: | :----------------------------- | :--------------------------- |
| `POST` | `/auth/login`                  | Login with username/password |
| `POST` | `/students`                    | Register student             |
| `POST` | `/students/{id}/register-face` | Upload image or embeddings   |
| `POST` | `/attendance`                  | Device logs attendance event |
|  `GET` | `/attendance?student_id=xx`    | Fetch attendance records     |
|  `GET` | `/reports/summary`             | Admin analytics              |
| `POST` | `/devices/register`            | Register new device          |


## 🎥 Demo & Screenshots

| Face Recognition          | Attendance Dashboard           |
| ------------------------- | ------------------------------ |
| ![](docs/assets/demo.gif) | ![](docs/assets/dashboard.png) |

> 💡 The demo showcases automatic recognition & instant attendance sync from device → cloud → dashboard.

---

## 🔒 Security & Privacy

SILFP prioritizes **data protection and ethical AI**:

* 🔐 **Encrypted channels** — TLS 1.3 & JWT for all API/device communications.
* 🙈 **Privacy-first** — Only embeddings & logs stored, no raw images by default.
* ⚙️ **Model integrity** — Signed model updates for edge devices.
* 🧾 **Audit logging** — Every attendance modification recorded with timestamps.
* 🧍‍♂️ **Opt-out options** — QR/NFC fallback for privacy-sensitive users.

See [`/docs/privacy.md`](docs/privacy.md) for details.

---

## 🧪 Testing

### Backend Unit Tests

```bash
cd backend
pytest -q
```

### Frontend

```bash
cd frontend
npm run test
```

### Load Simulation (Optional)

```bash
cd scripts
python load_test.py
```

---

## 🚀 Roadmap

| Phase      | Milestone                                    | Status                  |
| ---------- | -------------------------------------------- | ----------------------- |
| ✅ Phase 1  | Proof-of-Concept (1 class, 30 students)      | Completed / In Progress |
| 🔜 Phase 2 | Multi-Class Support + Cloud Dashboard        | Planned                 |
| 🔜 Phase 3 | Device OTA Updates + Edge Model Sync         | Planned                 |
| 🔜 Phase 4 | Analytics + AI Insights + Predictive Reports | Future                  |
| 🔜 Phase 5 | Pilot Deployment (10k students)              | Future                  |

---

## 🤝 Contributing

1. **Fork** this repository
2. **Create** your feature branch

   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Commit** changes

   ```bash
   git commit -m "Added new feature"
   ```
4. **Push** to branch and **open a PR**

---

## 📄 License

Licensed under the [MIT License](LICENSE)
© 2025 SILFP Team — All rights reserved.

---

## 👥 Team

| Role                               | Name        | Dept      |
| ---------------------------------- | ----------- | --------- |
| 🧭 Project Lead / System Architect | *Sashi Vardhan* | ECE   |
| 💻 Backend Developer               | *Adhitya*      | CSE       |
| 🌐 Frontend Developer              | *SaiTeja*      | CSE       |
| 🤖 ML & AI Engineer                | *Sunil*      | ECE       |
| 🔌 Hardware & IoT Integrator       | *Prem Kumar*      | ECE       |

---

## 📞 Contact

📧 **Email:** [sashi.vr007@gmail.com](mailto:sashi.vr007@gmail.com)

🌐 **Website:** [https://silfp.vercel.app](https://silfp.vercel.app)

🐙 **GitHub:** [(https://github.com/StriX-Lab007/SILFP/)](https://github.com/StriX-Lab007/SILFP/)

📍 **Institution:** Department of ECE & CSE, Malla Reddy (MR) Deemed to be University 
, India

---

<p align="center">
  <img src="docs/assets/footer-banner.gif" width="650" alt="Made with ❤️ by SILFP Team" />
</p>


