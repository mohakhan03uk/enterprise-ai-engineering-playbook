# Diagrams

Reusable Mermaid sources. Chapter diagrams are inline in the chapter markdown so they render on GitHub without a build step; this folder holds the ones referenced from more than one place.

| Diagram | Description | Used in |
| --- | --- | --- |
| [production-ai-stack.mmd](production-ai-stack.mmd) | The seven layers of a production AI system | [Chapter 1](../docs/01-ai-engineering-overview.md), Chapter 25 |

## Conventions

- **Mermaid only.** It renders natively on GitHub, diffs as text, and survives being edited by someone who is not a designer.
- **One diagram per idea.** One excellent diagram beats five average ones. If a diagram needs a legend to be understood, it is doing too much.
- **Stick to the conservative subset.** GitHub's Mermaid version lags upstream — verify rendering on GitHub, not just in a local preview.
- **Escape special characters.** Use `&amp;` for `&`, and quote any label containing punctuation or brackets.
- **Prefer these types:** `flowchart`, `sequenceDiagram`, `stateDiagram-v2`, `mindmap`, `classDiagram`.
