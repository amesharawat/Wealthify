# 💰 Wealthify — AI-Powered Personal Finance Platform

[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-CSS-06B6D4?style=for-the-badge&logo=tailwindcss)](https://tailwindcss.com/)
[![Prisma](https://img.shields.io/badge/Prisma-ORM-2D3748?style=for-the-badge&logo=prisma)](https://www.prisma.io/)
[![Supabase](https://img.shields.io/badge/Supabase-PostgreSQL-3ECF8E?style=for-the-badge&logo=supabase)](https://supabase.com/)
[![Clerk](https://img.shields.io/badge/Clerk-Auth-6C47FF?style=for-the-badge&logo=clerk)](https://clerk.com/)
[![Vercel](https://img.shields.io/badge/Deployed-Vercel-000000?style=for-the-badge&logo=vercel)](https://wealthify-nine.vercel.app/)

> A full-stack, AI-enhanced personal finance SaaS application that helps users track spending, manage budgets, scan receipts with AI, and receive automated financial insights — all in one place.

🔗 **Live Demo:** [wealthify-nine.vercel.app](https://wealthify-nine.vercel.app/)

---

## 📸 Screenshots

### 🏠 Landing Page
![Landing Page](https://github.com/amesharawat/Wealthify/blob/d0d8482258176fd1b94e47c124f18f14f768a098/Screenshot%20(891).png)

### 🏷️ Features Overview
![Features Overview](https://github.com/amesharawat/Wealthify/blob/1d8725d6915b4c9ae3f9574d475942379d6028d2/Screenshot%20(892).png)

### 📊 Dashboard
![Dashboard](https://github.com/amesharawat/Wealthify/blob/e7897887f793c5f340356357d04a279d9877f250/Screenshot%20(893).png)

### 📈 Analytics & Expense Breakdown
![Analytics](https://github.com/amesharawat/Wealthify/blob/b8d54bf85bff7868d060ea87141609b31c4849d5/Screenshot%20(894).png)

### 💳 Transaction Page
![Transactions](https://github.com/amesharawat/Wealthify/blob/04d97f8b7a0c08d72db9fcb5829b0f3b94273c4f/Screenshot%20(895).png)

### ➕ Add Transaction
![Add Transaction](https://github.com/amesharawat/Wealthify/blob/a2445a5146e42064ff2bdc712c6011a8e94192c9/Screenshot%20(896).png)

---

## ✨ Key Features

- 🏦 **Multi-Account Management** — Create and manage multiple financial accounts (checking, savings) with custom balances and a configurable default account
- 🤖 **AI Smart Receipt Scanner** — Upload a receipt image and let Google Gemini AI automatically extract and fill in the amount, date, description, and category
- 📊 **Interactive Dashboards** — Visualize income vs. expenses using dynamic bar charts and category-wise pie charts across custom timelines (7 days, 1 month, 3 months, etc.)
- 💸 **Advanced Transaction Management** — Real-time search, category filtering, bulk selection, and batch deletion across your full transaction ledger
- 🔁 **Recurring Transactions** — Set up daily, weekly, monthly, or yearly transactions that auto-process via scheduled background jobs
- 🚨 **Smart Budget Alerts** — Set monthly spending thresholds and receive automated email alerts when you cross 80% of your budget
- 📈 **AI Monthly Financial Reports** — Automated AI-generated monthly reports with personalized spending insights delivered directly to your inbox on the 1st of each month
- 🛡️ **Rate Limiting & Bot Protection** — Powered by Arcjet with shield defense, bot detection, and per-user API request limits (max 10 requests/hour)
- 🔐 **Secure Authentication** — Full sign-in/sign-up flow with Google OAuth via Clerk

---

## 🛠️ Tech Stack

| Category | Technology |
|----------|------------|
| **Framework** | Next.js 15 (App Router, Server Actions) |
| **Styling** | Tailwind CSS, Shadcn UI, Lucide React |
| **Database** | Supabase (PostgreSQL) |
| **ORM** | Prisma |
| **Authentication** | Clerk (Google OAuth) |
| **AI** | Google Gemini 1.5 Flash |
| **Background Jobs** | Inngest (Cron Jobs, Queues) |
| **Email** | Resend + React Email |
| **Charts** | Recharts |
| **Forms & Validation** | React Hook Form + Zod |
| **Security** | Arcjet (Rate Limiting, Bot Protection) |
| **Date Utilities** | date-fns |
| **Deployment** | Vercel |

---

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- A Supabase account
- A Clerk account
- A Resend account
- A Google Gemini API key
- An Arcjet account
- An Inngest account

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/amesharawat/Wealthify.git
cd Wealthify
```

**2. Install dependencies**

> ⚠️ The `--legacy-peer-deps` flag is required due to peer dependency conflicts between React 19 and certain packages (e.g. Shadcn UI components). This is intentional and safe.

```bash
npm install --legacy-peer-deps
```

**3. Set up environment variables**

Copy the example env file and fill in your keys:

```bash
cp .env.example .env
```

Here's the full list of required variables:

```env
# Database (Supabase)
DATABASE_URL=your_supabase_connection_string
DIRECT_URL=your_supabase_direct_url

# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
CLERK_SECRET_KEY=your_clerk_secret_key
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up

# Google Gemini AI
GEMINI_API_KEY=your_gemini_api_key

# Resend Email
RESEND_API_KEY=your_resend_api_key

# Arcjet Security
ARCJET_KEY=your_arcjet_key

# Inngest Background Jobs
INNGEST_EVENT_KEY=your_inngest_event_key
INNGEST_SIGNING_KEY=your_inngest_signing_key
```

**4. Set up the database**

```bash
npx prisma generate
npx prisma db push
```

**5. Run the development server**

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to view the app.

**6. Run the Inngest dev server** _(in a separate terminal)_

```bash
npx inngest-cli@latest dev
```

---

## 📁 Project Structure

```
Wealthify/
├── actions/             # Next.js Server Actions (transactions, budget, accounts, email)
├── app/
│   ├── (auth)/          # Clerk sign-in/sign-up pages
│   ├── (main)/          # Protected app routes (dashboard, accounts, transactions)
│   ├── api/             # API routes (Inngest handler)
│   └── lib/             # Zod schemas, utilities
├── components/          # Shared UI components (Shadcn, custom)
├── data/                # Static/seed data
├── emails/              # React Email templates
├── hooks/               # Custom React hooks (useFetch)
├── lib/                 # Prisma client, utility functions
├── prisma/              # Prisma schema
├── public/              # Static assets
├── .gitignore
├── components.json
├── eslint.config.mjs
├── jsconfig.json
├── middleware.js
├── next.config.mjs
├── package.json
└── postcss.config.mjs
```

---

## 🌐 Deployment

This project is deployed on **Vercel**. To deploy your own instance:

1. Push your code to GitHub
2. Import the repository on [vercel.com](https://vercel.com)
3. Add all environment variables in Vercel's project settings
4. Deploy

---

## 📬 Contact

**Amesha Rawat**
- GitHub: [@amesharawat](https://github.com/amesharawat)
- Live Project: [wealthify-nine.vercel.app](https://wealthify-nine.vercel.app/)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
