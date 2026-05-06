# 📈 VittaDrishti: AI Financial Intelligence Hub

**VittaDrishti** (meaning *Financial Vision* or *Perspective* in Sanskrit) is an industrial-grade, AI-powered financial intelligence platform. It merges real-time market data, AI-driven predictive modeling, and intelligent conversational research into a beautiful, high-performance web experience. 

---

## 🌟 What is VittaDrishti? (The Simple Explanation)

Have you ever wished you had a team of professional financial analysts, risk managers, and market researchers working for you around the clock? That is exactly what **VittaDrishti** is. 

Instead of jumping between complex spreadsheets, dense financial PDF reports, and endless news feeds, VittaDrishti gathers all of this into one visual hub. It uses state-of-the-art Artificial Intelligence to read financial documents, analyze news sentiment, and test how your investments would perform during major global crises—all in a matter of seconds.

### Who is this for?
* 🚀 **Individual Investors** who want a clear, visual understanding of their portfolio's health.
* 📊 **Financial Analysts** who need to dissect lengthy financial reports and PDFs without reading hundreds of pages manually.
* 🛡️ **Risk Managers** who want to stress-test portfolios under historic or custom "What-If" crisis scenarios.

---

## 🚀 Key Features & How They Help You

### 🧠 1. "What-If" Crisis Simulator (Risk Stress-Tester)
* **What it is:** A simulator that tests how your investments would survive major financial crashes.
* **How it works for you:** You can select a historic crisis (like the **2008 Global Financial Crisis**, the **2000 Dot-com Bubble Burst**, or the **2020 COVID-19 Crash**) or type in your own custom event (e.g., *"Sudden oil price spike"* or *"AI sector correction"*). Our AI immediately calculates estimated price shocks, displays simulated portfolio losses, shows visual sector heatmaps, and estimates how many years it would take for your assets to recover.
* **The Benefit:** You find out where your investments are vulnerable *before* a real crisis happens.

### 📚 2. Conversational Research Copilot (PDF Reader)
* **What it is:** An interactive AI assistant that has "perfect memory" of your uploaded financial documents.
* **How it works for you:** Upload lengthy, boring files (like company annual reports, market outlooks, or PDFs). Instead of scrolling and searching, you can simply text the AI: *"What are the key risk factors mentioned on page 14?"* or *"Summarize the company's Q3 earnings report."*
* **The Benefit:** You save hours of reading and extract crucial insights instantly.

### 📊 3. Real-Time Market Mood Analyzer (News Feed & Sentiment)
* **What it is:** An automated news reader that gauges the overall "mood" of the stock market.
* **How it works for you:** The platform ingests real-time financial news, and the AI automatically tags each headline as **Positive**, **Neutral**, or **Negative**. It then summarizes these into clean charts and sector indicators.
* **The Benefit:** You instantly understand whether market sentiment is optimistic or panicked without scrolling through hundreds of articles.

### 🎯 4. Smart Portfolio Generator & visualizer
* **What it is:** A tool that suggests customized investment allocations based on your comfort level.
* **How it works for you:** Input your desired investment amount and select your risk profile (Conservative, Moderate, or Aggressive). The system generates a mathematically balanced portfolio and displays it via interactive pie charts, risk gauges, and allocation summaries.
* **The Benefit:** Ensures your money is divided up in a way that matches your long-term goals and comfort zone.

---

## 🏗️ Technical Architecture (The Engine)

Behind the beautiful screens lies an advanced, multi-service architecture designed for maximum speed, security, and intelligence:

