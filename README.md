# 💻 Eric Gabriel Manabat
### Full-Stack AI Engineer

📍 Metro Manila, Philippines • **B.S. Information Technology (PLV, 1.03 Running GWA)** • **CTF Silver Medalist**

<p align="left">
  <a href="https://ericmanabat.is-a.dev/" target="_blank"><img src="https://img.shields.io/badge/Portfolio-ericmanabat.is--a.dev-8A1BE0?style=flat-square&logo=google-chrome&logoColor=white" alt="Portfolio" /></a>
  <a href="mailto:eric.manabatseam@gmail.com" target="_blank"><img src="https://img.shields.io/badge/Email-eric.manabatseam%40gmail.com-ea4335?style=flat-square&logo=gmail&logoColor=white" alt="Email" /></a>
  <a href="https://www.linkedin.com/in/eric-gabriel-manabat-554697204/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-Eric_Manabat-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="https://github.com/PSergio984" target="_blank"><img src="https://img.shields.io/badge/GitHub-PSergio984-181717?style=flat-square&logo=github&logoColor=white" alt="GitHub" /></a>
  <a href="https://ctf.hackthebox.com/user/profile/1014955" target="_blank"><img src="https://img.shields.io/badge/HackTheBox-Profile-9fef00?style=flat-square&logo=hackthebox&logoColor=black" alt="HackTheBox" /></a>
  <a href="https://tryhackme.com/p/eric.manabatseam" target="_blank"><img src="https://img.shields.io/badge/TryHackMe-Profile-3399FF?style=flat-square&logo=tryhackme&logoColor=white" alt="TryHackMe" /></a>
  <a href="https://www.leetcode.com/psergio984" target="_blank"><img src="https://img.shields.io/badge/LeetCode-psergio984-FFA116?style=flat-square&logo=leetcode&logoColor=black" alt="LeetCode" /></a>
</p>

---

## ⚡ About Me

I build full-stack systems and production AI architectures with strict security-first engineering. My focus centers on bounded agentic systems, hybrid neural retrieval (BM25 + Dense RRF), and resilient edge IoT computer vision, engineered with defensive AppSec principles (RBAC, PII redaction, Row-Level Security).

- 🎓 **Academic Standing**: Senior B.S. Information Technology student at Pamantasan ng Lungsod ng Valenzuela (PLV) — **1.03 Running GWA**, Consistent Dean's Lister.
- 🛡️ **Defensive Mindset**: Hands-on competitive CTF player (HTB, PicoCTF, ITlympics) applying threat modeling and vulnerability hunting to audit web services from the outside in.
- 🎨 **Design Rigor**: TESDA Visual Graphics Design NC III certified, bringing high typographic polish and design system consistency to complex data-heavy interfaces.

---

## 💼 Work Experience

### **FlyRank AI** — *Full-Stack AI Engineer Intern*
`JUN 2026 – PRESENT` • *Remote*
- **Retrieval Accuracy**: Architected and deployed an autonomous FastAPI AI sidecar microservice, **increasing Top-1 retrieval accuracy from 81.8% to 86.4%** on ground-truth benchmarks by fusing BM25 (SQLite FTS5) and dense vector search via Reciprocal Rank Fusion (RRF, $k=60$) with deterministic blend reranking.
- **Hallucination Elimination**: Engineered a bounded 3-step agentic query loop with cosine similarity gating ($<0.50$ threshold) and inline numbered citations, achieving a **100% negative query pass rate** and **90% LLM-as-judge relevance score** (`llama-3.3-70b`).
- **Latency & Telemetry**: Reduced time-to-first-token (TTFT) by **~65%** via asynchronous Server-Sent Events (SSE) streaming APIs, backed by Prometheus `/metrics` latency histograms and a 6-chart Dockerized Grafana monitoring dashboard.

### **Nexvision Innovations Inc.** — *Full Stack Software Engineering Intern (Team Lead)*
`JUN 2026 – PRESENT` • *Marikina (Hybrid)*
- **Statutory Compliance**: Ensured **100% DOLE compliance** across 4 enterprise HRIS applications by auditing payroll calculation engines and implementing interval-partitioned time algorithms to isolate 10 PM – 6 AM night differentials from standard overtime multipliers.
- **Automated Payroll**: Automated statutory multi-tier deductions and 13th-month proration across **500+ employee records** using TypeScript/Next.js calculation modules for progressive SSS/WISP, PhilHealth, and Pag-IBIG regular/MP2 brackets with immutable audit trails.
- **Multi-Tenant Security**: Hardened PostgreSQL and Supabase data layers against cross-branch data leaks by enforcing strict branch-scoped row-level security (RLS) query constraints.
- **CI/CD Acceleration**: Cut runner execution times by **40% (~12m down to ~7m)** in GitHub Actions and Jenkins by architecting an offline mock testing daemon that eliminated flaky external DNS timeouts.
- **Sprint Leadership**: Led sprint execution and technical code reviews across **180+ Jira/GitHub issues** as Intern Team Lead, enforcing TypeScript type safety and clean architecture standards.

---

## 🚀 Flagship Systems & Deep Technical Challenges

