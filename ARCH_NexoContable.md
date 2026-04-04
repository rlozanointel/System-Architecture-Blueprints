---
aliases:
  - NexoContable Blueprint
  - Virtual Tax Clinic
tags:
  - "#Blueprint"
  - "#SaaS"
  - "#Vue3"
  - "#Supabase"
estado: 🟢 Completado
fecha_actualizacion: 2026-03-18
descripción: "Plano arquitectónico maestro (SSOT) para el desarrollo del SaaS NexoContable. Consumible por LLMs."
---

# 🏗️ MASTER PROJECT BLUEPRINT: "NexoContable"

## 1. Project Overview & Business Logic
* **Project Name:** NexoContable
* **Type:** B2B/B2C SaaS (Software as a Service)
* **Core Value Proposition:** A "Virtual Tax Clinic" connecting independent workers/freelancers (e.g., Uber drivers) with certified accountants. It eliminates tax anxiety for the client and streamlines document management for the accountant.
* **Target Audience:**
	* **Clients (Mobile-First):** Non-technical users who want a simple, anxiety-free interface to check their tax status and upload receipts.
	* **Accountants (Desktop-First):** Professionals (starting with the founder's partner, an ex-SAT employee) who need a CRM/Dashboard to manage multiple clients, review PDFs, and update tax statuses.

---

## 2. Strict Developer Constraints (Critical)
> [!danger] Reglas de Entorno
> The LLM must strictly adhere to these constraints when suggesting code, architectures, or tools.
> * **Budget:** $0.00 initial budget. Absolutely no paid services, hidden fees, or credit card requirements for the MVP.
> * **Hardware:** The developer operates on an Ubuntu machine with exactly **8GB of RAM**.
> * **Development Environment:** [[Antigravity|Google_Antigravity]] (Agentic IDE).
> * *Rule:* Do not suggest running heavy local LLMs (like Ollama/Qwen) as they will crash the 8GB RAM machine.
> * *Rule:* Do not suggest Firebase Studio (Project IDX) due to the "Blaze Trap" (forced billing for backend functions).
> * **Time:** The developer is a solo "indie hacker" dedicating 1 hour per day. Code generation must rely heavily on AI agents.

---

## 3. Definitive Tech Stack & Architecture
> [!info] Justificación Arquitectónica
> This stack was chosen after deep research to avoid vendor lock-in, commercial restrictions, and RAM overload. Do NOT suggest alternatives like React, Next.js, Vercel, or Firebase.

* **Frontend Framework:** [[Vue_3]] + [[Nuxt_4]] (Configured strictly as a Single Page Application - SPA). Chosen for lightweight mobile performance.
* **UI Library:** Nuxt UI v4 + Tailwind CSS.
* **Hosting:** [[Cloudflare_Pages]] (Chosen for unlimited free bandwidth and DDoS protection. *Vercel is strictly banned* due to commercial use restrictions on their free tier).
* **Database & Authentication:** [[Supabase]] (PostgreSQL).
	* *Justification:* Requires strict multi-tenant data isolation. Supabase's Row Level Security (RLS) is mandatory to ensure clients cannot see each other's data.
* **Storage (Receipts/PDFs):** Cloudflare R2 (10GB free tier, zero egress fees).
* **OCR / Data Extraction (Future):** Google Cloud Vision API (1,000 free scans/month) with a local fallback to `Tesseract.js`.
* **AI Chat / Backend Queue (Future):** Groq API (Llama 3) for fast/free inference, Upstash Redis, Koyeb, and Cloudflare Workers.

---

## 4. Current Project State (What is already built)
The project has been initialized locally in the `NexoContable` directory. The static UI (Frontend) for the MVP is complete. No database is connected yet.

**Routing Setup (`app.vue`):** Refactored to use `<NuxtPage />` to enable Nuxt routing.

**Route 1: Client Dashboard (`pages/index.vue`)**
* **Design:** Mobile-First, minimalist.
* **Components:** Header, Central Card ("Semáforo Fiscal"), FAB (Upload documents), Chat Preview.

**Route 2: Accountant Dashboard (`pages/contador.vue`)**
* **Design:** Desktop-First, Split-screen layout.
* **Components:** Sidebar ("Mis Clientes"), Main Area (Traffic Light Controls, The Vault Document Table, Notes/Chat Box).

---

## 5. AI Agent Workflow Protocol
When the developer requests code generation via [[Antigravity|Google_Antigravity]], the LLM must follow these model-selection rules:
* **For Complex Tasks:** Use `gemini 3.1 pro high` in **Planning Mode**. The agent must write a plan, execute terminal commands, and verify via internal browser screenshots.
* **For Simple Tasks:** Use `gemini 3 flash` in **Fast Mode** to conserve weekly API quotas.
* **Context Awareness:** The LLM must read the local file system to understand the context. Do not rely on chat history.

---

## 6. Development Roadmap (Completed)
- [x] **Phase 1: Validation** - Static UI built.
- [x] **Phase 2: Authentication & Database**
	- [x] Integrate Supabase into the Nuxt 4 SPA.
	- [x] Create PostgreSQL tables: `Users` and `Assignments`.
	- [x] Implement Google OAuth / Email Login.
	- [x] Implement Row Level Security (RLS).
- [x] **Phase 3: State Management & Storage Vault**
	- [x] Connect the "Semáforo" buttons in `/contador` to update the database.
	- [x] Integrate Cloudflare R2 (or Supabase Storage).
- [x] **Phase 4: Internal Chat System**
	- [x] Implement 1-on-1 real-time chat using Supabase Realtime.
	- [x] Set up transactional emails (e.g., Resend).
- [x] **Phase 5: Refinement, Monetization & Launch**
	- [x] **Monetization:** Integrate Stripe Checkout for monthly subscriptions.
	- [x] **UX Polish (Stripe):** Handle the success redirect (`?pago=exito`).
	- [x] **UX Polish (Alerts):** Implement the "Undo Notification Alert" logic.
	- [x] **UI Polish (Responsive):** Fix the accountant sidebar taking up the whole screen on mobile devices.
	- [x] **Production Deployment:** Cloudflare Pages deployment via GitHub CI/CD.

---

## 7. Instructions for the LLM reading this document
1. Acknowledge receipt of this blueprint.
2. Adopt the persona of a Senior Software Architect and Expert Vue 3 / Nuxt 4 Developer.
3. Never suggest paid tools or heavy local processing.
4. When asked for the next step, immediately reference the current active phase and provide the exact terminal commands and code snippets needed.
5. Keep responses highly technical, concise, and formatted in Markdown.