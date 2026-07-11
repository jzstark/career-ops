# Article Digest — Proof Points for Jianxin Zhao

## Core Focus (use this to frame the narrative in evaluations)

**Primary direction:** LLM inference and serving optimization — latency, throughput, cost reduction — targeting cloud and edge/embedded deployment (robots, embedded devices). NOT training. The background in DL compilers, edge AI, distributed systems, and federated learning feeds directly into this.

**Secondary direction:** Agentic AI systems — token cost reduction, efficient tool use, multi-agent coordination. Active research: modifying LibreChat's orchestration layer to reduce token spend in agentic workflows (paper in progress).

**How to use this in evaluations:**
- For inference/serving roles: lead with DL compiler work, edge AI deployment experience, Triton/CUDA skills, and the direction of travel
- For agent roles: lead with Legal AI system (LibreChat + MCP), token cost research, and agentic workflow design
- Acknowledge that current portfolio is research-stage on inference specifically — compensate with depth of adjacent systems work and rapid learning track record
- Never pitch as a training specialist; always reframe past distributed/federated work as "systems thinking that now applies to serving"
- KnowledgeBase-S is a **production LLM application, personally built and deployed** — never frame it as a "personal wiki/side project"

---

## Interview Narrative — "What's your experience with LLMs?" (90-second answer)

Use this framing in Block F interview prep, cover letters, and any narrative output. It is the canonical version — rehearsed, not improvised.

> "My LLM experience runs along two tracks. On the **application side**, I built and deployed an LLM-powered knowledge platform that's in production pilot with a law firm in China — I own the whole stack: a dynamically self-organizing RAG system, agent orchestration with MCP tool use, and domain-specific problems like tracking when legal sources get superseded. Real users, real feedback loops, ongoing iterations. On the **systems side** — which is where my depth is — I work on LLM inference for edge deployment in autonomous driving at KIT. And before the LLM era I spent a decade on the same underlying problems — distributed training, edge deployment, systems optimization — so for me LLMs are a new workload on a stack I know very well."

**Honest-boundary redirect** (when asked about frontier-scale training or high-traffic serving — one honest sentence, immediate pivot, no apology):

> "Not at frontier scale — my training experience is at the fine-tuning and small-model level. Where I go deep is the inference and serving side: memory management, quantization trade-offs, latency under SLA. Happy to go into any of that."

**Hard limits (source-of-truth):** never claim frontier-scale model training, high-traffic production serving, or upstream contributions/projects that don't exist yet. The nano-vLLM engine, Jetson Orin benchmarks, and vLLM PRs are planned work — they must NOT appear in any generated output until real, at which point add them below.

<!-- PLACEHOLDER (activate when real): ## Edge Inference Engine (nano-vLLM) — paged KV cache, continuous batching, W4A16 quantization; Jetson Orin latency measurements; upstream vLLM/SGLang contributions. -->

---

## Systems Architect — Full-Stack ML Stack (Owl)

**The pitch:** In the agentic AI era, the bottleneck is rarely the model — it's the system that orchestrates, serves, and optimizes it. Owl demonstrates the ability to architect a complete ML stack from top to bottom, not just wire together libraries.

**Owl's full vertical stack (top to bottom):**
```
Advanced DNN applications (image segmentation, generation, NLP)
    ↓
Automatic differentiation engine (forward/reverse mode AD)
    ↓
Optimization algorithms (SGD, Adam, L-BFGS, custom optimizers)
    ↓
Linear algebra & statistics (matrix ops, decompositions, distributions)
    ↓
Hardware-aware C kernels (133K OCaml + 103K C — BLAS/LAPACK/OpenCL bindings)
    ↓
Parallel & distributed execution (multi-core, GPU, cloud)
```

**Why this matters for modern AI roles:**
- LLM serving engineers need to understand the full stack to know *where* latency comes from — not just call `vllm.serve()`
- Agentic system designers need to understand memory, batching, and scheduling tradeoffs at the system level
- Most "AI engineers" work at the Python framework layer. Owl demonstrates you can go all the way down to C + hardware properties

**Key metrics:** 236K+ total LoC (133K OCaml + 103K C), 1.3K GitHub stars, adopted by Jane Street, EPSRC-funded (£1.24M). Recognised by the Cambridge University Computer Laboratory as one of the most representative systems developed in its CS department, alongside Xen Hypervisor and EDSAC — source: cl.cam.ac.uk/research/srg/.

