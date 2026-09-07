# 5G Sentinel — Capstone 2 SIEM

**5G Sentinel** is a Capstone 2 cybersecurity project that extends 5G intrusion detection into an explainable, SIEM-style security monitoring and assurance platform. It combines traffic ingestion, ML-assisted threat detection, telemetry replay, 5G network-function context, risk analysis, explainability, evidence generation, and human-gated response recommendations in a single web dashboard.

> **Project focus:** 5G security monitoring, attack analysis, explainable detection, research validation, and safe response assurance.

## Key Capabilities

- **5G traffic ingestion:** Upload CSV-based network traffic for analysis through the web interface.
- **Threat detection:** Classifies and scores suspicious traffic using schema-aware machine-learning pipelines.
- **SIEM-style dashboard:** Presents alerts, attack distributions, risk levels, security scores, and operational evidence.
- **5G network context:** Maps security findings to relevant 5G network functions such as gNB, AMF, SMF, AUSF, and UPF.
- **Telemetry replay:** Replays captured events to demonstrate detection and investigation workflows without requiring live 5G hardware.
- **Explainability:** Provides feature-level reasoning and evidence for security findings instead of showing only a prediction score.
- **Trust and assurance:** Adds trust context, model-health checks, drift evidence, and assurance gates before recommending a response.
- **Human-approved response:** Response actions are simulation-only / approval-gated; the platform does not perform uncontrolled autonomous network blocking.
- **Research validation:** Includes file/capture holdout evaluation, calibration evidence, drift baselines, model hashes, and open-world/unknown-traffic analysis.
- **Docker deployment:** Frontend and backend services can be launched using Docker Compose.

## Capstone 2 Contribution

Capstone 2 moves beyond the question **“Does this traffic look malicious?”** and asks a more operational question:

**“Does the platform have enough trustworthy and explainable evidence to recommend a security response?”**

The project introduces an **Assurance-Gated Adaptive Response (AGAR)** concept. A high model score alone is not treated as permission to act. Response recommendations consider detection confidence, explanation fidelity, 5G network-function mapping, safe-twin residual risk, and model-health evidence. If required evidence is missing, the platform fails closed and requests human approval.

## System Architecture

The solution consists of:

1. **React/Vite Frontend** — operator dashboard, dataset upload, results, explainability, replay, and research views.
2. **Python Backend/API** — ingestion, case management, scoring, analytics, replay, assurance logic, and research endpoints.
3. **Machine-Learning Layer** — schema-aware feature processing, model selection, prediction, calibration, and validation.
4. **Evidence & Assurance Layer** — model-health evidence, drift checks, trust context, explainability, and response assurance certificates.
5. **Docker Deployment** — containerized frontend and backend for repeatable demonstrations.

## Technology Stack

| Layer | Technologies |
|---|---|
| Frontend | React, TypeScript, Vite, CSS, Nginx |
| Backend | Python, FastAPI-compatible API structure, ML/data-processing libraries |
| Machine Learning | Scikit-learn based training/evaluation workflows |
| Data | CSV 5G/network-traffic datasets |
| Deployment | Docker, Docker Compose |
| Security Analysis | SIEM-style alerting, risk scoring, explainability, telemetry replay, assurance gating |

## Project Structure

```text
5G-Sentinel-Capstone2/
├── backend/
│   ├── app/                    # Main API and case-management logic
│   ├── model_artifacts/        # Model/evaluation metadata
│   ├── training_data/          # Training datasets
│   ├── evaluate_open_world.py  # Open-world evaluation
│   ├── evaluate_phase2.py      # Phase-2 validation
│   ├── train_5gid.py           # 5GID model training
│   └── train_cap1_flow.py      # Capstone-1 flow training
├── frontend/
│   ├── src/                    # React/TypeScript dashboard
│   └── public/datasets/        # Demo/reference datasets
├── scripts/                    # Demo/support scripts
├── capstone2/                  # Capstone-2 technical documentation
├── docker-compose.yml
├── CAPSTONE2_*.md              # Architecture, evaluation, research & innovation notes
└── README.md
```

## Running the Project

### Prerequisites

- Docker
- Docker Compose

### Start the application

```bash
docker compose up --build -d
```

The project configuration exposes the UI and API through the ports defined in `docker-compose.yml` (the current Capstone 2 configuration uses UI port **8612** and API port **8012**).

### Stop the application

```bash
docker compose down
```

## Typical Demonstration Workflow

1. Start the frontend and backend using Docker Compose.
2. Open the 5G Sentinel dashboard.
3. Upload a supported CSV network-traffic dataset.
4. Review schema/model-selection information.
5. Run threat analysis and inspect predicted malicious traffic.
6. Review attack distribution, risk level, and security score.
7. Open explainability and evidence views.
8. Replay telemetry/events for investigation.
9. Review 5G network-function context and assurance evidence.
10. Inspect the response recommendation and human-approval requirement.

## Research Validation

The repository contains evaluation scripts and evidence for:

- capture/file-holdout testing;
- calibration evidence including Brier score and calibration bins;
- feature drift baselines;
- reproducibility metadata such as model SHA-256 and training-file lists;
- open-world / unknown-traffic evaluation;
- explicit handling of limitations instead of presenting unsupported accuracy claims.

A key result documented by the project is that a closed-set binary model may fail to generalize to a completely unseen attack capture. 5G Sentinel treats this as a research finding and uses unknown/abstain behaviour plus human approval rather than hiding the limitation.

## Assurance-Gated Adaptive Response (AGAR)

AGAR creates a response-assurance view based on multiple forms of evidence:

- detection confidence;
- risk-decomposition fidelity;
- 5G network-function mapping confidence;
- counterfactual/safe-twin residual risk;
- model-health and drift evidence.

If critical evidence is unavailable, the result is **`HUMAN_APPROVAL_REQUIRED`** and automatic network action remains disabled. This makes the response workflow explainable, auditable, and fail-closed.

## Screenshots

### Sentinel Command Center

![5G Sentinel Command Center](FIGURE_SENTINEL_COMMAND_CENTER.png)

### Explainability View

![5G Sentinel Explainability](FIGURE_SENTINEL_EXPLAINABILITY.png)

### Telemetry Replay

![5G Sentinel Replay](FIGURE_SENTINEL_REPLAY.png)

## Documentation Included

The repository contains supporting Capstone 2 material covering:

- architecture;
- problem statement;
- implementation plan;
- dataset adapter audit;
- dataset and enhancement plan;
- evaluation;
- open-world research;
- innovation and assurance design;
- viva guidance;
- compiled/final project reports.

## Safety and Scope

5G Sentinel is an academic/research prototype. Mock replay and response functions are designed for demonstration and evaluation. Response actions are simulation-only or human-approved; the repository does not claim uncontrolled autonomous defence in a production 5G network.

## Project

**Capstone 2 — 5G Sentinel (SIEM)**  
Cybersecurity / 5G Network Security / Security Monitoring / Machine Learning / Explainable Security Analytics
