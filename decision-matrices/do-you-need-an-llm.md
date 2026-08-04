# Decision Matrix: Do You Need an LLM At All?

**Use this in:** discovery workshops, architecture reviews, and any meeting where "let's use AI" has been said but not justified.

**Source chapter:** [Chapter 1 — AI Engineering Overview](../docs/01-ai-engineering-overview.md)

---

## The Escalation Ladder

Start at rung 1. Move up only when you can articulate why the rung below fails for *this* problem. Every rung upward buys capability with latency, cost, non-determinism, and a new class of failure.

| # | Approach | Use when | Cost of getting here |
| --- | --- | --- | --- |
| 1 | **Rules / SQL / config** | The logic is expressible and stable | None. This is what you already run |
| 2 | **Search — keyword or full-text** | Users need to *find* something, not be *told* something | Low |
| 3 | **Classical ML** | You have labelled data and need a prediction: score, rank, classify, forecast | Training and monitoring pipeline |
| 4 | **LLM, single call** | Input is unstructured language; output is language or structured data | Non-determinism, per-token cost, an eval suite |
| 5 | **LLM + retrieval (RAG)** | The answer depends on your data, which changes | A retrieval pipeline, and it becomes the main source of bugs |
| 6 | **LLM + tools** | The system must read or change state in other systems | Authorisation, side effects, injection surface |
| 7 | **Agent (a loop)** | Steps cannot be known in advance | Unbounded cost and latency; hardest debugging in the field |
| 8 | **Multi-agent** | Genuinely parallel subproblems with different tool scopes | Coordination overhead that usually exceeds the benefit |

> Most enterprise value sits at rungs 4–6. Most enterprise *disappointment* comes from starting at rung 7.

---

## Should this problem use an LLM?

| | |
| --- | --- |
| ✅ **YES if** | The input is unstructured language, images, or documents · The output tolerates variation in wording · A wrong answer is recoverable, or a human reviews it · The task is currently done by a person reading and writing text · The rules are too numerous or too fuzzy to enumerate |
| ❌ **NO if** | The answer must be exactly reproducible · A wrong answer is unrecoverable and unreviewed · A deterministic rule already solves it · The task is arithmetic, aggregation, or a database query · You cannot define what "correct" means · Latency budget is under ~200ms end-to-end |
| ⚠️ **It depends on** | Whether you can build an evaluation set. If nobody can produce 50 examples with agreed-correct answers, the project is not ready — regardless of the technology |

---

## The Four Questions That Kill Bad Projects Early

Ask these in week one. Each has ended a project that would otherwise have died expensively in month six.

**1. "Show me fifty examples with the correct answers."**
If they cannot, the requirements do not exist yet. You have a definition problem, not an AI problem.

**2. "What happens when it is confidently wrong?"**
If the answer is "that would be very bad" and there is no human in the loop, either add the human or change the scope.

**3. "Who is accountable when a customer acts on a wrong answer?"**
If nobody has an answer, the project will stall at the legal or risk review, not at the engineering.

**4. "What does this cost at full volume?"**
Multiply expected tokens per request by expected requests per month. If the number is uncomfortable at pilot scale, it is fatal at production scale.

---

## Common Justifications, and What They Actually Mean

| What is said | What it usually means | Better response |
| --- | --- | --- |
| "We need an AI strategy" | Someone senior read something | "Which business process is expensive because a human reads text? Start there" |
| "Our competitor launched a copilot" | Feature anxiety | "What do our users currently do that takes too long?" |
| "We want an agent" | They saw a demo | "What decision would it make that we cannot pre-define? If none, you want a workflow" |
| "We need to use our data" | Real, but unscoped | "Which questions should it answer? Who owns those documents? Who is allowed to see them?" |
| "The model isn't accurate enough" | Almost always a retrieval or context problem | "Show me what was actually put in the context window for a failing case" |

---

## The Reverse Test

Before committing, argue the opposite position for five minutes: *why should this **not** use AI?*

If you cannot construct a credible argument against it, you have not understood the problem well enough to build it.
