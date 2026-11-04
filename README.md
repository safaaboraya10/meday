<p align="center">
  <img src="public/logo.png" alt="MeDay logo" width="140" />
</p>

<h1 align="center">MeDay Smart Platform</h1>

<p align="center">
  A full-stack web platform for a beauty &amp; aesthetics clinic, with an AI assistant
  that recommends treatments, online booking, and a complete admin system.
</p>

<p align="center">
  <img alt="React" src="https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white" />
  <img alt="Vite" src="https://img.shields.io/badge/Vite-7-646CFF?logo=vite&logoColor=white" />
  <img alt="Tailwind CSS" src="https://img.shields.io/badge/Tailwind-3-06B6D4?logo=tailwindcss&logoColor=white" />
  <img alt="FastAPI" src="https://img.shields.io/badge/FastAPI-Python-009688?logo=fastapi&logoColor=white" />
  <img alt="SQLite" src="https://img.shields.io/badge/SQLite-003B57?logo=sqlite&logoColor=white" />
  <img alt="Gemini" src="https://img.shields.io/badge/Google-Gemini-4285F4?logo=google&logoColor=white" />
</p>

---

## Overview

MeDay is a smart website for a real aesthetics clinic. Clients can browse treatments,
chat with an AI assistant that asks a few questions and recommends the right treatment,
and book an appointment. Clinic staff manage everything from role-based dashboards:
appointments, employees and shifts, customers, and the website's content.

## Features

**For clients**
- 🤖 **AI treatment assistant**: a chatbot that understands free-text questions, asks guided questions, and recommends treatments based on a scoring system
- 💆 **Treatment catalog**: treatment categories and detailed treatment pages
- 📅 **Online booking** and a personal **client area**
- 🔐 **Google sign-in**
- 🖼️ **Gallery** with lightbox, **About**, **Professional team**, and **Careers** pages

**For the clinic**
- 📊 **Admin dashboard**: clinic overview and insights
- 👥 **Staff, employee and shift management**, with role-based access (admin / secretary / staff)
- 🧾 **Customer management** and an **audit log** of admin actions
- ✏️ **Content management**: edit category pages and import the chatbot knowledge base from Excel
- 🗓️ **Secretary page** for managing appointments

## How the AI assistant works

1. **Gemini** reads the client's message and detects the intent (a question, a treatment, a concern…).
2. Answers are **grounded in the clinic's own knowledge base** (treatments, FAQs, clinic info), loaded from an Excel file into SQLite, so the bot doesn't make things up.
3. A **guided question flow + scoring engine** picks the best-matching treatments.
4. If the AI is unavailable, a **rule-based fallback** keeps the chat working.

## Architecture

![MeDay system architecture](poster-assets/meday-architecture-diagram.png)

| Layer | Technology |
|---|---|
| Frontend | React 19, Vite, Tailwind CSS, Framer Motion, React Router, Three.js |
| Backend | Python, FastAPI, Uvicorn |
| Database | SQLite |
| AI | Google Gemini API |
| Auth | Google OAuth + JWT |

## Run locally

**Backend**
```bash
cd backend
python -m venv venv
venv\Scripts\activate        # macOS/Linux: source venv/bin/activate
pip install -r requirements.txt
python import_meday_data.py  # builds the chatbot knowledge base from the Excel file
uvicorn main:app --reload
```

**Frontend** (in a second terminal, from the project root)
```bash
npm install
npm run dev
```

Copy `.env.example` → `.env` (frontend) and `backend/.env.example` → `backend/.env`, and fill in your keys
(`GEMINI_API_KEY`, `GOOGLE_CLIENT_ID`, `VITE_GOOGLE_CLIENT_ID`).

## Deployment

Free hosting with **Render** (backend) and **Vercel** (frontend). See [DEPLOY.md](DEPLOY.md).

## Team

Built as a final project by:

- [@safaaboraya10](https://github.com/safaaboraya10)
- [@olahassan123](https://github.com/olahassan123)
- [@marahab114-web](https://github.com/marahab114-web)
- Luna
