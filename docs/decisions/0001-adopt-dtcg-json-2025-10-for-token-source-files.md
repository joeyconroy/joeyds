---
status: "accepted"
date: 2026-10-24
supersedes: [] # ADR numbers this record replaces, e.g. [0003]
superseded-by: [] # ADR numbers that replace this record; set only when status is superseded
---

# Adopt DTCG JSON 2025.10 for token source files

## Context and Problem Statement

Design tokens are a core source of truth for the system and are direct inputs to the transformation pipeline which outputs styling code (e.g. CSS) for implementation technology.

What is the best format for representing this system's design tokens in source code?

Out of scope:

- the build tool used for the token pipeline (separate ADR)
- token naming and taxonomy (separate ADR)
- approach to theming (separate ADR)

## Decision Drivers

- Want: community-driven standard (so format reflects broad needs, not a vendor roadmap).
- Want: compatibility with existing tools (for flexibility).
- Want: a clearly published specification.
- Nice to have: a specified mechanism for extensible metadata (for future capabilities).
- Nice to have: a stable and mature specification.
- Avoid: vendor lock-in (to preserve agility).

## Considered Options

- DTCG JSON 2025.10
- A tool's third-party format
- No token files; just CSS custom properties

## Decision Outcome

Chosen option: DTCG JSON 2025.10, because it is a community-driven, tool-neutral format with a published specification.

### Consequences

- Good, because it separates the format from build tool, making it easier to replace pipeline elements.
- Good, because the system is moving in a community-driven direction.
- Good, because its standardized support for metadata will be important for future experiments.
- Good, because it provides foundation for future support of non-web consumers.
- Bad, because the stable release is less than a year old. Tool conformance to 2025.10 has to be checked per tool.

### Confirmation

A CI check validates every token source file against the Format Module 2025.10 and fails on any invalid file. The validator is chosen in the token build tool record.

## Pros and Cons of the Options

### DTCG JSON 2025.10

A JSON format for design tokens created by the W3C Design Tokens Community Group (DTCG).

The format specification covers: what makes a token valid; JSON file structure of tokens and groups; token properties like `$type`, `$value`, and `$extensions`; group-level types and group extension; aliases between tokens and their resolution rules; primitive and composite value types.

- Good, because the format has no owner. It is tool-neutral by design and has a published specification.
- Good, because `$extensions` provides an extension point for custom metadata.
- Good, because current build tools read it: Terrazzo natively, Style Dictionary since version 4.
- Bad, because adoption among shipped design systems is still low, so there are few reference implementations to learn from.

### A tool's third-party format

A tool-specific format for representing tokens in code, such as that of Style Dictionary or Tokens Studio.

- Good, because these formats are more mature and widely used.
- Good, because they are well documented by vendors and have plenty of examples.
- Bad, because the formats are tool-specific and driven by the vendor's product strategy.
- Bad, because the unique format causes vendor lock-in.
- Bad, because each tool has a unique way of extending with custom metadata.
- Neutral, because tools are increasingly providing DTCG JSON compatibility.

### No token files; just CSS custom properties

Hand-written custom CSS property declarations in the tokens layer are the source, eliminating a build pipeline.

- Good, because it gives you maximal control over the outputs that get consumed.
- Good, because it eliminates significant infrastructure by obviating the build pipeline.
- Neutral, because consumer receives the same format as other options.
- Bad, because it is CSS-only. No path to design-tool variables or non-CSS consumers.
- Bad, because it makes it harder to manage naming conventions and the cascade at scale.
- Bad, because there is no machine-readable token data: no typing beyond `@property`, no descriptions, no deprecation flags, no enriched metadata, no alias graph without parsing CSS.

## More Information

Final DTCG Reports:

- [Format Module 2025.10](https://www.w3.org/community/reports/design-tokens/CG-FINAL-format-20251028/)
- [Resolver Module 2025.10](https://www.w3.org/community/reports/design-tokens/CG-FINAL-resolver-20251028/)
- [Color Module 2025.10](https://www.w3.org/community/reports/design-tokens/CG-FINAL-color-20251028/)

Related ADRs:

- taxonomy and naming <!-- link when merged -->
- token build tool <!-- link when merged -->
- theming and modes <!-- link when merged -->
