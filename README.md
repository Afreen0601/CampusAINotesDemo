# 📚 AI-Book — Digital Notes Sharing & Academic Assistant System

> An AI-powered digital academic repository and notes sharing platform tailored for college students and faculty. Organize lecture notes semester-wise and subject-wise, read verified PDFs with an in-app viewer, test your understanding with AI-generated quizzes, and consult the Gemini-powered academic tutor.

[![Node.js](https://img.shields.io/badge/Node.js-20+-68a063?style=flat-square&logo=node.js)](https://nodejs.org)
[![React](https://img.shields.io/badge/React-19-61dafb?style=flat-square&logo=react)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-3178c6?style=flat-square&logo=typescript)](https://www.typescriptlang.org)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-38bdf8?style=flat-square&logo=tailwindcss)](https://tailwindcss.com)
[![Supabase](https://img.shields.io/badge/Supabase-PostgreSQL-3ecf8e?style=flat-square&logo=supabase)](https://supabase.com)
[![Google Gemini](https://img.shields.io/badge/Google_Gemini-2.5_Flash-8e75ff?style=flat-square&logo=google)](https://ai.google.dev)

---

## 🌟 Highlights & Features

- **Semester & Subject Curriculum Structure**:
  - Organized navigation across college semesters (Semesters 1 through 6).
  - Categorized subject repositories (BBA & BCA programs supported).
  - Search, filter by subject, and sort notes by newest upload, downloads, or views.

- **Interactive Note & PDF Viewer**:
  - In-browser reading interface with zoom controls, full-screen toggle, dark/light reading modes, and page navigation.
  - One-click PDF download of verified academic materials.

- **🤖 Google Gemini AI Academic Assistant**:
  - **Instant Note Summarizer**: Generate concise, exam-focused key takeaways from any uploaded note unit.
  - **Practice Quiz Generator**: Auto-generate multiple-choice practice tests tailored to specific curriculum topics with real-time scoring and explanations.
  - **Interactive Tutor Chat**: Ask conceptual questions, clarify formulas, and get contextual help from the AI tutor.

- **Role-Based Authentication**:
  - **Students**: Register with Student ID, program (BBA / BCA), bookmark favorite notes, track quiz history and averages.
  - **Faculty / Teachers**: Upload lecture notes, manage curriculum syllabi, and monitor academic materials.

- **Supabase Cloud Database**:
  - Persistent cloud storage for users, notes, semesters, and subjects with Row-Level Security (RLS).
  - Real-time connection status indicator with in-app schema sync.

---

## 🛠️ Tech Stack

- **Frontend**: React 19, TypeScript, Tailwind CSS v4, Lucide React, Framer Motion
- **Backend**: Node.js, Express, Multer (file uploads)
- **Database**: Supabase (PostgreSQL with Row Level Security)
- **AI Engine**: Google Gemini API (`@google/genai` SDK)
- **Bundler & Tooling**: Vite, esbuild, TypeScript compiler

---

## 🚀 Getting Started

### Prerequisites

Ensure you have installed:
- [Node.js](https://nodejs.org/) (version 18 or 20+ recommended)
- `npm`, `pnpm`, or `bun`

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/ai-book-notes.git
cd ai-book-notes
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

Copy the example environment file:

```bash
cp .env.example .env
```

Open `.env` and fill in your keys:

```env
# Gemini API Key for AI study tutor & quiz generation
# Get one at https://aistudio.google.com/app/apikey
GEMINI_API_KEY="your-gemini-api-key"

# Supabase Configuration
# Found in your Supabase Project Settings -> API
SUPABASE_URL="https://your-project-id.supabase.co"
SUPABASE_KEY="your-supabase-anon-or-service-key"

# Application host port (optional, defaults to 3000)
PORT=3000
```

### 4. Set Up Supabase Database

1. Open your [Supabase Dashboard](https://supabase.com/dashboard).
2. Go to the **SQL Editor** (`/sql/new`).
3. Open `supabase-schema.sql` from the root of this project, paste the entire contents into the editor, and click **Run**.
4. The schema creates all required tables (`users`, `semesters`, `subjects`, `notes`), indexes, and RLS policies.

### 5. Run Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## 📦 Production Build

To compile both the Vite frontend bundle and the Express backend server:

```bash
npm run build
```

To run the production build:

```bash
npm run start
```

---

## 🚢 Deployment Guide

### Deploying to Render / Railway / Fly.io

1. **Build Command**: `npm run build`
2. **Start Command**: `npm run start`
3. **Environment Variables**: Add `GEMINI_API_KEY`, `SUPABASE_URL`, `SUPABASE_KEY`, and `NODE_ENV=production`.

### Deploying to Vercel or Netlify

For serverless platforms, ensure API proxying routes are forwarded to your serverless backend functions or host the full-stack container on [Cloud Run](https://cloud.google.com/run) or [Render](https://render.com).

---

## 📂 Project Structure

```
├── .github/
│   └── workflows/
│       └── ci.yml               # GitHub Actions CI workflow
├── public/                      # Static web assets
├── server/
│   └── supabaseClient.ts        # Supabase database client and health checks
├── src/
│   ├── components/              # React UI components
│   │   ├── AiStudyModal.tsx     # Gemini AI tutor, summary & quiz generator
│   │   ├── LoginModal.tsx       # Authentication & registration modal
│   │   ├── Navbar.tsx           # App header, role switcher & navigation
│   │   ├── PdfViewerModal.tsx   # Document reader & viewer
│   │   ├── SemesterNotesExplorer.tsx # Semester & subject notes browser
│   │   ├── SupabaseModal.tsx    # Supabase connection & sync manager
│   │   └── UploadNoteModal.tsx  # Document upload modal
│   ├── data/
│   │   └── seedData.ts          # Seed curriculum and mock notes
│   ├── App.tsx                  # Main application state & routing
│   ├── main.tsx                 # React entry point
│   ├── types.ts                 # TypeScript type definitions
│   └── index.css                # Tailwind CSS v4 styling
├── index.html                   # HTML template
├── package.json                 # Project dependencies & scripts
├── server.ts                    # Full-stack Express server + Vite middleware
├── supabase-schema.sql          # PostgreSQL database schema & migrations
└── vite.config.ts               # Vite bundler configuration
```

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