* **Frontend (The Visual Layer):** Built with **Next.js 14**, **React 18**, and styled with **Tailwind CSS**. It uses **Framer Motion** for fluid animations and **Recharts** to display real-time financial graphs. It features an industrial-grade Fintech dark mode.
* **Backend (The Core AI & Calculations):** A high-performance **Python FastAPI** server that coordinates calculations, database writes, and artificial intelligence queries.
* **Intelligence Layer (The AI Brain):** 
  * **Google Gemini Pro** acts as the core reasoning engine and text-embedding model (`text-embedding-004`).
  * **Llama 3 (via Groq API)** executes low-latency, real-time structured calculations for the Crisis Stress Simulator.
  * **Pinecone Vector Database** stores processed text from uploaded PDFs, allowing the AI to fetch relevant facts and answer questions in milliseconds using a **RAG (Retrieval-Augmented Generation)** pipeline.
* **Database & Security (The vault):** **Supabase (PostgreSQL)** securely handles user accounts, saved portfolios, and chat logs, protected by strict **Row Level Security (RLS)**.

---

## 🛠️ Developer Setup & Execution Guide

### 1. Prerequisites
* **Node.js** (v18+)
* **Python** (3.10+)
* **Supabase Account** (Database setup)
* **Pinecone Account** (Index: 768-dimension, Cosine metric)

---

### 2. Configure Environment Variables

Create `.env` files in both the `/backend` and `/frontend` directories using the reference keys below:

#### `/backend/.env`
```env
GEMINI_API_KEY=your_gemini_key
PINECONE_API_KEY=your_pinecone_key
PINECONE_ENVIRONMENT=your_region
PINECONE_INDEX_NAME=your_index
SUPABASE_URL=your_supabase_url
SUPABASE_SERVICE_KEY=your_service_role_key
GROQ_API_KEY=your_groq_key
TAVILY_API_KEY=your_tavily_key
ALPHA_VANTAGE_API_KEY=your_av_key
```

#### `/frontend/.env`
```env
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_anon_key
NEXT_PUBLIC_API_URL=http://localhost:8000
```

---

### 3. Running the Project Locally

You need to run both the Python backend and the Next.js frontend concurrently:

#### Tab 1: AI Backend (Python FastAPI)
```bash
cd backend
python -m venv venv

# Windows:
venv\Scripts\activate
# Mac/Linux:
source venv/bin/activate

pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

#### Tab 2: Frontend (Next.js 14)
```bash
cd frontend
npm install
npm run dev
```

Visit: `http://localhost:3000` to interact with the platform!

---

## 🌐 Deployment (Render Blueprint)

VittaDrishti is fully configured for easy one-click deployment on [Render](https://render.com) using the included `render.yaml` blueprint.

### Option A: Automatic Blueprint Deployment
1. Connect your GitHub repository to your Render account.
2. Go to **Blueprints** inside the Render Dashboard and click **New Blueprint Instance**.
3. Render automatically reads `render.yaml` and requests the necessary environment variables.
4. *Note:* For `NEXT_PUBLIC_API_URL`, type in your backend's expected Render URL (e.g., `https://vittadrishti-backend.onrender.com`).
5. Deploy!

### Option B: Manual Setup
If setting up web services individually on Render:
* **Backend Web Service:**
  * Runtime: `Python`
  * Build Command: `pip install -r requirements.txt`
  * Start Command: `uvicorn main:app --host 0.0.0.0 --port $PORT`
  * Root Directory: `backend`
* **Frontend Web Service:**
  * Runtime: `Node` / `Next.js`
  * Build Command: `npm install && npm run build`
  * Start Command: `npm run start`
  * Root Directory: `frontend`
  * Env Var: `NEXT_PUBLIC_API_URL` set to your backend's Render service URL.

---

## 🛡️ Security, Performance & Scalability
* **Secure Data Management:** All user actions, portfolio histories, and conversation threads are locked down behind Supabase RLS. Users can only access their own data.
* **Low-Latency RAG Pipeline:** Context extraction from Pinecone uses dense cosine vector matching to answer complex financial queries under 1.5 seconds.
* **Modern Deployment Scaling:** Containerizable design ready for vertical/horizontal scaling on modern cloud infrastructure.
