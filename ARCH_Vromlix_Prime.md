---
aliases:
  - Vromlix Prime Blueprint
  - Cognitive Edge Architecture
tags:
  - "#Blueprint"
  - "#AI_Orchestration"
  - "#Python"
  - "#GraphRAG"
estado: 🟢 Producción
fecha_actualizacion: 2026-03-18
descripción: "Plano arquitectónico maestro (SSOT) para el sistema operativo cognitivo Vromlix Prime."
---

# 🏗️ MASTER PROJECT BLUEPRINT: "Vromlix Prime OS"

## 1. Project Overview & Business Logic
* **Project Name:** Vromlix Prime (v6.1.1 Genesis)
* **Type:** Cognitive Operating System / Multi-Agent Orchestrator
* **Core Value Proposition:** A deterministic, local-first AI orchestrator that bridges the gap between industrial process rigor ([[ISO_9001]], [[Six_Sigma_DMAIC]]) and probabilistic Large Language Models. It eliminates LLM hallucinations, automates OSINT data pipelines, and manages complex code refactoring through a highly secure, mathematically verifiable architecture.
* **Target Audience:**
	* **Internal Use:** Personal Knowledge Graph management, automated job hunting (Fábrica de Empleo), and continuous codebase refactoring.
	* **Enterprise Application:** A blueprint for startups needing $0 CapEx, high-throughput AI orchestration without relying on expensive, bloated frameworks like LangChain or LlamaIndex.

---

## 2. Strict Developer Constraints (Critical)
> [!danger] Reglas de Entorno
> The architecture must strictly adhere to these constraints to ensure sovereign execution.
> * **Hardware Ceiling:** The system operates on an Ubuntu machine with exactly **8GB of RAM**. Out-Of-Memory (OOM) errors are unacceptable.
> * **API Rate Limits:** The system relies on free-tier API quotas (e.g., Gemini 3.0 Flash/Pro with 30k TPM / 15 RPM limits). The architecture must natively absorb and bypass `429 Resource Exhausted` errors.
> * **Security (HitL):** The AI has zero direct write access to the host OS. All file system mutations must pass through a Human-in-the-Loop (HitL) Sandbox Firewall.
> * **Dependency Minimalism:** Avoid heavy JVM-based graph databases (Neo4j) or bloated Python wrappers. Rely on native Python, `sqlite-vec`, and `pydantic`.

---

## 3. Definitive Tech Stack & Architecture
> [!info] Justificación Arquitectónica
> This stack prioritizes edge execution, deterministic routing, and zero-latency memory retrieval.

* **Core Engine:** [[Python]].
* **LLM Orchestration:** `google-genai` SDK (Gemini 3.0 Flash for routing/ETL; Gemini 3.0 Pro for deep reasoning).
* **Edge AI (Local Inference):** `llama-cpp-python` running Microsoft Phi-4.
	* *Optimization:* 8-bit Key-Value (KV) Cache quantization to fit within the 8GB RAM constraint.
* **Vector Database & Memory:** [[SQLite-vec]] (C++ WASM extension for SQLite).
	* *Justification:* Provides ultra-fast, serverless 768-dimensional vector search directly at the edge.
* **Data Validation & Routing:** `pydantic`.
	* *Justification:* Enforces strict JSON schemas for Monte Carlo Tree Search (MCTS) routing, preventing LLM output parsing failures.
* **Headless Proxy:** `FastAPI` + `uvicorn`.
	* *Justification:* Allows Vromlix to act as a mock OpenAI endpoint for automated benchmarking (SWE-bench, GAIA).

---

## 4. Core System Topology (The Anatomy)
Vromlix is not a single script; it is a decoupled ecosystem of specialized modules.

### A. The Kernel (`core_vromlix_prime.py`)
The central event loop and Terminal UI. It manages the Short-Term Memory (Session Tracker), intercepts user inputs, and orchestrates the parallel execution of the Agentic Swarm using Python `concurrent.futures.ThreadPoolExecutor`.

