# Decision Matrices

Standalone matrices, extracted from the chapters so you can bring them into an architecture review, a customer workshop, or a design doc without making anyone read a chapter first.

Each chapter contains its own Decision Matrix in section 7. This folder holds the ones that span chapters.

| Matrix | Question it answers | Source |
| --- | --- | --- |
| [Do you need an LLM at all?](do-you-need-an-llm.md) | Should this problem be solved with a language model, or with the boring technology you already run? | [Chapter 1](../docs/01-ai-engineering-overview.md) |
| [Choosing a model](choosing-a-model.md) | Which capability tier, reasoning mode, and deployment model? | [Chapter 2](../docs/02-how-llms-behave.md) |

## How to Use These

Treat them like an escalation ladder, not a menu. Start at the cheapest, most deterministic option and move up only when you can articulate why the previous rung fails.

The most valuable answer any of these matrices gives you is **"no."** A well-argued no in week one saves a quarter.
