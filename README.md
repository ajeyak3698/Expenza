# Expenza

Expenza is a modern, secure, and delightful personal expense-tracking application that helps individuals and small teams track spending, manage budgets, and gain insights into their financial habits. Built with a focus on usability, performance, and data privacy, Expenza combines a clean interface with powerful reporting and automation features.

## Key Features

- Intuitive expense entry with categories, tags, and receipts
- Recurring transactions and bill reminders
- Budgets with alerts and progress tracking
- Powerful filters and search (date ranges, categories, tags, merchants)
- Visual insights: charts for spending by category, trends, and cashflow
- CSV import/export and quick backup/restore
- Multi-currency support and simple conversion
- Offline-first data model with secure sync (opt-in)
- Role-based access for team accounts (owner, admin, member)

---

## Table of Contents

- [Demo](#demo)
- [Screenshots](#screenshots)
- [Tech Stack](#tech-stack)
- [Architecture Overview](#architecture-overview)
- [Quick Start](#quick-start)
  - [Prerequisites](#prerequisites)
  - [Local Development (Full-stack)](#local-development-full-stack)
  - [Environment Variables](#environment-variables)
- [Usage](#usage)
- [Testing](#testing)
- [Deployment](#deployment)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

---

## Demo

A live demo (if available) can be hosted at: https://expenza.example.com

If you have a local build, run the app following the instructions below and open http://localhost:3000 (web) or run the mobile app through the simulator.

## Screenshots

Place screenshots in /assets/screenshots and reference them here.

- Dashboard — Overview of current balances and recent activity
- New Expense — Fast entry with receipt capture
- Reports — Charts showing spending by category

---

## Tech Stack

Expenza is intentionally modular so teams can pick technologies that suit them. A recommended stack:

- Frontend: React (TypeScript) or React Native for mobile
- Backend: Node.js + Express (TypeScript) or NestJS
- Database: PostgreSQL (production) / SQLite (development)
- Authentication: JWT / OAuth 2.0 + optional 2FA
- Storage: S3-compatible object storage for receipts
- CI/CD: GitHub Actions
- Containerization: Docker

---

## Architecture Overview

- Client(s): Web and/or Mobile apps that call REST / GraphQL APIs
- API Server: Auth, expense CRUD, reporting, notifications
- Database: Stores users, accounts, transactions, categories, tags
- Worker Queue: Background jobs for recurring payments, receipts OCR, report generation
- Storage: Object store for receipts and exports

Security & privacy considerations:
- Encrypt sensitive fields at rest (e.g., tokens, payment references)
- Use HTTPS everywhere and enforce secure cookies
- Allow users to export and delete their data easily

---

## Quick Start

### Prerequisites

- Node.js 18+ and npm or yarn
- PostgreSQL 12+ (or Docker)
- Docker & Docker Compose (recommended for an isolated dev environment)

### Local Development (Full-stack)

1. Clone the repository

   git clone https://github.com/ajeyak3698/Expenza.git
   cd Expenza

2. Copy the example env files

   cp .env.example .env
   cp server/.env.example server/.env   # if mono-repo has server folder
   cp client/.env.example client/.env   # if applicable

3. Start the database (local or with Docker Compose)

   # using Docker Compose (recommended)
   docker-compose up -d

4. Install dependencies

   # From the repo root (adjust if there are /server and /client packages)
   npm install
   cd server && npm install
   cd ../client && npm install

5. Run migrations

   # Example with TypeORM or Prisma
   npx prisma migrate dev --name init
   # OR
   npm run migrate

6. Start the backend and frontend

   # From repo root in separate terminals
   cd server && npm run dev
   cd client && npm run dev

7. Open the application

   - Web: http://localhost:3000
   - API: http://localhost:4000

### Environment Variables

Create a .env file from .env.example and set the following variables as appropriate:

- DATABASE_URL=postgresql://user:password@localhost:5432/expenza
- PORT=4000
- JWT_SECRET=replace_me_with_a_strong_secret
- S3_ENDPOINT= (if using S3 for receipts)
- S3_BUCKET=expenza-receipts
- SENDGRID_API_KEY= (for email notifications)

Example .env.example (simplified):

DATABASE_URL=postgresql://postgres:postgres@localhost:5432/expenza
PORT=4000
JWT_SECRET=change_this_to_a_strong_secret
NODE_ENV=development

---

## Usage

- Add accounts and categories
- Create expenses quickly using the Add Expense flow
- Attach receipts (camera or file upload)
- Create budgets and set monthly/weekly targets
- Use the Reports view to analyze spending trends
- Export transactions to CSV for tax or bookkeeping

CLI helpers (if provided):

- Seed demo data: npm run seed
- Create admin user: npm run create-admin

---

## Testing

Run unit and integration tests:

- Install dev dependencies
- Run tests with your test runner (Jest recommended)

Commands:

npm run test
npm run test:watch

---

## Deployment

Simple deployment patterns:

- Docker: Build images for server and client, deploy to your registry, run on ECS/GKE.
- Vercel / Netlify: Deploy the client
- Render / Railway / Heroku: Deploy server and DB

CI example (GitHub Actions):
- Build and test on push
- Build Docker images on release
- Deploy to staging on push to main

---

## Roadmap

Planned features:
- Bank account integrations (Plaid / Open Banking)
- Smart categorization using ML
- Multi-user household accounts and permissions
- In-app budgeting advice and insights
- Scheduled exports and accountant access

If you want to contribute a feature, create a discussion or ticket.

---

## Contributing

Thank you for considering contributing to Expenza! We follow a simple contribution process:

1. Fork the repository
2. Create a feature branch: git checkout -b feat/your-feature
3. Commit changes with clear messages
4. Open a pull request describing your changes and linking any related issues

Please read CONTRIBUTING.md (if present) for coding standards, commit message format, and review process.

---

## Code of Conduct

This project follows the Contributor Covenant Code of Conduct. By participating you agree to abide by its terms.

---

## Acknowledgements

- Thank you to all contributors and users
- Icons and illustrations from free/open sources; see assets/credits.md

---

## Contact

- Repository: https://github.com/ajeyak3698/Expenza
- Issues: https://github.com/ajeyak3698/Expenza/issues