**Framing by role:**
- For inference/serving: "I understand the full stack from DNN ops to hardware-level kernel optimization — I know where LLM serving latency actually comes from"
- For agents: "I've architected systems where every abstraction layer was intentional — I bring that discipline to orchestration and tool design"
- For research engineering: "Owl is a research platform — I designed it to be both scientifically rigorous and production-grade"
- For LegalTech / product engineering: "I can architect a full system, not just integrate APIs — the Legal AI system has the same layered design philosophy"

---

## Rapid Learning — 3 Certifications in 2 Months

**Proof point:** AWS Certified Solutions Architect – Professional + AWS Certified AI Practitioner + NVIDIA-Certified Associate: Generative AI LLMs — all acquired within 2 months in mid-2025, while actively publishing research and building the Legal AI system.

**Why it matters:** Solutions Architect Pro is a demanding exam (cloud architecture, networking, security at scale). Passing three certifications simultaneously across two vendors while doing research and product work signals fast, structured ramp-up on new stacks.

**Framing by context:**
- "Picked up the full AWS + NVIDIA GenAI stack and certified in under 2 months alongside active research commitments"
- For roles mentioning AWS: direct stack fit, not just familiarity
- For roles emphasizing adaptability: pairs with the OCaml → Python → CUDA → LLM trajectory across 10 years
- For startup roles: "I learn what I need quickly, and I prove it"

---

## Legal AI / KnowledgeBase-S (2026 – present)

**What it is:** A full Legal AI system for a leading Chinese law firm — not just a knowledge base. Backend (KnowledgeBase-S repo) + LibreChat frontend in a separate repo. Solo-built end-to-end with Claude Code/Codex.

**Tech stack:** Python/FastAPI, PostgreSQL 16 + pgvector (1536-dim embeddings), Docker Compose, Claude Haiku 4.5 (analysis) + Sonnet 4.6 (synthesis/comparison), OpenAI text-embedding-3-small, Next.js.

**Architecture highlights:**
- HyDE query expansion: generates hypothetical document abstract before embedding to improve retrieval relevance
- Hybrid search: `final_score = vector_score + (0.15 if keyword_hit else 0)`
- Multi-stage retrieval: summary-first → entities → articles fallback
- 4-layer knowledge graph: articles, entities, summaries, indexes — connected by typed relations (mentions, similar_to, contains)
- Continuous entity updating: stale abstract detection + async refresh workers
- 7 MCP tools: search, fetch, related, timeline, compare, cite, summarize_corpus
- Document taxonomy: regulation / case / news / memo / contract / analysis

**Sell angles by job type:**
- **RAG Engineer:** HyDE expansion, hybrid vector+keyword scoring, multi-stage retrieval pipeline, pgvector at scale
- **Knowledge Base / Enterprise AI:** 4-layer graph model, entity disambiguation, cross-reference discovery, regulatory taxonomy
- **Client-facing product:** LibreChat frontend, production Docker deployment, real law firm users, feedback-driven iteration
- **Legal AI / RegTech:** regulation/case/contract taxonomy, citation verification, entity extraction for legal domains; published book on AI regulation landscape (Wiley, 2026) — covers EU liability frameworks, GDPR intersection, UNECE WP.29
- **Agentic coding / AI-assisted dev:** 14K+ LoC built solo with Claude Code/Codex through multiple refactor rounds, MCP server design
- **LLM Platform / Infrastructure:** MCP server with 7 tools, stable public API vs internal API separation, async worker architecture

**Scale:** 14,000+ lines of code; active production use; multiple refactor rounds.

---

## OWL: OCaml Scientific and Engineering Computing (2016 – present)

**What it is:** NumPy + SciPy + PyTorch for OCaml. The definitive scientific computing library in the OCaml ecosystem.

**Key metrics:**
- 1,300+ GitHub stars (one of the most starred OCaml repos)
- 230,000+ lines of code
- Adopted by Jane Street and other leading companies
- Ranks alongside Xen Hypervisor and EDSAC as a representative Cambridge CS system

**Technical highlights:** Algorithmic differentiation, distributed/parallel computing, GPU acceleration, DNN support, full ML pipeline from data to deployment.

**Sell angles:**
- Open-source leadership and community building
- Systems programming and compiler-level ML optimization
- Functional programming applied to ML/AI platforms
- Long-term technical vision and execution (10 years)

---

## EU CulturalRoad — Horizon Europe (2024 – present)

**Budget:** €1.9 million  
**Scope:** 5 European demo sites including Karlsruhe; academic + industry consortium  
**My role:** AI-based multi-agent modeling and coordination for CCAM services  
**Publications:** IEEE TITS 2026 systematic review on vehicular collaborative perception (27.1, pp. 81–118)

