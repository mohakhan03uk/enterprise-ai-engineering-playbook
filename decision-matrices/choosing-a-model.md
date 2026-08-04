# Decision Matrix: Choosing a Model

**Use this in:** architecture reviews, cost discussions, and the meeting where someone proposes standardising the whole organisation on one frontier model.

**Source chapter:** [Chapter 2 — LLM Fundamentals](../docs/02-llm-fundamentals.md)

---

## Three Independent Axes

Model selection is three separate decisions that teams collapse into one. Decide them separately.

| Axis | Question | Decided by |
| --- | --- | --- |
| **Capability tier** | Small, mid, or frontier? | Your eval suite, per use case |
| **Reasoning mode** | Extended thinking, or standard? | Whether intermediate logic must be correct |
| **Deployment** | Hosted API, cloud platform, or self-hosted open-weight? | Data boundary, volume, operational capability |

---

## Axis 1 — Capability Tier

| Tier | Choose it when | Watch out for |
| --- | --- | --- |
| **Small / fast** | Classification, routing, extraction, high-volume simple transforms, guardrail checks | Instruction-following degrades on long, multi-part prompts |
| **Mid** | The default for most production traffic; usually the best cost/quality point | Nothing structural. Start here |
| **Frontier** | Hard reasoning, long-context synthesis, high-stakes output, ambiguous instructions | Cost. Reserve for requests that need it, not the whole workload |

**Operating rule:** default to the cheapest model that passes your eval suite, and escalate **per request**, not per application.

Before reaching for any generative model, check whether the task is actually generative:

| If the task is | Consider | Why |
| --- | --- | --- |
| Fixed-label classification | An encoder model (BERT-family) | Milliseconds, pennies, deterministic, often more accurate on the narrow task |
| Ranking retrieved results | A cross-encoder reranker | Purpose-built; a generative model is the wrong shape |
| Semantic similarity | An embedding model | Chapter 6 |
| Format conversion | Code | Not a model problem |

---

## Axis 2 — Reasoning or Standard

| | |
| --- | --- |
| ✅ **Reasoning if** | A wrong intermediate step ruins the answer · Multi-step maths, complex code, planning, agent step sequencing · The task is asynchronous or batch · The gain is demonstrated on *your* eval set |
| ❌ **Standard if** | Summarisation, classification, extraction, rewriting, lookup · Interactive latency budget under a few seconds · High-volume, low-stakes traffic · You have not measured the gain |
| ⚠️ **Depends on** | Your task distribution. Cost multipliers of 5–30× are non-uniform — harder inputs generate far longer reasoning chains |

**Before committing:** measure thinking-token consumption on representative inputs, including your hardest ones. A visible 500-token answer can hide 20,000 billed reasoning tokens.

---

## Axis 3 — Hosted, Cloud Platform, or Self-Hosted

| Option | Choose it when | Real cost |
| --- | --- | --- |
| **Frontier hosted API** | Time to market matters; traffic is spiky or modest; you want the best capability with no infrastructure | Per-token pricing; data leaves your boundary; the model can change under you |
| **Cloud AI platform** (Bedrock / Vertex / Foundry) | Data must stay in your existing cloud boundary; procurement is already done | Slightly behind on newest models; still per-token |
| **Self-hosted open-weight** | Data genuinely cannot leave; volume is high *and steady*; you need a frozen model | GPUs are paid for whether used or not, plus an engineer who maintains it indefinitely |

**The break-even question nobody asks honestly:** what is your *sustained* utilisation? Reserved capacity costs the same at 10% and 90%. Include the maintaining engineer in the comparison. Self-hosting breaks even far later than most teams estimate.

---

## The Questions That Decide It

Ask these before comparing any two models.

1. **What is the longest legitimate input?** Determines the window requirement and whether chunking is needed.
2. **Interactive or batch?** Splits reasoning models, streaming, and async architecture in one answer.
3. **What languages?** Non-English input inflates token counts 1.5–3×, changing the cost model per market.
4. **What must never leave the network?** Determines deployment before capability is even discussed.
5. **What is the acceptable wait before the first word, and before the last?** Two different budgets; customers always have different tolerances.
6. **Sustained requests per day at full rollout?** The only input to a meaningful cost forecast.
7. **Who signs off that quality is good enough, against what threshold?** If there is no answer, you are not ready to choose a model.

---

## Anti-Patterns

| Pattern | Why it fails | Instead |
| --- | --- | --- |
| **One approved model organisation-wide** | You pay frontier rates for classification forever | Approve a *set* with routing rules |
| **Choosing on leaderboards** | Benchmarks are stale, contaminated, and not your traffic | Your eval set is the only benchmark that predicts anything |
| **Reasoning mode enabled globally** | 5–30× cost for no measurable gain on most traffic | Route by task |
| **Undated model aliases in production** | Behaviour changes without a deploy on your side | Pin dated versions |
| **Upgrading the model to fix quality** | The fault is usually retrieval or context, not capability | Check the trace first |
| **Self-hosting for cost reasons at low volume** | Idle GPUs are the most expensive tokens you will ever buy | Run the break-even including staffing |
