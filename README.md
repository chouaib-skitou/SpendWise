# 💸 SpendWise – Personal Finance Tracker

> **SpendWise** is a modern **Personal Finance & Budget Tracking App** built with  
> **Spring Boot (Java 21)** for the backend and **React + TypeScript** for the frontend.

SpendWise helps you **organise your accounts, track expenses, create budgets, and analyse your spending habits** — securely and effortlessly.

---

## ✨ Key Features

- 🔐 **Authentication & Security**
  - Sign-up / Sign-in with **JWT Access + Refresh**
  - Email verification & password reset
  - Optional **MFA (TOTP)**
  - Role-based access control (`USER`, `ADMIN`)

- 💳 **Accounts & Categories**
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

SpendWise starts as a **modular monolith** for simplicity and maintainability.

```
SpendWise/
├─ apps/
│  ├─ api/              # Backend – Spring Boot
│  └─ web/              # Frontend – React + TypeScript
├─ infra/
│  └─ docker/           # Docker Compose for dev (Postgres, Redis, Mailhog)
└─ README.md
```

### Tech Stack
| Layer             | Technology                                |
|-------------------|------------------------------------------|
| Backend           | Spring Boot 3.3+, Java 21                |
| Auth              | JWT Access/Refresh (OAuth2 RS)           |
| Database          | PostgreSQL + Flyway                      |
| Frontend          | React 19 + TypeScript + Vite             |
| Documentation     | OpenAPI / Swagger                        |
| Testing           | JUnit 5 + Testcontainers (PostgreSQL)    |
| Dev Infrastructure| Docker Compose (Postgres, Redis, Mailhog)|
| Future Storage    | S3 / MinIO for receipt images            |

---

## 🚀 Getting Started

### 1. Prerequisites
- Java 21
- Gradle 8+
- Docker & Docker Compose
- Node 18+ (for frontend later)

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

### 4. Run the Backend
```bash
cd apps/api
./gradlew flywayMigrate bootRun
```
- API → [http://localhost:8080](http://localhost:8080)  
- Swagger UI → [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)

---

## 🔑 Core Modules

- **AuthService** → login, register, refresh tokens, email verify
- **AccountsService** → manage accounts and balances
- **CategoriesService** → user-defined categories
- **BudgetService** → monthly budgets per category
- **TransactionService** → CRUD, splits, CSV import
- **ReportService** → spending charts, budget vs actual

---

## 🗄️ Database Schema (Simplified)

- `users` – authentication & profile  
- `accounts` – bank / cash / credit accounts  
- `categories` – hierarchical expense categories  
- `budgets` & `budget_items` – monthly budgets  
- `transactions` (+ splits, tags) – expense / income / transfer logs  

Migrations are handled by **Flyway** under  
`apps/api/src/main/resources/db/migration/`.

---

## 🔐 Security Highlights

- Passwords hashed with **BCrypt**
- **JWT**: short-lived Access + long-lived Refresh with rotation & revocation
- Strict **CORS** for frontend domains
- Rate-limit on login and password-reset endpoints
- Security headers: **CSP, HSTS, X-Content-Type-Options, Referrer-Policy**

---

## 📈 Roadmap

- [x] User auth (JWT, refresh, email verify)
- [] Accounts / Categories CRUD
- [] Budgets & Transactions MVP
- [ ] Auto-categorisation rules
- [ ] Recurring transactions
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
