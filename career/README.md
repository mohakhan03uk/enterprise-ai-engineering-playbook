# Career

Where this playbook takes you, and what each destination actually involves day to day.

---

## The Honest Starting Point

If you have a decade of production software engineering behind you, you are closer to being an AI Engineer than the job postings suggest. The gap is narrower than the ecosystem's vocabulary makes it look.

What transfers directly, and is genuinely scarce in this field:

- Distributed systems intuition — AI systems are distributed systems with a probabilistic node in the middle
- Failure-mode thinking — timeouts, retries, circuit breakers, graceful degradation
- Observability discipline — the ability to debug something you cannot reproduce
- Cost awareness at scale
- API and integration design
- The instinct to ask "what happens when this breaks at 3am?"

What you have to add: how models behave, how retrieval works, how to evaluate a non-deterministic output, and how to bound autonomy. That is a matter of months, not years — and this playbook is that material.

What you do **not** need: a maths background, a PhD, or the ability to implement backpropagation. Those belong to ML Engineering, a genuinely different job.

---

## Five Roles

| Role | Core question you answer | Where you sit |
| --- | --- | --- |
| **AI Engineer** | "How do we ship this feature reliably?" | Product engineering team |
| **Applied AI Engineer** | "Can AI solve this business problem, and how well?" | Between product and engineering |
| **Forward Deployed Engineer** | "How do we make this work in *your* environment?" | On site with the customer |
| **AI Platform Engineer** | "How do fifty teams do this without fifty different stacks?" | Platform / infrastructure org |
| **Enterprise AI Architect** | "What is our reference architecture and risk posture?" | Architecture / CTO office |

### AI Engineer

Building product features on foundation models. Most of your week is retrieval quality, prompt and context design, evaluation, and chasing down why a specific answer was wrong.

**Emphasise:** Parts I–IV, Evaluation, Observability.
**Interview signal:** you can describe a RAG pipeline's failure modes without prompting, and you talk about evals unprompted.

### Applied AI Engineer

Translating fuzzy business problems into AI capabilities and proving whether they work. Heavier on problem framing and measurement, lighter on infrastructure.

**Emphasise:** Parts I–III, Evaluation, Cost.
**Interview signal:** you scope a problem down to something measurable before proposing a solution.

### Forward Deployed Engineer

The customer-facing build role. You do discovery, design in someone else's estate, integrate with systems you did not choose, and deliver against constraints nobody wrote down. Half engineering, half consulting, and unusually well suited to people with a long delivery background.

**Emphasise:** every FDE Notes section, Parts VI–VII.
**Interview signal:** you ask discovery questions during the interview itself, and you have a view on build vs buy that is not ideological.

### AI Platform Engineer

Building the paved road: LLM gateway, shared eval harness, tracing, guardrail services, cost attribution, governance. Closest to classic platform engineering — the customers are internal teams.

**Emphasise:** Parts V–VII, Deployment, Security.
**Interview signal:** you think in terms of multi-tenancy, quotas, and what happens when one team's runaway loop affects everyone else.

### Enterprise AI Architect

Owning the reference architecture, technology selection, and risk posture across an organisation. Success is measured in decisions that did not need to be reversed.

**Emphasise:** Parts VI–VII, every Decision Matrix.
**Interview signal:** you argue *against* AI for a specific use case, convincingly.

---

## Skills Matrix

Rough guide to depth required, by role. **D** = deep, **W** = working knowledge, **A** = awareness.

| Area | AI Eng | Applied | FDE | Platform | Architect |
| --- | --- | --- | --- | --- | --- |
| LLM behaviour & limits | D | D | D | W | W |
| Prompt & context engineering | D | D | D | W | W |
| Structured outputs | D | W | D | W | A |
| Retrieval / RAG | D | D | D | W | W |
| Vector databases | W | W | W | D | W |
| Tool calling & MCP | D | W | D | D | W |
| Agents & workflows | D | W | D | W | W |
| Evaluation | D | D | D | D | W |
| Observability & tracing | W | A | W | D | W |
| Guardrails | W | W | D | D | W |
| AI security | W | A | D | D | D |
| Deployment & serving | W | A | W | D | W |
| Cost engineering | W | W | D | D | D |
| Enterprise architecture | A | A | W | W | D |
| Stakeholder / discovery skill | W | D | D | W | D |

---

## Interview Preparation

AI Engineering interviews in 2026 are mostly **systems design interviews with a probabilistic component**, not ML theory exams. Expect:

| Round | What is really being tested |
| --- | --- |
| **AI system design** ("design a support agent over our docs") | Do you think in layers? Do you mention evaluation and failure modes unprompted? |
| **Debugging a bad answer** | Can you localise a failure to retrieval, context, or generation? |
| **Trade-off discussion** | RAG vs fine-tuning vs longer context. Do you reason, or recite? |
| **Security** | Prompt injection. Do you know why it cannot be fully "fixed" with a prompt? |
| **Cost** | Can you estimate cost per request and name the levers? |
| **Behavioural / delivery** (FDE especially) | Have you told a customer no, and made it stick? |

Three things that separate strong candidates from the rest, consistently:

1. **They bring up evaluation without being asked.** This is the single clearest seniority signal in the field.
2. **They can say when *not* to use AI**, with a specific example.
3. **They talk about failure modes as design inputs**, not as edge cases to handle later.

Each chapter ends with 10–15 conceptual interview questions drawn from real loops.

---

## A Realistic Timeline

For an experienced engineer studying alongside a full-time job:

| Month | Focus | You can now |
| --- | --- | --- |
| 1 | Parts I–II | Discuss LLM behaviour precisely; design a basic retrieval pipeline |
| 2 | Part III + Evaluation | Build a grounded, tool-using feature with a real eval suite |
| 3 | Part IV + Observability | Design and bound an agent; debug it from traces |
| 4–5 | Parts V–VI | Choose a framework defensibly; own security and cost |
| 6 | Part VII + a real project | Hold your own in an architecture review |

The compressing variable is not reading speed — it is whether you build something real alongside it. Reading twenty-eight chapters and shipping nothing produces someone who can talk about AI Engineering. Reading ten and shipping one grounded, evaluated, instrumented feature produces an AI Engineer.
