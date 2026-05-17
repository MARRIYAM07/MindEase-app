# MindEase 🌿
### *A quiet space to unburden.*

> A bilingual (English + اردو) AI-powered mental wellness journaling app that listens to your words and reads between the lines.

**Live app → [mindease-app-sable.vercel.app](https://mindease-app-sable.vercel.app)**  
**Demo → [Watch on Loom](https://www.loom.com/share/d780f2e825044ca08af905b2a4e70023)**

---

## What is MindEase?

Most journaling apps store your thoughts. MindEase *listens* to them.

It detects the gap between how you say you feel and how you actually write. It offers a companion that gives no advice, just company. It speaks Urdu. And it keeps your data entirely your own.

---

## Features

### 📖 Journaling
- Poetic mood selector — *Luminous, Weightless, Still, Clouded, Restless*
- Stress slider (before and after journaling) to track how writing affects you
- Voice dictation with a **transcription review step** — fix errors before saving
- Bilingual support — write in English, اردو, or both

### 🧠 AI Analysis
- **"You Felt vs We Sensed"** — detects the gap between your chosen mood and the emotional tone of your words
- Pattern detection, theme tags, recurring word analysis
- Urdu stress keyword detection — پریشان، اداس، مایوس and more
- Powered by **Groq**

### 💬 Ease — AI Companion
- Warm, conversational AI chat
- No advice. No toxic positivity. Just company.
- Remembers your journal context across the conversation
- Powered by **Groq** with streaming responses

### 📊 Patterns Dashboard
- 30-day mood trend chart
- Entry length over time
- Weekly rhythm heatmap by day of week
- Word cloud of your most-used words
- Stress trigger vocabulary
- Writing style analysis (sentence length changes under stress)

### 🧘 Practices & Games
- 4-7-8 breathing exercise
- Fill the Day: color therapy
- Burst the Stress: pop balloons to release worry
- Constellations Connect
- Gratitude prompts
- Guided meditation

### 📄 Smart PDF Exports
- **English PDF** — clean jsPDF export of all English entries
- **اردو PDF** — RTL layout, Noto Nastaliq Urdu font, fully formatted
- Available from both Journal page and Settings

### ⚙️ Settings
- Dark / candlelight mode toggle
- Daily reminder notifications
- Export journal (English + Urdu separately)
- Delete account with password confirmation

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React + TypeScript + Vite |
| Styling | Tailwind CSS + shadcn/ui |
| Animations | Framer Motion |
| Backend / Auth / DB | Supabase (PostgreSQL + RLS + Edge Functions) |
| AI / LLM | Groq — Llama 3.3 70B Versatile |
| Email | Resend (SMTP) |
| Deployment | Vercel |
| Charts | Recharts |
| PDF | jsPDF + html-to-image |

---

## Architecture

```
src/
├── pages/
│   ├── Journal.tsx        # Main journaling page + voice dictation
│   ├── Dashboard.tsx      # Patterns & mood analytics
│   ├── Practices.tsx      # Wellness games & exercises
│   ├── Settings.tsx       # User preferences & exports
│   └── Auth.tsx           # Login / signup / reset password
├── components/
│   ├── EaseFloating.tsx   # AI companion chat widget
│   └── Layout.tsx         # Navigation wrapper
├── contexts/
│   ├── AuthContext.tsx     # Supabase auth state
│   └── ThemeContext.tsx    # Dark/light mode
└── lib/
    ├── moods.ts           # Mood definitions & sentiment mapping
    └── moodPalette.ts     # Color system

supabase/functions/
├── ease-chat/             # Streaming AI companion (Groq)
├── analyze-entry/         # Mood + stress + pattern analysis (Groq)
├── hum-poem/              # Feeling-to-poem generator (Groq)
├── reframe-thought/       # Cognitive reframing (Groq)
├── writing-prompt/        # Contextual journal prompts (Groq)
└── weekly-patterns/       # Weekly observation summary (Groq)
```

---

## Database Schema

```sql
profiles          -- user display name, theme, notification preferences
journal_entries   -- text, mood, sentiment, stress_level, ai_summary,
                  -- mood_before, mood_after, word_count,
                  -- mood_score, patterns, theme_tags, recurring_words
```

All tables protected with **Row Level Security** — users can only access their own data.

---

## Key Design Decisions

**Why Groq?** Fast inference, generous free tier, OpenAI-compatible API. Llama 3.3 70B handles bilingual (English + Urdu) content naturally.

**Why Supabase Edge Functions?** Keeps API keys server-side. The Groq key never touches the client.

**Why separate Urdu PDF?** jsPDF doesn't support Arabic script rendering. The Urdu export uses an HTML/CSS approach with Google Fonts (Noto Nastaliq Urdu) opened in a print dialog instead.

**Why "You Felt vs We Sensed"?** The emotional gap between what someone *says* they feel and what their writing *reveals* is the core insight of the app — made visible on every journal card.

---

---

## Built by

**Marriyam Andeel** — as part of the [Build Club](https://buildclub.ai) Women in AI Accelerator.

*Every single feature came from a real moment of needing it.*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Marriyam%20Andeel-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/marriyam-andeel/)
---

> *"If you've ever written 'I'm fine' when you weren't — this one's for you."* 🤍
