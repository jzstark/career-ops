# Article Digest — Proof Points for Jianxin Zhao

## Core Focus (use this to frame the narrative in evaluations)

**Primary direction:** LLM inference and serving optimization — latency, throughput, cost reduction — targeting cloud and edge/embedded deployment (robots, embedded devices). NOT training. The background in DL compilers, edge AI, distributed systems, and federated learning feeds directly into this.

**Secondary direction:** Agentic AI systems — token cost reduction, efficient tool use, multi-agent coordination. Active research: modifying LibreChat's orchestration layer to reduce token spend in agentic workflows (paper in progress).

**How to use this in evaluations:**
- For inference/serving roles: lead with DL compiler work, edge AI deployment experience, Triton/CUDA skills, and the direction of travel
- For agent roles: lead with Legal AI system (LibreChat + MCP), token cost research, and agentic workflow design
- Acknowledge that current portfolio is research-stage on inference specifically — compensate with depth of adjacent systems work and rapid learning track record
- Never pitch as a training specialist; always reframe past distributed/federated work as "systems thinking that now applies to serving"

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
