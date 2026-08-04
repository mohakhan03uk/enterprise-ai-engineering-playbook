# References

Consolidated reading list. Chapter-specific references live at the end of each chapter; this is the cross-cutting set worth bookmarking permanently.

## Primary Sources — Read These First

| Source | Why it matters |
| --- | --- |
| [OpenAI Platform Docs](https://platform.openai.com/docs) | Reference implementation of most patterns the industry then copies |
| [Anthropic Engineering Blog](https://www.anthropic.com/engineering) | The most rigorous public writing on agent design and context engineering |
| [Google Cloud — Generative AI on Vertex AI](https://cloud.google.com/vertex-ai/generative-ai/docs) | Enterprise framing: governance, grounding, deployment |
| [Microsoft — Azure AI Foundry](https://learn.microsoft.com/azure/ai-foundry/) | Enterprise governance and .NET-side patterns |

## Specifications & Standards

| Spec | Scope |
| --- | --- |
| [Model Context Protocol](https://modelcontextprotocol.io) | Standard interface between models and tools/data |
| [OpenTelemetry GenAI Semantic Conventions](https://opentelemetry.io/docs/specs/semconv/gen-ai/) | Vendor-neutral tracing for LLM and agent calls |
| [Agent2Agent (A2A) Protocol](https://a2a-protocol.org/) | Cross-vendor agent interoperability |
| [OWASP Top 10 for LLM Applications](https://genai.owasp.org/) | The security baseline; injection, data leakage, agentic risks |
| [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) | The vocabulary enterprise risk and compliance teams use |
| [EU AI Act](https://artificialintelligenceact.eu/) | Risk tiering and obligations for systems touching the EU |

## Engineering Writing Worth Following

| Source | Focus |
| --- | --- |
| [Anthropic — Building Effective Agents](https://www.anthropic.com/engineering/building-effective-agents) | The clearest statement of workflows vs agents |
| [Chip Huyen's blog](https://huyenchip.com/blog/) | Systems-level thinking on AI platforms and evaluation |
| [Simon Willison's blog](https://simonwillison.net/) | Fast, sceptical, unusually accurate tracking of the field |
| [Eugene Yan's writing](https://eugeneyan.com/writing/) | Evaluation and applied ML/LLM patterns |
| [Hamel Husain's blog](https://hamel.dev/) | Evals, error analysis, and why most AI projects fail |
| [LangChain blog](https://blog.langchain.com/) | Agent architecture patterns, framework-flavoured but substantive |

## Papers That Changed How Systems Are Built

Included only where they altered engineering practice, not for completeness.

| Paper | Why it matters |
| --- | --- |
| [Attention Is All You Need](https://arxiv.org/abs/1706.03762) (2017) | The transformer. Read the architecture section, skip the rest |
| [Retrieval-Augmented Generation](https://arxiv.org/abs/2005.11401) (2020) | Named the pattern that carries most enterprise AI value |
| [Chain-of-Thought Prompting](https://arxiv.org/abs/2201.11903) (2022) | Why "think step by step" works, and its limits |
| [ReAct: Synergizing Reasoning and Acting](https://arxiv.org/abs/2210.03629) (2022) | The loop underneath essentially every agent framework |
| [Lost in the Middle](https://arxiv.org/abs/2307.03172) (2023) | Long context windows do not mean uniform attention — a load-bearing result for RAG design |

## Staying Current Without Drowning

The field produces more content than anyone can read, and most of it is restated marketing. A workable filter:

- **Follow engineering blogs from labs and infrastructure vendors, not news aggregators.** People who operate systems write differently from people who describe them.
- **Read changelogs of the two or three tools you actually run.** Higher signal than any newsletter.
- **Ignore benchmarks and leaderboards.** They are stale within weeks and rarely reflect your workload. Your eval suite is the only benchmark that matters.
- **When something new appears, wait a quarter before adopting it.** The genuinely durable ideas are still there in three months; most of the rest are not.