### B. The Nervous System (`vromlix_utils.py`)
The centralized orchestrator for environment detection (Colab vs. Local Ubuntu) and I/O management.
* **Active Key Manager:** A custom Round-Robin load balancer that tracks timestamp usage across 100+ API keys, enforcing a strict 61-second cooldown to bypass rate limits.
* **OSINT Grounder:** Map-Reduce pipelines utilizing `feedparser` and `requests` to extract real-time Google News RSS feeds, bypassing IP blocks.

### C. The Memory Center (`auto_indexador.py` & `sqlite-vec`)
* **Tool Knowledge Indexer (TKI):** Scans the local codebase, extracts metadata, and uses Gemini to auto-generate JSON descriptions of all scripts.
* **GraphRAG (1-Hop Traversal):** Upgrades standard flat RAG by using SQLite Recursive CTEs to pull not just the semantic match, but its adjacent contextual nodes, structured under a W-B-O-S (World, Biographical, Opinion, Summary) taxonomy.

### D. The Brain (`02_MoE_Routing.json` & `05_Orchestrator_Prompts.xml`)
* **Mixture of Experts (MoE):** A JSON registry defining 30+ specialized agents (e.g., `AUDIT_CODE_SECURITY`, `OPTIMIZE_CAREER_ATS`).
* **MCTS Router:** Uses Pydantic to mathematically simulate and score multiple Directed Acyclic Graph (DAG) execution paths before delegating tasks to the experts.

### E. The Immune System (`core_maker_checker_agent.py`)
* **Dual-LLM Adversarial Auditing:** A "Surgeon" agent generates code mutations, which are then mathematically verified by an isolated "Forensic Auditor" agent.
* **HitL Sandbox Firewall:** Intercepts all OS-level commands (create, move, delete) and surgical diff patches, requiring explicit `[Y/n]` terminal authorization.

---

## 5. AI Agent Workflow Protocol
1. **Ingestion & Grounding:** User input is received. The system queries `sqlite-vec` (Deep Memory) and executes OSINT RSS searches (Web Grounding) if real-time data is required.
2. **MCTS Routing:** The Router simulates execution paths and outputs a strict Pydantic JSON DAG (e.g., Step 1: Extract Data -> Step 2: Write Code -> Step 3: Audit).
3. **Parallel Swarm Execution:** Experts execute their tasks in parallel or sequentially based on the DAG dependencies. If an expert has the `LOCAL_` prefix, the task is routed to `llama.cpp` (Phi-4) instead of the cloud API.
4. **Ockham Synthesis:** The `OckhamSynthesizer` fuses the multiple expert outputs into a single, high-density response, stripping out conversational fluff and enforcing the "Iron Truth" axiom.
5. **Firewall & Output:** The HitL Firewall scans the final output for OS commands. If safe, the response is printed, and the `RealTimeVectorizer` asynchronously saves the interaction to the SQLite database.

---

## 6. Development Roadmap
- [x] **Phase 1: Core Infrastructure** - MoE Routing, SQLite-vec integration, Active Key Manager.
- [x] **Phase 2: Edge Compute Integration** - `llama.cpp` integration for offline inference within 8GB RAM limits.
- [x] **Phase 3: Headless Benchmarking** - FastAPI proxy deployment for SWE-bench integration.
- [ ] **Phase 4: Advanced Memory Consolidation (CURRENT)**
	- Implement RAPTOR (Recursive Abstractive Processing for Tree-Organized Retrieval) using UMAP and Gaussian Mixture Models (GMM) to cluster and summarize low-level memory nodes into high-level concepts.
- [ ] **Phase 5: Autonomous Web Interaction (FUTURE)**
	- Integrate Project Mariner / Playwright for autonomous, multi-step browser navigation and DOM interaction, bypassing the need for static Selenium scripts.