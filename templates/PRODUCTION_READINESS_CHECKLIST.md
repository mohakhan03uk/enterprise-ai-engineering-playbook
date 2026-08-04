# AI Production Readiness Checklist

For the review before an AI feature meets real users. Anything unchecked is a risk someone must accept by name.

This is the generic checklist. Chapters add domain-specific items in their FDE Notes sections.

---

## Correctness & Evaluation

- [ ] A golden dataset exists, with at least 50 representative cases including known-hard ones
- [ ] A passing threshold is defined and agreed with the business owner — not "it seems good"
- [ ] The eval suite runs in CI and blocks merges on regression
- [ ] Prompt and model versions are pinned; a provider-side model update cannot silently change behaviour
- [ ] Online quality signal exists (thumbs, escalation rate, task completion), not just offline scores

## Failure Behaviour

- [ ] Timeouts set on every model and tool call
- [ ] Retries with backoff, and a cap — a retry storm cannot amplify an outage
- [ ] Fallback path defined: cheaper model, cached answer, or an honest "I can't help with that"
- [ ] The system degrades rather than collapses when the provider is down
- [ ] Loops are bounded by iteration count, token budget, and wall-clock time

## Security

- [ ] Prompt-injection threat model documented for every path where untrusted content reaches the model
- [ ] Untrusted input cannot reach a tool with side effects without a policy check or human approval
- [ ] Tools enforce authorisation as the *end user*, not as a shared service account
- [ ] Secrets are never placed in prompts or context
- [ ] Output is treated as untrusted input by every downstream consumer — especially renderers and shells
- [ ] Data leaving the trust boundary is documented and contractually covered

## Observability

- [ ] End-to-end trace per request: inputs, retrieved context, tool calls, model calls, latencies, token counts
- [ ] Traces are queryable weeks later — you will need to debug a specific bad answer
- [ ] Prompt and model version attached to every trace
- [ ] Alerting on error rate, p95 latency, cost per hour, and guardrail trigger rate
- [ ] User feedback is captured and joined back to the trace that produced it

## Cost

- [ ] Cost per request measured, not estimated
- [ ] Per-tenant and per-feature token quotas enforced at the gateway
- [ ] Caching in place where the workload allows, and its hit rate is monitored
- [ ] A runaway loop cannot exhaust the monthly budget in an afternoon
- [ ] Cost attribution reporting exists before the first invoice, not after

## Data

- [ ] Retrieval sources have owners, refresh cadence, and a staleness alarm
- [ ] Document-level access control is enforced *at retrieval*, not by asking the model to be discreet
- [ ] PII handling documented: what is collected, redacted, logged, retained, and for how long
- [ ] Deletion requests propagate to vector stores, caches, and trace storage

## Operations

- [ ] Rollback is a config change, not a redeploy
- [ ] Runbook exists for: bad answers in production, provider outage, cost spike, injection incident
- [ ] On-call knows how to read a trace and how to disable the feature
- [ ] A named human owns quality, with a review cadence

## Human Factors

- [ ] Users are told they are interacting with an AI system
- [ ] Uncertainty is surfaced rather than hidden behind fluent prose
- [ ] Sources are cited where the answer is factual
- [ ] An escape hatch to a human exists, and its usage rate is monitored
- [ ] High-consequence actions require explicit confirmation
