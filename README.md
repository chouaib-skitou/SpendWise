# 💸 SpendWise – Personal Finance Tracker

> **SpendWise** is a modern **Personal Finance & Budget Tracking App** built with  
> **Node.js + TypeScript** for the API Gateway and **Symfony 7 + API Platform** for the Finance Service,  
> paired with a **React + TypeScript** frontend.

SpendWise helps you **organise your accounts, track expenses, create budgets, and analyse your spending habits** — securely and effortlessly.

---

## ✨ Key Features

- 🔐 **Authentication & Security**
  - Sign-up / Sign-in with **JWT Access + Refresh**
  - Email verification & password reset
  - Optional **MFA (TOTP)**
  - Role-based access control (`USER`, `ADMIN`)

- 💳 **Accounts & Categories**
  - Managed by Symfony Finance Service
  - Multiple accounts: Cash, Bank, Card, Savings
  - Hierarchical expense categories

- 💸 **Budgets & Transactions**
  - Monthly budgets per category
  - Expense / Income / Transfer transactions
  - Transaction **splits** across categories
  - Tags, notes & CSV import
  - Auto-categorisation rules (coming soon)

- 📊 **Analytics & Reports**
  - Spending by category / month
  - Budget vs Actual
  - Cashflow trends

- 📦 **Planned Enhancements**
  - Recurring transactions
  - Receipt uploads (S3/MinIO)
  - Budget alerts & notifications
  - Multi-currency & shared budgets
  - Open Banking integration

---

## 🏗️ Architecture Overview

SpendWise follows a **modular service-oriented architecture**:

```
SpendWise/
├─ apps/
│  ├─ gateway/           # Node.js + TypeScript – Auth, orchestration, integrations
│  ├─ finance-api/       # Symfony + API Platform – domain logic & persistence
│  └─ web/               # React + TypeScript frontend
├─ infra/
│  └─ docker/            # Docker Compose for local dev (Postgres, Redis, Mailhog)
└─ README.md
```

### Tech Stack

| Layer             | Technology |
|-------------------|------------|
| Gateway Backend   | Node.js 22 + TypeScript (NestJS / Fastify) |
| Domain Service    | Symfony 7 + API Platform + Doctrine |
| Database          | PostgreSQL + Flyway / Doctrine migrations |
| Caching           | Redis |
| Frontend          | React 19 + TypeScript + Vite |
| Documentation     | Swagger (Node) + API Docs (API Platform) |
| Testing           | Jest (Node) + PHPUnit (Symfony) |
| Dev Infrastructure| Docker Compose (Postgres, Redis, Mailhog) |
| Storage (future)  | S3 / MinIO for receipt images |

---

## 🚀 Getting Started

### 1. Prerequisites
- Node.js 22+
- pnpm / npm / yarn
- PHP 8.3+
- Composer
- Docker & Docker Compose

### 2. Clone the Repository
```bash
git clone https://github.com/chouaib-skitou/SpendWise.git
cd SpendWise
```

### 3. Start Dev Infrastructure
```bash
docker compose -f infra/docker/docker-compose.yml up -d
```

Services started:
- 🐘 **Postgres** → `localhost:5432`
- 🔴 **Redis** → `localhost:6379`
- 📬 **Mailhog** → [http://localhost:8025](http://localhost:8025)

### 4. Run the Node Gateway
```bash
cd apps/gateway
pnpm install
pnpm run dev
```
- API → [http://localhost:8080](http://localhost:8080)  
- Swagger UI → [http://localhost:8080/docs](http://localhost:8080/docs)

### 5. Run the Symfony Finance API
```bash
cd apps/finance-api
composer install
symfony serve
```
- API Platform UI → [http://localhost:8000/api](http://localhost:8000/api)

---

## 🔑 Core Services

- **GatewayService (Node)** → authentication, token refresh, email verify, rate limit, MFA
- **FinanceService (Symfony)** → accounts, categories, budgets, transactions, reports
- **NotificationService (Node)** → emails, alerts, real-time updates
- **FileService (Node)** → upload receipts to S3/MinIO

---

## 🔐 Security Highlights

- Passwords hashed with **Argon2 / BCrypt**
- **JWT**: short-lived Access + long-lived Refresh with rotation
- Strict **CORS** policy
- Rate-limiting & IP blocking on sensitive endpoints
- Security headers: **CSP, HSTS, X-Content-Type-Options, Referrer-Policy**

---

## 📈 Roadmap

- [x] User auth (JWT, refresh, email verify)
- [ ] Accounts / Categories CRUD (Symfony)
- [ ] Budgets & Transactions MVP (Symfony)
- [ ] CSV Import & Splits
- [ ] Receipt uploads (S3/MinIO)
- [ ] Budget alerts & notifications
- [ ] Multi-currency support
- [ ] Shared budgets & collaboration
- [ ] Open Banking integration

---

## 🤝 Contributing
Contributions, issues and feature requests are welcome!  
Please follow the existing code style and include tests for new features.

---

## 📜 License
MIT © 2025 **SpendWise – Personal Finance Tracker**

---

> _“Track your spending. Master your budget. Achieve your goals.”_