---

## National Key R&D Program — Industrial IoT Big Data Lake (2021–2023)

**Budget:** €460,000 (Chinese national program)  
**My role:** Technical Lead  
**What we built:** Cloud–edge knowledge transfer system for heterogeneous industrial big data  
**Hardware:** 20+ GPU on-premise cluster, K8s orchestration  
**Result:** +3% accuracy vs manual inspection across 5+ defect categories in textile manufacturing  
**Deployment:** National big data center (edge gateways + data lake), partnered with leading textile manufacturer

---

## Books (4 published / forthcoming)

| Title | Publisher | Date |
|-------|-----------|------|
| Autonomous Driving: Technical, Business and Regulatory Landscape | Wiley | Jul 2026 |
| Strategic Blueprint for Enterprise Analytics | Wiley | Jul 2026 |
| Architecture of Advanced Numerical Analysis Systems | Apress | Dec 2022 |
| Functional Programming in Data Science and AI | Springer (Undergrad Topics in CS) | Apr 2022 |

### Autonomous Driving Book — Framing by Role Type

The book is structured in two parts: **Technology** (Ch 1–7) and **Business and Regulation** (Ch 8–14). The technical half is rich enough to serve multiple distinct framing angles beyond the regulatory one. Use the table below to select the right angle at evaluation time.

| Role type | Lead chapter(s) | Key angle |
|-----------|----------------|-----------|
| Automotive semiconductor / ML compiler (e.g. NXP, Qualcomm, ARM) | Ch 4 + Ch 5 | E/E architecture evolution, computation hardware landscape, AUTOSAR middleware — understands the deployment context for the chips and compiler targets |
| Automotive ADAS / perception / AD research (e.g. Waymo, Mobileye) | Ch 2 + Ch 3 + Ch 7 | Full algorithm coverage: localization, SLAM, object tracking, motion planning, end-to-end AD; collaborative perception and V2X system architecture |
| Safety-critical embedded / functional safety | Ch 4.4 + Ch 14 | Hardware for safety (Safety CPU, Hardware Safety Manager, external MCUs), ISO 26262 ASIL product development, SOTIF — published familiarity with automotive safety standards |
| Legal AI / RegTech / Compliance AI | Ch 14 | Functional safety (ISO 26262), SOTIF, EU type-approval, GDPR intersection — regulatory depth validated by BMW foreword |
| Autonomous driving startup / business roles | Ch 9 + Ch 11 | Value chain (domain controllers, sensors, component providers), commercialization tarpit, ADAS company landscape |

---

**Ch 4 — Hardware Platform (pp. 87–107): the automotive silicon angle**

Covers: brief history of automotive chips (§4.1), E/E architecture evolution (§4.2), computation hardware overview (§4.3), hardware for safety — Safety CPU, Information Safety, Hardware Safety Manager, external MCUs (§4.4), Snapdragon computation platforms (§4.5), communication hardware — bus systems, Automotive Ethernet, PCIe (§4.6).

**Why it matters for compiler/semiconductor roles (NXP, Qualcomm, ARM, Mobileye):**
- E/E architecture evolution (§4.2) is the macro trend NXP is betting on: the shift from distributed ECU-based architectures to centralized/zonal compute. A compiler engineer who understands *why* this is happening can reason about which NPU targets actually matter and how compilation strategies should evolve.
- §4.4 covers safety CPU and Hardware Safety Manager concepts — NXP's ASIL-certified chips are exactly this category. Shows familiarity with the hardware constraints the compiler must respect (real-time, safety partitioning, lockstep CPU modes).
- §4.6 communication hardware (CAN, Automotive Ethernet, PCIe) — the inter-chip fabric that compiled model outputs traverse. Understanding bus latency constraints informs compilation trade-offs.

**Frame as:** "My Wiley book includes a dedicated chapter on automotive hardware platforms and E/E architecture evolution — I understand the silicon landscape and deployment context for the compiler targets I'd be working with."

---

**Ch 5 — Software Platform (pp. 109–131): the AUTOSAR / OS angle**

Covers: software architecture overview (§5.1), hypervisor (§5.2), AUTOSAR Classic and Adaptive AUTOSAR (§5.3 — including SWC development process), OS Core — QNX as guest OS, vendor-specific tools (§5.4), functional and application software layers (§5.5–5.6), vehicle-cloud synergy (§5.7), case study: evolution of Baidu Apollo (§5.8).

