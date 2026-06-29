# 🤖 DevSecOps Agent — Telegram-Controlled CI/CD

> An AI-powered DevSecOps agent controlled entirely via Telegram. Trigger pipelines, run security scans, deploy applications, and receive real-time alerts — without leaving your chat.

---

## Architecture

```
Telegram User
     │
     ▼
Telegram Bot  (node-telegram-bot-api)
     │
     ▼
AI Agent  (Express.js · Mistral AI · Claude fallback)
     │
     ├──► GitLab CI/CD   →  8-stage pipeline
     ├──► SonarQube       →  SAST
     ├──► Trivy           →  Docker image scanning
     ├──► Gitleaks        →  Secret detection
     └──► npm audit       →  Dependency scanning
                               │
                               ▼
                    Prometheus + Grafana · Redis
```

## What It Does

| | |
|---|---|
| **Pipeline** | Trigger, cancel, retry, status, logs — from Telegram |
| **Security** | SAST, dependency, container, and secret scans on demand |
| **Deployment** | Staging (auto) · Production (confirmation required) · Rollback |
| **AI Reports** | Security analysis and recommendations via Mistral AI / Claude |
| **Notifications** | Real-time alerts for pipeline events, vulnerabilities, deploys |

## Stack

| Component | Technology |
|---|---|
| Bot | Node.js · node-telegram-bot-api |
| AI Agent | Node.js · Express.js |
| LLM | Mistral AI (primary) · Claude / Anthropic (fallback) |
| CI/CD | GitLab CI/CD — 8 stages |
| SAST | SonarQube |
| Container scan | Trivy |
| Secret detection | Gitleaks |
| Dependencies | npm audit |
| Cache | Redis 7 |
| Monitoring | Prometheus + Grafana |
| Orchestration | Docker Compose |

## Project Structure

```
├── telegram-bot/         # Bot — commands, auth, inline buttons
├── agent-ia/             # Express API — orchestration, AI, webhooks
├── gitlab-ci/            # .gitlab-ci.yml — 8-stage DevSecOps pipeline
├── deployment/           # Docker Compose + Prometheus config
├── security-tools/       # SonarQube, Trivy, Gitleaks, npm audit configs
└── docs/INSTALL.md       # Full installation guide
```

> See [`docs/INSTALL.md`](docs/INSTALL.md) to get started.
