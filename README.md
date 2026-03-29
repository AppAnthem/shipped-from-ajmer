# Shipped from Ajmer

> Two production products. One solo builder. Built from Ajmer, Rajasthan.

I'm **Himanshu Dadhich**.

I was born in Ajmer, Rajasthan. Did my schooling here. Walked these streets before I ever wrote a line of code. Then life took me to Bangalore — 15 years in Data Analytics, building at GE and Cytiva, managing teams, solving enterprise-scale problems. I had the career. I had the city everyone moves to. 4 years ago, I moved back to Ajmer — still with Cytiva, working remotely. But last year, the builder in me woke up. I wanted to create something of my own. AjmerAstro carries this city's name because this platform was imagined here, built here, and shipped from here. Proof that the next wave of builders isn't just coming from metros — it's coming from everywhere. All you need is conviction, a laptop, and Claude.

These aren't side projects or weekend experiments. These are **production-grade platforms** — architected, secured, tested, and shipped.

---

## AjmerAstro — India's Most Complete Astrology Platform

**Live:** [ajmerastro.com](https://ajmerastro.com)

A full-scale astrology platform covering **Vedic, KP (Krishnamurti Paddhati), and Western** astrology systems — with real astronomical calculations powered by Swiss Ephemeris.

### What it does

- **Vedic Kundali Engine** — All divisional charts (D1–D60), Vimshottari Dasha (3-level), Ashtakvarga, Shadbala, Bhava Chalit
- **KP Astrology** — 249 sub-lord system, horary number support, cuspal significator analysis
- **Western Astrology** — Tropical zodiac, Placidus houses, aspect calculations, element/modality balance
- **Kundali Matching** — Ashtakoot 36-point Gun Milan + Manglik/Nadi Dosha detection
- **Dosha Detection** — 8 doshas (Kala Sarpa, Manglik, Nadi, Pitra, Bhakoot, Guna, Var, Tara)
- **Yoga Detection** — 16+ yogas (Pancha Mahapurusha, Gajakesari, Budhaditya, Lakshmi, Dhana, and more)
- **Panchang** — Daily Tithi, Nakshatra, Yoga, Karana, Rahu Kaal, Choghadiya
- **14 Free Calculators** — Sade Sati, Moon Sign, Numerology, Gemstone Recommendation, and more
- **Shri Ram Shalaka Prashnavali** — 15×15 interactive divination grid
- **1,667+ SEO Pages** — Programmatically generated (27 Nakshatras, 144 zodiac pairs, 31 blogs, 35 festivals)

### Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Next.js 16 (App Router), React 19, TypeScript, Tailwind CSS v4, shadcn/ui |
| Astro Engine | Python FastAPI + Swiss Ephemeris (pyswisseph) — 11 calculation services, ~3,870 lines |
| Database | Supabase (PostgreSQL) — 17 migrations, 15 RLS policies |
| Auth | Supabase Auth (Email + Phone + Google + Apple) |
| Caching | Upstash Redis (serverless) |
| Security | Arcjet (rate limiting + bot detection + WAF), Cloudflare Turnstile, Zod validation, 7 security headers (CSP, HSTS, etc.) |
| Monitoring | Sentry (error tracking), PostHog (product analytics), GA4 |
| Testing | Playwright — 52 E2E tests + 76 security tests |
| Deployment | Vercel (frontend) + Render (astro-engine) |

### Architecture

```
User Browser
    │
    ▼
Next.js 16 App (Vercel)
    ├── Server Components (SEO + SSR)
    ├── Client Components (Interactivity)
    ├── API Routes (4 endpoints)
    │   ├── /api/calculate → Astro Engine
    │   ├── /api/horoscope
    │   ├── /api/contact (RLS protected)
    │   └── /api/newsletter
    │
    ▼
Python FastAPI Astro Engine (Render)
    ├── /api/v1/kundali    — Vedic birth charts
    ├── /api/v1/kp         — KP astrology
    ├── /api/v1/western    — Tropical zodiac
    ├── /api/v1/compatibility — Ashtakoot matching
    ├── /api/v1/panchanga  — Daily almanac
    └── /api/v1/transit    — Real-time positions
    │
    ▼
Swiss Ephemeris (pyswisseph)
    └── Real astronomical calculations
```

### Security Posture

- Row-Level Security (15 policies) on all user-facing tables
- Rate limiting on every API endpoint (Arcjet)
- CAPTCHA on public forms (Cloudflare Turnstile)
- Input validation with Zod schemas
- Security headers: CSP, HSTS (2yr + preload), X-Frame-Options, Permissions-Policy
- Error message sanitization — no stack traces leak to users
- 76 security tests covering XSS, SQLi, auth bypass, header validation

### What's Next

- AI-powered Kundli interpretation (Claude API integration)
- Astrologer consultation marketplace (chat, audio, video)
- E-commerce (gemstones, rudraksha, pooja booking)
- PDF report generation (15+ report types)
- Multi-language support (12+ languages)

### How AjmerAstro is Different

Standing on the shoulders of platforms like AstroSage and AstroTalk, AjmerAstro brings a modern, AI-native approach to an industry running on legacy technology.

- **Triple astrology system** — Vedic + KP + Western in one platform
- **Own Astro Engine, not API wrappers** — Unlike most astrology apps that depend on third-party APIs (like Prokerala, Veda API) for calculations, AjmerAstro runs its own Python FastAPI engine powered by Swiss Ephemeris. Zero dependency on external API costs — a massive cost advantage at scale
- **API-as-a-Service on the roadmap** — Since the core astro-engine is built in-house, the plan is to offer it as a standalone Astrology API service for other developers and platforms — similar to what Prokerala offers, but with KP + Western support on top of Vedic
- **Enterprise-grade security** — RLS, rate limiting, penetration-tested, 76 security tests. Astrology apps rarely take security this seriously
- **AI-native architecture** — Built ground-up for Claude API integration, not AI bolted onto legacy code
- **Modern stack** — Next.js 16, React 19, Tailwind v4, Supabase — while competitors run on decade-old codebases

---

## ZettlAI — AI Meeting Notes That Actually Work

**Status:** Stealth Mode

An AI-powered meeting notes platform currently in stealth. Paste a Google Meet link, a bot joins your call, records, transcribes with Whisper, and generates structured notes with Claude.

### What it does

- **Automated Bot** — Puppeteer-based bot joins Google Meet as a participant
- **Live Transcription** — OpenAI Whisper for accurate speech-to-text
- **AI-Generated Notes** — Claude API produces structured notes: executive summary, decisions, action items, blockers, follow-ups
- **BYOK Model** — Users can bring their own API keys (Starter/Privacy plans) — near-zero API cost for us
- **Privacy-First Plan** — Zero data storage option for enterprises — transcript + notes deleted after download
- **Hindi Support** — Full Devanagari output for Pro users
- **White Label** — Custom branding for hospitals, law firms, corporates
- **Team Workspaces** — Shared meeting history, admin dashboard, seat management

### Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Next.js 14 (App Router), TypeScript, Tailwind CSS |
| Bot Server | Node.js + Express + Puppeteer + puppeteer-stream |
| Transcription | OpenAI Whisper API |
| AI Notes | Anthropic Claude API |
| Real-time | WebSockets (live status updates) |
| Database | Supabase (PostgreSQL + Auth + Storage) |
| Payments | Razorpay (UPI, cards, subscriptions) |
| Email | Resend + React Email |
| Deployment | DigitalOcean VPS + PM2 + Nginx |
| Testing | Playwright E2E |

### Architecture

```
User Browser
    │
    ▼
Next.js App (port 3000)
    │  POST /api/bot/start
    ▼
Bot Server (port 3001) ◄──── WebSocket ────► Browser (live status)
    │
    ├── Puppeteer joins Google Meet
    ├── Records audio → /tmp/recordings/
    ├── OpenAI Whisper → transcript
    ├── Claude API → structured notes (JSON)
    └── Updates Supabase → user views notes
```

### Business Model

| Plan | Price | Highlights |
|------|-------|-----------|
| Free | ₹0 | 2 meetings/month, 15 min max |
| Starter | ₹499/mo | 10 meetings, BYOK |
| Pro | ₹2,499/mo | 30 meetings, managed keys, Hindi |
| Privacy | ₹2,999/mo | Zero storage, enterprise compliance |
| Team | ₹7,999/mo | 5 seats, shared workspace |
| White Label | ₹15K–35K/mo | Custom branding, dedicated support |

### What's Next

- MS Teams support
- Zoom support

---

## Why This Matters

Both products are **vibe-coded and solo-built** from Ajmer — no team, no funding, no Bangalore bubble.

What I bring to the table:
- **15+ years** in Data Analytics and enterprise tech (GE/Cytiva)
- **Full-stack execution** — frontend, backend, Python microservices, database design, security, DevOps
- **Enterprise-grade habits** — RLS, rate limiting, E2E testing, error monitoring, security headers
- **Real products** — not tutorials, not clones, not demos

---

## Connect

- **LinkedIn:** [linkedin.com/in/himanshudadhich](https://www.linkedin.com/in/himanshudadhich/)
- **AjmerAstro:** [ajmerastro.com](https://ajmerastro.com)
