# 📐 System Architecture Blueprints

**Master Project Blueprints (SSOT) for Sovereign AI & SaaS Ecosystems**

This repository serves as the **Single Source of Truth (SSOT)** for my architectural designs. These blueprints are engineered to be consumed by both human architects and AI agents, ensuring absolute consistency between design and implementation.

> [!IMPORTANT]
> All architectures in this repo follow a strict **$0 initial CapEx** and **Sub-8GB RAM** constraint, proving that enterprise-grade AI can be deployed on standard edge hardware.

---

## 🏗️ Blueprint Catalogue

### 🧠 [Vromlix Prime OS](./ARCH_Vromlix_Prime.md)
*Cognitive Operating System & Multi-Agent Orchestrator*
- **Key Features:** Deterministic MCTS Routing, GraphRAG with 1-Hop Traversal, Active Key Manager.
- **Status:** 🟢 Production
- **Stack:** Python 3.12, sqlite-vec, Gemini 3.0, llama-cpp-python.

### 💼 [NexoContable](./ARCH_NexoContable.md)
*B2B2C Serverless SaaS Platform*
- **Key Features:** Multi-tenant RLS Isolation, Stripe Monetization, 100% Serverless Edge Stack.
- **Status:** 🟢 Completed
- **Stack:** Vue 3, Nuxt 4 (Nitro), Supabase, Cloudflare Pages/R2.

---

## 🛠️ The "Blueprint" Philosophy
These files (in Markdown and PDF) contain:
1. **Business Logic:** Core value proposition and target audience.
2. **Developer Constraints:** Hardware ceilings and API rate limits.
3. **Tech Stack Justification:** Why specific tools were chosen over popular alternatives.
4. **Agent Workflow Protocols:** Specific instructions for AI agents during development.
5. **Development Roadmap:** Trackable phases of evolution.

---

*Designed for rigorous execution and deterministic results.*
