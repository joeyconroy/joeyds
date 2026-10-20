---
status: "accepted"
date: 2026-10-12
supersedes: []
superseded-by: []
---

# Use MADR (Markdown Architectural Decision Records)

## Context and Problem Statement

Architecturally significant decisions in this repository need a durable, readable record.
Which format should the records follow?

## Decision Drivers

- Want: readable in the repository with no tooling.
- Want: a fixed structure, so records compare across time.
- Want: metadata that can be read programmatically.
- Avoid: unnecessary overhead.

## Considered Options

- MADR 4.0.0
- Michael Nygard's template
- Sustainable Architectural Decisions
- [Other templates](https://github.com/joelparkerhenderson/architecture_decision_record)
- Formless

## Decision Outcome

Chosen option: "MADR 4.0.0", because it is the only option with a fixed place for considered options and their trade-offs, and it is maintained.

Front matter is trimmed to `status`, `date`, `supersedes` and `superseded-by`. The last two are lists, so a graph of records can be built from them later.

Full form (with optional sections) is chosen over minimal or bare MADR templates because the optional sections are where alternatives and confirmation live.

### Consequences

- Good, because every record carries its alternatives and trade-offs.
- Bad, because the full form is long for small decisions.

### Confirmation

- The template file itself, `docs/decisions/adr-template.md`, which every record starts from
- ADR checklist item in the PR template
- Future: indexing and metadata checks

## Pros and Cons of the Options

### MADR 4.0.0

- Good, because options and trade-offs are part of the structure.
- Good, because maintained; 4.0.0 released 2024-09-17.
- Bad, because the full form is heavy for small decisions.

### Michael Nygard's template

- Good, because short, and established.
- Bad, because no place for alternatives.

### Sustainable Architectural Decisions

- Good, because one sentence per decision.
- Bad, because no place to capture trade-offs for alternatives.

### Other templates

- Neutral, because many exist and none dominates.

### Formless

- Good, because no overhead.
- Bad, because it doesn't promote a consistent decision-making process.
- Bad, because records don't compare across time.

## More Information

MADR: https://adr.github.io/madr/