### 1. [PLV eLib — CEIT Library System + AI Sidecar](https://github.com/PSergio984/CEIT-Library)
*Decoupled Dual-Engine Architecture: Core Web Monolith + Autonomous FastAPI AI Sidecar*
- **The Challenge**: The university library required fast, reliable catalog search and automated Q&A over institutional research docs without vendor lock-in, hallucinations, or crashing the primary web server.
- **Architecture & Engineering**:
  - Decoupled a Laravel 11 monolith (PHP 8.4, PostgreSQL, Livewire 3, MaryUI, QR borrowing) from an external FastAPI AI Sidecar ([`PSergio984/ceit-ai-sidecar`](https://github.com/PSergio984/ceit-ai-sidecar)).
  - Implemented hybrid neural retrieval fusing SQLite FTS5 (BM25) with `all-MiniLM-L6-v2` dense embeddings using Reciprocal Rank Fusion (RRF, $k=60$), lifting retrieval from 81.8% to 86.4% Top-1.
  - Bounded agentic loop with cosine similarity gating ($<0.50$) that forces deterministic refusal on zero context, completely eliminating out-of-domain hallucinations.
- **Verification & Telemetry**: 600+ PHPUnit tests, 78 pytest tests, evaluated against a 27-case golden set ($P@5$: 0.45, $R@5$: 0.72, Top-1: 86.36%). Monitored via Prometheus latency histograms and Dockerized Grafana.

### 2. [AGOS — AI-Guided Overflow Surveillance](https://agos-platform.vercel.app/)
*Solar-Powered Edge IoT Flood Surveillance System for Barangay Maysan*
- **The Challenge**: High-resolution flood monitoring in remote, low-bandwidth urban waterways with strict solar battery constraints and severe network dropouts.
- **Architecture & Engineering**:
  - **92% Compute Reduction**: Decoupled a lightweight 15-second camera feed for live human monitoring from a 3-minute server-side YOLOv8 inference cycle, slashing continuous compute demands and preventing thermal throttling on Raspberry Pi Zero 2W.
  - **Sensor & Decision Fusion**: Engineered a composite 0–100 hazard scoring algorithm fusing ultrasonic depth telemetry (JSN-SR04T) with debris detection (YOLOv8) and weather API alerts.
  - **Alert Fatigue Prevention**: Integrated 3-tier hardware LEDs (Safe/Warning/Critical) with SMS/push notification throttling enforcing a strict 30-minute cooldown.
  - **Dataset Engineering**: Curated and annotated 5,000 drainage images on CVAT.ai with OpenCV frame quality pre-filtering.

### Additional Production & Open-Source Systems

| Project | Architecture & Stack | Hard Problem Solved |
| :--- | :--- | :--- |
| **[Task-Buddy](https://task-buddy-frontend.vercel.app/)** | React 19, TypeScript, FastAPI, Supabase, pgvector, Redis, Groq | Hybrid BM25 + Jina v3 vector retrieval with sub-500ms Groq `llama-3.3-70b` planning fallback; historical completion-based effort estimation; real-time WebSockets. |
| **[Survey Portal](https://valenzuela-satisfaction-survey-main-plae88.laravel.cloud/)** | Laravel 12, Inertia.js 2, React 19, Filament 4, PostgreSQL | Recursive `PiiScrubberProcessor` sanitizing sensitive PII from application logs; real-time detractor alerts via synchronous `AnswerObserver`; 146 automated tests with 5,856 assertions. |
| **[CTF Writeups](https://datus-ctf-writeups.vercel.app/)** | Next.js, Markdown, Tailwind CSS | Curated vulnerability analysis and exploitation walkthroughs across HackTheBox, PicoCTF, and web application security labs. |

---

## 🛠️ Technical Stack & Architectural Competencies

- **AI, RAG & Vector Systems**: FastAPI, LangChain, LangGraph, pgvector, Pinecone, ChromaDB, SQLite FTS5 (BM25), Hybrid RRF Search, YOLOv8, OpenCV, Prometheus, Grafana, LLM-as-Judge Evaluation, Server-Sent Events (SSE)
- **Languages**: TypeScript, JavaScript (ES6+), Python, PHP (8.4), C# / .NET, Java, SQL
- **Frontend & UI**: Next.js (App Router), React 19, Tailwind CSS v4, shadcn/ui, MaryUI, Filament 4, Livewire 3, Alpine.js, Zustand, Figma
- **Backend & Databases**: FastAPI, Laravel 11/12, Node.js, PostgreSQL, Supabase, Redis, MySQL, MongoDB, SQLite
- **Cloud, DevOps & Tooling**: Docker, Jenkins, GitHub Actions, AWS, Google Cloud (GCP), Vercel, Cloudflare, Render, Railway, Vite, Sentry
- **Defensive Security & AppSec**: Burp Suite, Wireshark, Kali Linux, Role-Based Access Control (RBAC), Row-Level Security (RLS), PII Masking, OWASP Top 10 Auditing

---

## 🏆 Honors & Competitions

- 🥈 **Silver Medal (CTF)** | ITlympics 2026 — *Pamantasan ng Lungsod ng Valenzuela*
- 🥇 **Gold Medal (Quiz Bee)** | ITlympics 2025 — *Pamantasan ng Lungsod ng Valenzuela*
- 🥉 **Bronze Medal** | Gamecon 2026 — *Pamantasan ng Lungsod ng Valenzuela*
- 🎖️ **Representative (Cybersecurity Quiz Bee)** | 14th National IT Olympics — *University of Makati*
