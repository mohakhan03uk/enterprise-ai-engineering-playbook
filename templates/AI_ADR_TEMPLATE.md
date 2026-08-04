# ADR-{NNN}: {Decision Title}

**Status:** Proposed | Accepted | Superseded by ADR-{NNN}
**Date:** YYYY-MM-DD
**Deciders:** {names / roles}

---

## Context

The situation forcing a decision. Include the constraints that are actually binding — data residency, latency budget, existing cloud commitment, team skills, deadline.

**Non-functional requirements**

| Requirement | Target |
| --- | --- |
| p95 latency | |
| Cost per request | |
| Accuracy threshold (and how measured) | |
| Data residency / sovereignty | |
| Human-in-the-loop required? | |

---

## Decision

What we are doing, in one paragraph.

---

## Options Considered

| Option | Pros | Cons | Est. cost | Est. effort |
| --- | --- | --- | --- | --- |
| A. Do nothing / non-AI solution | | | | |
| B. | | | | |
| C. | | | | |

> Always evaluate "solve this without an LLM" as a real option. It wins more often than the industry admits.

---

## AI-Specific Considerations

Questions a traditional ADR does not ask, and an AI one must.

| Question | Answer |
| --- | --- |
| What is the failure mode when the model is confidently wrong? | |
| Who is accountable for a wrong answer reaching a customer? | |
| How do we evaluate this — what is the golden dataset and the passing bar? | |
| What is the prompt-injection threat model? | |
| Does untrusted input ever reach a tool with side effects? | |
| What happens on provider outage or rate limit? | |
| Can we swap the model provider, and what is the switching cost? | |
| How is cost attributed and capped, per tenant and per feature? | |
| What data leaves our boundary, and under what contract? | |
| What is the rollback plan if quality regresses in production? | |

---

## Consequences

**Positive** — what gets better.

**Negative** — what gets worse. Be specific; every AI decision buys capability with latency, cost, or control.

**Accepted risks** — with owner and review date.

---

## Reversibility

| | |
| --- | --- |
| Type | One-way door / Two-way door |
| Cost to reverse | |
| Trigger to revisit | |

---

## Evaluation Plan

How we will know, in production, whether this decision was correct. Metrics, thresholds, and the date of first review.
