# Contributing to joeyds

Welcome! This project is still in its early stages and will offer many more opportunities to contribute in the future.

## Ways to contribute

For now, we gladly accept bug reports and accessibility issue submissions. In the future, you will be able to suggest enhancements to the system.

- Report an [accessibility issue](https://github.com/joeyconroy/joeyds/issues/new?template=a11y_issue.yml)
- Submit a [bug report](https://github.com/joeyconroy/joeyds/issues/new?template=bug_report.yml)

<!-- section: working on the code -->
<!-- general workflow loop -->
<!-- commit and title format: decided in the versioning and release notes record -->
<!-- issues, branches, and PRs -->

## Decision records

Significant decisions are captured as decision records in `docs/decisions/`, using [the template](/docs/decisions/adr-template.md) based on [Markdown Architectural Decision Records (MADR)](https://adr.github.io/madr/).

Decision records exist to:

1. encourage a good decision-making process
2. encourage clear technical communication
3. answer the question, "How did the project come to be as it is?"

### Which decisions warrant a decision record?

Not every design or engineering decision needs a record.

The threshold is about risk: uncertainty that can cause loss of value, whether existing or potential. The risk can lie in the product (_what_ is built) or the process (_how_ it is built). **Decisions that carry significant risk deserve a record.**

A record is warranted if the answer to either question is yes:

- Would it be costly to get the decision wrong, or to reverse it later?
- Would getting it right bring significant value?

To identify that cost or value, consider whether the decision:

- affects a quality the project relies on, such as performance, accessibility, maintainability, or portability
- adds reliance on something outside the project's control, like a tool, service, or specification
- affects many parts of the system, or every change
- tackles a kind of problem the project hasn't solved before

### When a record should get committed

- A record written ahead of the implementation is committed in its own pull request, after approval.
- A record for a decision that arises during implementation is committed on that work's branch.

### How to write a record

1. Copy the template into `docs/decisions/`, named as below.
2. Fill in every section the template does not mark optional.
3. Commit it as described above.

Conventions:

- **Front matter:** every field is required. `supersedes` and `superseded-by` may be empty lists.
- **Title:** states the outcome, concisely.
- **Number:** the next four-digit number, assigned at commit, in commit order.
- **Filename:** the number, then the full title in lowercase with dashes. For example, `0001-adopt-dtcg-json-2025-10-for-token-source-files.md`.
- **Links to records not yet written:** plain words followed by `<!-- link when merged -->`. When the later record merges, earlier records are edited to link to it.
- **Category:** one of the values below. The set is closed.

| Decision Category | Description                                                                      |
| ----------------- | -------------------------------------------------------------------------------- |
| `architecture`    | What is built: structure, tokens, components, build and packaging                |
| `operations`      | How the project is run: branching, versioning, releases, licensing, contributing |

### Editing a record

Once a record is accepted, its decision and reasoning do not change. To change a decision, write a new record that supersedes it.

These edits are allowed:

- updating front matter, such as `status` and `superseded-by` when a later record replaces this one
- adding links to records that have since merged
- fixing typos and formatting that do not change meaning

### Confirming the implementation

Every decision record includes a "Confirmation" section describing how to check that the decision was implemented. When a record merges, an issue is opened to track its confirmation, referencing the record. The resulting check carries the record's number in its name.
