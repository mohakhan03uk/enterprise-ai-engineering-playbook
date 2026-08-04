# Roadmap

## Publishing Model

One chapter at a time. A finished chapter beats four drafts.

Each chapter ships complete — all fifteen sections, diagrams, decision matrix, FDE notes, interview questions, and verified references. Nothing is merged as a stub.

---

## Current Status

| | Count |
| --- | --- |
| Published | 1 / 28 |
| In progress | 0 |
| Planned | 27 |

**Just shipped:** [Chapter 1 — AI Engineering Overview](docs/01-ai-engineering-overview.md)
**Next up:** Chapter 2 — LLM Fundamentals

---

## Chapter Queue

### Part I — Foundations

- [x] **1. AI Engineering Overview** — the discipline, the seven-layer stack, and why the model is the easy part
- [ ] **2. LLM Fundamentals** — tokens, context windows, sampling, latency, and the four behaviours that break your assumptions
- [ ] **3. Prompt Engineering** — prompts as a versioned interface, not wordsmithing
- [ ] **4. Structured Outputs** — getting machine-parseable data out of a text generator, reliably
- [ ] **5. Context Engineering** — the discipline that replaced prompt engineering: what goes in the window and why

### Part II — Grounding

- [ ] **6. Embeddings** — vectors as a similarity primitive, and where the metaphor breaks
- [ ] **7. Retrieval-Augmented Generation** — the highest-leverage pattern in enterprise AI
- [ ] **8. Vector Databases** — do you need one, or is it an index on the database you already run?
- [ ] **9. Knowledge Graphs & GraphRAG** — when relationships matter more than similarity

### Part III — Action

- [ ] **10. Function & Tool Calling** — the mechanism behind every agent; why "function" and "tool" calling are the same thing
- [ ] **11. Model Context Protocol (MCP)** — the integration standard, and what it does and does not solve

### Part IV — Agents

- [ ] **12. AI Agents: Foundations** — the loop, the failure modes, and when a workflow is the better answer
- [ ] **13. Agent Workflows & Orchestration Patterns** — routing, chaining, parallelism, reflection, human-in-the-loop
- [ ] **14. Memory** — short-term, long-term, episodic, semantic; and why most "memory" is a database with better marketing
- [ ] **15. Multi-Agent Systems & A2A** — coordination cost, and the cases where it genuinely pays

### Part V — Frameworks

- [ ] **16. Choosing an Agent Framework** — the decision framework, applied to the 2026 landscape
- [ ] **17. LangChain & LangGraph** — the production default, its graph model, and its verbosity tax
- [ ] **18. Provider-Native SDKs** — OpenAI Agents SDK, Claude Agent SDK, Google ADK, Microsoft Agent Framework / Semantic Kernel
- [ ] **19. Data & Typed Frameworks** — LlamaIndex, PydanticAI, DSPy, CrewAI, Agno

### Part VI — Operations

- [ ] **20. Evaluation** — golden datasets, LLM-as-judge, and the regression suite that gates every change
- [ ] **21. AI Observability & Tracing** — OpenTelemetry GenAI conventions, LangSmith, and what a good trace looks like
- [ ] **22. Guardrails** — input and output validation, PII, topical boundaries, and the latency they cost
- [ ] **23. AI Security** — prompt injection, the lethal trifecta, OWASP LLM and Agentic Top 10
- [ ] **24. Deployment & Serving** — hosted vs self-hosted, gateways, routing, caching, tail latency

### Part VII — Enterprise

- [ ] **25. Enterprise AI Architecture** — the reference architecture, and the org chart it implies
- [ ] **26. Cost Optimization** — token budgets, caching layers, model tiering, cost attribution
- [ ] **27. Building an AI Platform** — the paved road: gateway, eval harness, tracing, governance, self-service
- [ ] **28. Future Trends & Staying Current** — what is durable, what is hype, and how to tell the difference in six months

---

## Design Decisions

Choices made about scope, recorded so they can be challenged.

### Function Calling and Tool Calling are one chapter, not two

They are the same mechanism described at two levels of abstraction. Two chapters would repeat each other. The chapter covers both and explains why the industry uses both terms.

### Nine framework topics became four chapters

A chapter each for LangChain, LangGraph, OpenAI Agents SDK, Google ADK, CrewAI, Semantic Kernel, LlamaIndex, PydanticAI, DSPy, and Agno would be nine variations on the same content — and stale within a year.

What actually transfers is *how to evaluate a framework*. So Part V leads with the decision framework, gives LangGraph a full chapter because it dominates production deployments, and covers the rest comparatively. If a framework becomes a production default later, it earns its own chapter then.

### RAG comes before agents

The original topic ordering placed retrieval after the agent frameworks. Reversed deliberately: most enterprise AI projects are retrieval problems, agents are a smaller subset, and agents that retrieve badly fail for retrieval reasons. Grounding first.

### No chapter on fine-tuning

Fine-tuning is ML Engineering, not AI Engineering, and in enterprise settings it is the answer far less often than people expect. It is covered as a *decision* — when it beats retrieval and prompting — inside Context Engineering and Cost Optimization, rather than as a how-to.

---

## Non-Goals

- Complete applications or reference implementations
- API syntax reference — the provider docs do that better and stay current
- Model benchmarks and leaderboards — stale within weeks
- Model training, fine-tuning mechanics, or GPU kernel work
- Vendor advocacy

---

## Maintenance

The ecosystem moves fast; the engineering reasoning does not. Chapters are structured so that the durable parts — mental models, architecture, trade-offs — stay valid, and the volatile parts — Technology Landscape, References — are isolated in named sections that can be refreshed without a rewrite.

**Review cadence:** Technology Landscape and References sections reviewed quarterly. Everything else, on change.