**Why it matters:**
- AUTOSAR Classic and Adaptive (§5.3) is the middleware stack on which automotive software components (SWCs) run — including ML inference components that MLIR/IREE compiled models get packaged into. A compiler engineer who understands the AUTOSAR SWC development process knows what constraints the binary output must satisfy.
- Hypervisor (§5.2) and QNX (§5.4.2) — the runtime environment for safety-critical automotive compute. Published familiarity signals awareness of the OS-level constraints RTOS imposes on compiled code (real-time scheduling, memory isolation, deterministic execution).
- Adaptive AUTOSAR (§5.3.3) is the modern interface for ADAS domain controllers — precisely where NXP's S32G processor family targets.

**Frame as:** "I've written about AUTOSAR and automotive OS architecture — I understand the runtime environment that MLIR-compiled inference components are deployed into, which directly shapes compilation optimization priorities."

---

**Ch 7 — V2X: Cooperative Driving (pp. 161–177): the CCAM / V2X angle**

Covers: DSRC and C-V2X (§7.1), application scenarios including vehicle-infrastructure-cloud integration (§7.2), global V2X regulatory efforts across US/EU/South Korea/China (§7.3), collaborative perception — system architecture, information fusion strategies, datasets and benchmarks (§7.4).

**Why it matters:** Directly overlaps with Jianxin's CulturalRoad EU Horizon program work and IEEE TITS 2026 systematic review. The book's V2X chapter and the research publications are mutually reinforcing — the book provides the system-level and regulatory framing; the papers provide the research depth. Use this when applying to V2X, CCAM, or connected vehicles roles.

**Frame as:** "My published book chapter on V2X and collaborative perception complements my research publications — the IEEE TITS systematic review covers the technical depth, the book frames the ecosystem and regulatory context."

---

**Ch 14 — Safety Standards and Regulations (pp. 307–328): the functional safety angle**

Covers: functional safety — concept phase, product development, ISO 26262 components (§14.1), Safety of the Intended Functionality — SOTIF (§14.2), information safety (§14.3).

**Why it matters for compiler/embedded roles:** ISO 26262 ASIL requirements directly constrain compiler output for safety-critical automotive applications. A compiler engineer who understands ASIL levels, the concept phase, and hardware-software interface requirements (from the product development section) can make better decisions about code generation, static analysis integration, and safety partitioning in the compilation flow.

**Frame as:** "I've covered ISO 26262 functional safety and SOTIF in depth — I understand the certification constraints that automotive compiler output must satisfy, which is not a common background for compiler engineers."

---

**Legal AI / RegTech angle — Autonomous Driving book:**
The Wiley book covers regulations governing autonomous vehicles in depth — EU type-approval rules, liability frameworks, GDPR intersection, cross-border policy. Foreword written by an industry expert from BMW — signals recognition from a Tier 1 automotive OEM, not just academic peers. This is directly useful when applying to Legal AI, RegTech, Compliance AI, or automotive AI roles: demonstrates published domain expertise in AI regulation validated by industry. Frame as: "Published author on the regulatory landscape of AI systems (Wiley, 2026), with foreword by BMW" — especially strong for companies dealing with EU AI Act compliance, automotive regulation (UNECE WP.29), or cross-jurisdictional policy analysis.

---

## Patents (5)

1. Distributed Learning for Edge-Based Image Recognition in ITS — CN ZL2022114419068 (Jan 2026)
2. Game-Theoretic Distributed Learning for Crowdsourced Image Recognition — CN ZL2022109450145 (Jul 2025)
3. Large-Scale Edge ML Training via Probabilistic Sampling — CN ZL202110285186.X (Nov 2022)
4. Client Selection for Edge Federated Learning under Heterogeneous Data — CN ZL20211498897.1 (May 2024)
5. Air-Ground Collaborative Vehicular Crowdsensing — **Gold Medal, iENA Nuremberg 2025**

---

## Certifications

- AWS Certified Solutions Architect – Professional (Sep 2025–2028)
- AWS Certified AI Practitioner (Aug 2025–2028)
- NVIDIA-Certified Associate: Generative AI LLMs (Aug 2025–2027)

---

## Key Research Areas (for matching)

- Federated learning (6 IEEE-level publications: TSC, TITS, TNSE, JSTSP, P2P)
- Edge AI and distributed ML systems
- Multi-agent reinforcement learning for autonomous driving
- LLM systems: RAG, MCP, vector retrieval, knowledge graphs
- DL compilation and cross-platform optimization
- Vehicular/V2X networks and crowdsensing
