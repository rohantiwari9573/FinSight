<div align="center">

# FinSight

**An AI-powered financial assistant for small businesses: transaction tracking, cash-flow analytics, anomaly alerts, a natural-language finance chatbot and one-click PDF reports.**

![React](https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express_5-000000?style=flat-square&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)
![Groq](https://img.shields.io/badge/Groq-Llama_3.3_70B-F55036?style=flat-square)

**[Live demo](https://fin-sight-murex.vercel.app/)**

</div>

<br />

<img src="docs/screenshots/landing.png" alt="FinSight sign-in page" width="100%" />

---

## Features

| | |
|---|---|
| 📊 **Dashboard** | Revenue, expense and net-profit KPIs, a financial health score, monthly trends and an expense breakdown |
| 💸 **Transactions** | Record and categorize income and expenses |
| 📈 **Cash flow** | Month-by-month cash-flow chart with labeled axes |
| 🚨 **Anomaly alerts** | Flags transactions that are far above a user's historical average |
| 💡 **AI insights** | Summaries of trends and unusual spending patterns |
| 🤖 **AI chatbot** | Ask questions like *"Why is cash flow down this month?"* in plain language (Groq, Llama 3.3 70B) |
| 🧾 **Reports** | Profit & loss and tax summary views |
| 📄 **PDF export** | One-click monthly, yearly or all-time reports (PDFKit) |

## Architecture

```mermaid
flowchart LR
    UI["React 19 + Vite<br/>Recharts"] -->|"REST · JWT"| API["Express 5 API"]
    API --> DB[("MongoDB<br/>Mongoose")]
    API --> LLM["Groq API<br/>Llama 3.3 70B"]
    API --> PDF["PDFKit<br/>report generation"]
```

The API exposes `/api/auth`, `/api/transactions`, `/api/dashboard`, `/api/insights`, `/api/ai/chat` and `/api/reports/export`. Everything except auth requires a JWT.

## Getting started

**Prerequisites:** Node.js (LTS), a MongoDB connection string and a [Groq](https://console.groq.com) API key.

Create `server/.env`:

```env
MONGO_URI=mongodb+srv://...
JWT_SECRET=change-me
GROQ_API_KEY=gsk_...
CLIENT_URL=http://localhost:5173
```

```bash
# API
cd server
npm install
npm run dev

# Web client (in a second terminal)
cd client
npm install
npm run dev
```

To fill an account with sample transactions, run `node scripts/seedDemo.js --email you@example.com` from `server/`.

## Project structure

```text
client/src/
  pages/        Dashboard, Transactions, Cash Flow, Insights, Chatbot, P&L, Tax Summary
  components/   KPI grid, charts, health score, chat, sidebar
server/
  routes/ · controllers/   REST endpoints
  services/     AI assistant, insights, anomaly detection, dashboard aggregation
  models/       User, Transaction (Mongoose)
  scripts/      demo data seeding
```

## Team

FinSight is a team project, originally developed in [Lakshya080805/FinSight](https://github.com/Lakshya080805/FinSight).

- **Lakshya Singhal:** lead developer
- **Rohan Tiwari:** contributor

## License

Proprietary. All rights reserved.
