# Roadmap

## Publishing Model

One chapter at a time. A finished chapter beats four drafts.

Each chapter ships complete — plain-English explanation, working snippets in raw OpenAI and in LangChain or LangGraph, one diagram, a decision matrix, FDE notes, and verified references. Nothing merges as a stub.

---

## Current Status

| | Count |
| --- | --- |
| Published | 8 / 28 |
| Planned | 20 |

**Parts I and II complete.**
**Just shipped:** [Chapter 8 — Building MCP Servers and Clients](docs/08-building-mcp-servers-and-clients.md)
**Next up:** Chapter 9 — Embeddings

---

## Chapter Queue

### Part I — Foundations

- [x] **1. AI Engineering Overview** — the discipline, the layers of a real system, and why the model is the easy part
- [x] **2. How LLMs Behave** — the five behaviours that break your engineering assumptions, and what each one costs you
- [x] **3. The OpenAI API, Properly** — messages, roles, parameters, `finish_reason`, streaming, and errors. Everything later assumes this
- [x] **4. Prompt Engineering** — prompts as a versioned interface, not wordsmithing
- [x] **5. Structured Outputs** — constrained decoding, schema design, and why a guaranteed shape says nothing about truth

### Part II — Action: Tools and MCP

- [x] **6. Function and Tool Calling** — the mechanism behind every agent, and why every tool call is untrusted input
- [x] **7. MCP Explained** — the N×M problem, the three primitives, the stateless revision, and what MCP does not solve
- [x] **8. Building MCP Servers and Clients** — designing for a consumer that cannot read docs, and the token audience rule you cannot get wrong

### Part III — Data: Grounding

- [ ] **9. Embeddings** — vectors as a similarity primitive, and where the idea breaks down
- [ ] **10. Retrieval-Augmented Generation** — the highest-leverage pattern in enterprise AI
- [ ] **11. Vector Databases** — do you need one, or is it an index on the database you already run?
- [ ] **12. Chunking and Retrieval Quality** — where RAG systems actually fail, and how to measure it
- [ ] **13. Knowledge Graphs and GraphRAG** — when relationships matter more than similarity

### Part IV — Agents

- [ ] **14. What an Agent Really Is** — the loop, the failure modes, and when a workflow is the better answer
- [ ] **15. LangChain** — the pieces worth knowing, the pieces to skip, and the abstraction tax
- [ ] **16. LangGraph** — state, nodes, edges, checkpoints, and human-in-the-loop
- [ ] **17. Agent Patterns and Workflows** — routing, chaining, parallelism, reflection, approval gates
- [ ] **18. Memory** — short-term, long-term, and why most "memory" is a database with better marketing
- [ ] **19. Multi-Agent Systems and A2A** — coordination cost, and the cases where it genuinely pays

### Part V — The Wider Landscape

- [ ] **20. The Framework Landscape** — OpenAI Agents SDK, Google ADK, CrewAI, Semantic Kernel, LlamaIndex, PydanticAI, DSPy, Agno. How to evaluate a framework, applied

### Part VI — Production

- [ ] **21. Evaluation** — golden datasets, LLM-as-judge, and the regression suite that gates every change
- [ ] **22. Observability and LangSmith** — traces, OpenTelemetry GenAI conventions, and debugging a bad answer from last month
- [ ] **23. Guardrails** — input and output validation, PII, topical boundaries, and the latency they cost
- [ ] **24. AI Security** — prompt injection, the lethal trifecta, OWASP LLM and Agentic Top 10
- [ ] **25. Deployment and Serving** — hosted vs self-hosted, gateways, routing, caching, tail latency
- [ ] **26. Cost Optimization** — token budgets, caching, model tiering, cost attribution

### Part VII — Enterprise

- [ ] **27. Enterprise AI Architecture** — the reference architecture, and the org chart it implies
- [ ] **28. Future Trends and Staying Current** — what is durable, what is hype, and how to tell in six months

---

## House Style

The playbook is written for an experienced software engineer with **no ML background** who is building tools, MCP servers, and agents.

| Rule | Detail |
| --- | --- |
| **Concrete over abstract** | Every concept is shown in raw OpenAI first, then in LangChain or LangGraph |
| **Concept and framework named separately** | "This is tool calling; LangChain calls it `bind_tools`" — so the chapter survives a rename |
| **Snippets under 12 lines** | If it needs more, it needs a diagram |
| **No maths, ever** | ML appears only as intuition, in a clearly marked skippable box |
| **No hardware internals** | Give the consequence, not the mechanism |
| **Self-contained examples** | Every example is explained where it appears. No cross-chapter memory required |
| **Paragraphs of 2–4 sentences** | And a bolded takeaway opening each section, so skimming works |

Full guidance: [templates/CHAPTER_TEMPLATE.md](templates/CHAPTER_TEMPLATE.md).

---

## Design Decisions

Choices about scope, recorded so they can be challenged.

### Builder-first ordering

Tool calling is Chapter 6 and MCP is Chapter 7, rather than 10 and 11. Most readers of this playbook are building tools, MCP servers, and agents — making them wait through five chapters of retrieval theory first is the wrong order for that job. Retrieval follows immediately after, because an agent that retrieves badly fails for retrieval reasons.

### A dedicated chapter on the OpenAI API

Chapter 3 exists because everything later assumes you can read a request and a response object fluently — roles, `finish_reason`, `usage`, streaming, tool call structure. It is also the fastest way to make abstract concepts concrete.

### LangChain and LangGraph get chapters; the rest get a survey

They are what most teams actually encounter, and LangGraph dominates production agent deployments. Nine separate framework chapters would be nine variations on one theme and stale within a year, so the others are covered comparatively in Chapter 20 — after you know enough to evaluate them.

### Function Calling and Tool Calling are one chapter

Same mechanism, two names. Two chapters would repeat each other.

### No chapter on fine-tuning

Fine-tuning is ML Engineering, and in enterprise settings it is the answer far less often than people expect. It appears as a *decision* — when it beats retrieval and prompting — inside the retrieval and cost chapters, not as a how-to.

---

## Non-Goals

- Complete applications or reference implementations
- API syntax reference — provider docs do that better and stay current
- Model benchmarks and leaderboards — stale within weeks
- Model training, fine-tuning mechanics, or GPU work
- Vendor advocacy

---

## Maintenance

The ecosystem moves fast; the engineering reasoning does not. Volatile content — Technology Landscape sections, references, framework APIs — is isolated in named sections that can be refreshed without a rewrite.

**Review cadence:** Technology Landscape, code snippets, and References reviewed quarterly. Everything else on change.
