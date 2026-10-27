---
status: "accepted"
date: 2026-10-26
category: "operations"
supersedes: [] # ADR numbers this record replaces, e.g. [0003]
superseded-by: [] # ADR numbers that replace this record; set only when status is superseded
---

# Categorize decision records with a front-matter field

## Context and Problem Statement

Not every decision worth recording is architectural. Decisions about how the project is operated also need a durable record, and readers need to tell the two kinds apart.

How should decision records be categorized?

## Decision Drivers

- Want: distinguish an architecture decision from an operations decision at a glance.
- Want: continue using MADR format and global numbering.
- Want: metadata that can be read programmatically.
- Want: ability to add more categories in future if needed.
- Avoid: moving or renaming existing records.

## Considered Options

- A `category` front-matter field
- Subfolders per category, numbered locally (MADR's own approach)
- Subfolders per category, numbered globally
- No categories

## Decision Outcome

Chosen option: "A `category` front-matter field", because it maintains global numbering and existing file paths, and is machine-readable.

The values are a closed set, enumerated in `CONTRIBUTING.md`, that can be extended over time. Initial values: `architecture` and `operations`.

This option gives less visibility to record categories, but code search and future indexing will compensate.

### Consequences

- Good, because records can be filtered by category without changing how they are referenced.
- Bad, because existing records need the field added.
- Bad, because a closed category set has to be governed.

### Confirmation

- `CONTRIBUTING.md` enumerates the allowed values.
- `docs/decisions/adr-template.md` offers the field.
- Future: a CI check of front matter.

## Pros and Cons of the Options

### A `category` front-matter field

A field added to the YAML front-matter in the ADR template.

- Good, because it doesn't change record numbering or paths.
- Good, because it is machine-readable.
- Good, because it supports future additions to categories.
- Bad, because the category is not visible in a folder listing.

### Subfolders per category, numbered locally

Create a subfolder under `docs/decisions` for each category, but make numbers unique within each category folder, not globally.

- Good, because the category is visible in the folder structure.
- Good, because it supports future additions to categories.
- Bad, because numbers are no longer unique, which breaks reference by number.
- Bad, because existing records move, and paths change if a category changes.

### Subfolders per category, numbered globally

Create a subfolder under `docs/decisions` for each category, and keep numbers unique across all ADR subfolders.

- Good, because the category is visible in the folder structure.
- Good, because it supports future additions to categories.
- Neutral, because existing unique IDs are retained.
- Bad, because existing records move, and paths change if a category changes.
- Bad, because adding a number may involve looking at all folders.

### No categories

Reject categories for ADRs and make no changes to the template.

- Good, because no overhead.
- Bad, because no ability to differentiate architectural decision records from non-architectural records.

## More Information

- [MADR decision 0010](https://adr.github.io/madr/decisions/0010-support-categories.html)
- [ADR = Any Decision Record? (Zimmermann, 2021)](https://ozimmer.ch/practices/2021/04/23/AnyDecisionRecords.html)
