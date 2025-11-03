# 📈 Signalist - Stock Tracker & Analysis App

Signalist is a modern, full-stack stock tracking application designed to help users make informed investment decisions. It provides real-time market data, personalized watchlists, interactive charts, and AI-powered daily email summaries tailored to the user's portfolio.

### ✨ [Live Demo Link ](https://stock-market-app-sage.vercel.app/)

---

## 🚀 Key Features

* **🔍 Advanced Stock Search**: Find any stock and get detailed information, including financial metrics and company profiles.
* **❤️ Personalized Watchlist**: Add and remove stocks from your personal watchlist to track your favorite companies.
* **📊 Interactive Charts**: Leverage the power of TradingView to analyze stock performance with various chart types and indicators.
* **📰 Top Market News**: Browse the latest financial news and top stories provided by the Finnhub API.
* **🤖 AI-Powered Daily Emails**: Receive a personalized daily email summarizing the latest news for the stocks on your watchlist, powered by Inngest and Nodemailer.
* **🔐 Secure Authentication**: Robust and secure user authentication system provided by Better Auth.
* **📱 Responsive Design**: A clean, modern UI built with Shadcn that works seamlessly on both desktop and mobile devices.

---

## 🛠️ Tech Stack

* **Framework**: Next.js 15 (App Router)
* **Language**: TypeScript
* **Styling**: Tailwind CSS, Shadcn/UI
* **Authentication**: Better Auth
* **Database**: MongoDB Atlas with Mongoose
* **Background Jobs & Automation**: Inngest
* **Email Service**: Nodemailer (with Google App Password)
* **APIs**: Finnhub API (Market Data & News), Google Gemini (AI Summaries)
* **Charting**: TradingView Lightweight Charts

---

## 🏁 Getting Started

### 1. Prerequisites

Make sure you have the following installed:
* [Node.js](https://nodejs.org/en/) (v18 or later)
* `npm`, `yarn`, or `pnpm`
* [Git](https://git-scm.com/)
* Inngest CLI (for background jobs)

### 2. Clone the Repository

```bash
git clone https://github.com/Maanav-1/Signalist_stock-tracker-app.git
cd Signalist_stock-tracker-app
```

### 3. Install Dependencies

```bash
npm install
# or
yarn install
# or
pnpm install
```

### 4. Set Up Environment Variables

Create a file named `.env.local` in the root of your project directory and add the following variables.

```env
# General
NODE_ENV='development'
NEXT_PUBLIC_BASE_URL='http://localhost:3000'

# MongoDB
MONGODB_URI='your_mongodb_connection_string'

# Better Auth
BETTER_AUTH_SECRET='generate_a_strong_secret_key' # Use a secure, random string
BETTER_AUTH_URL='http://localhost:3000'

# Google Gemini API
GEMINI_API_KEY='your_google_gemini_api_key'

# Nodemailer (using Gmail)
NODEMAILER_EMAIL='your-gmail-address@gmail.com'
NODEMAILER_PASSWORD='your_16_digit_google_app_password' # Important: This is NOT your regular password

# Finnhub API
NEXT_PUBLIC_FINNHUB_API_KEY='your_finnhub_api_key'
```

**How to get the `NODEMAILER_PASSWORD`:**

1. Go to your Google Account settings.
2. Navigate to `Security` -> `2-Step Verification` (it must be enabled).
3. At the bottom, click on `App passwords`.
4. Generate a new password for "Mail" on "Other (Custom name)" and use the 16-digit code provided.

### 5. Run the Development Servers
```bash
# In first terminal: Next.js dev server
npm run dev

# In second terminal: Inngest dev server (required for email automation)
npx inngest-cli@latest dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser to see the application running.

Note: The Inngest dev server is required for email automation (welcome emails and daily news updates) to work locally.

## ⚡ Background Jobs (Inngest)

Inngest powers our automated email delivery system:
- **Welcome Emails**: Personalized AI-generated welcome messages when users sign up
- **Daily News Digest**: Every day at 12 PM UTC, Inngest:
  1. Fetches news relevant to each user's watchlist
  2. Uses AI to summarize and personalize the content
  3. Delivers a curated email digest of market updates
  
Route: `/api/inngest` handles these scheduled tasks and event processing

-----

## 🌐 Environment Variables Explained

| Variable                      | Description                                                                                              |
| ----------------------------- | -------------------------------------------------------------------------------------------------------- |
| `NODE_ENV`                    | Sets the environment to `development` or `production`.                                                   |
| `NEXT_PUBLIC_BASE_URL`        | The base URL of your application.                                                                        |
| `MONGODB_URI`                 | The connection string for your MongoDB Atlas database.                                                   |
| `BETTER_AUTH_SECRET`          | A secret key used by Better Auth to sign and encrypt session data.                                       |
| `BETTER_AUTH_URL`             | The base URL of your app, used by Better Auth for callbacks.                                             |
| `GEMINI_API_KEY`              | Your API key for Google Gemini, used for AI-powered news summarization.                                  |
| `NODEMAILER_EMAIL`            | The Gmail address from which the daily summary emails will be sent.                                      |
| `NODEMAILER_PASSWORD`         | The 16-digit Google App Password for the sending email account.                                          |
| `NEXT_PUBLIC_FINNHUB_API_KEY` | Your API key for the Finnhub service to fetch stock data and news.                                      |


