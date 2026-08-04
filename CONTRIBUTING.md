# Contributing

Corrections, production war stories, and "this was true in 2025 but is wrong now" reports are the most valuable contributions here.

## The Bar

Every addition is judged by one question:

> **Will this help an experienced software engineer become a better AI Engineer?**

If the answer is no, it stays out — however interesting it is.

## What Is Welcome

| Contribution | Notes |
| --- | --- |
| **Factual corrections** | Especially in Technology Landscape sections, which age fastest |
| **Production war stories** | A real failure with the root cause is worth more than a paragraph of theory |
| **Better diagrams** | One excellent diagram beats five average ones. Replacing is fine |
| **Sharper trade-offs** | If a Decision Matrix is missing a real alternative, say so |
| **Dead or moved links** | References are checked quarterly but rot faster |
| **Interview questions** | Conceptual only, and only if you have actually been asked them |

## What Is Not Welcome

- Complete applications, reference implementations, or starter templates
- API syntax reference — the provider docs do that better and stay current
- Vendor promotion, benchmark marketing, or leaderboard screenshots
- Encyclopedic expansions. Chapters must stay at 30–45 minutes. Adding a section usually means cutting one
- Restating a concept covered in another chapter. Link to it instead

## Writing Style

- **Why before how.** Architecture before code. Trade-offs before recommendations
- **Assume competence.** The reader has shipped distributed systems. Do not explain what a queue is
- **Analogies must be to traditional software engineering.** "MCP is JDBC for AI tools" lands; "MCP is like a friendly librarian" does not
- **Snippets stay tiny.** Pseudo-code or ~15 lines. If it needs more, it needs a diagram
- **Name the trade-off.** Every recommendation carries a cost. State it
- **No hedging.** "It depends" is only acceptable when followed by *what* it depends on

## Chapter Structure

New chapters use [templates/CHAPTER_TEMPLATE.md](templates/CHAPTER_TEMPLATE.md) and follow all fifteen sections in order. The consistency is the feature — readers learn to skim to the section they need.

## Diagrams

Mermaid only, rendered inline in the markdown. Preferred types: `flowchart`, `sequenceDiagram`, `stateDiagram-v2`, `mindmap`, `classDiagram`.

Before submitting, verify the diagram renders on GitHub — not just in your editor. GitHub's Mermaid version lags upstream, so avoid the newest syntax. Escape special characters in node labels (`&amp;` rather than `&`) and quote labels containing punctuation.

## Process

1. Open an issue first for anything larger than a correction — it saves you writing something that gets rejected on scope
2. One chapter or one topic per pull request
3. Explain *why* the change makes the reader a better engineer in the PR description
4. Expect editorial pushback on length. Cutting is most of the work

## Licence

Contributions are accepted under the repository's [MIT licence](LICENSE).
