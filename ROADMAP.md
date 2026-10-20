# Roadmap

## [v0.1](https://github.com/joeyconroy/joeyds/milestone/1) - The seed of a quality design system

v0.1 is meant to serve as the foundation for future experiments in machine-checkable design systems.

The system will aim to serve AI consumers just as well as it does human consumers.

Although v0.1 has an intentionally small component count, the scope is meant to cover the minimal technical architecture, governance, operations, and content required for continuous development to get up and running.

- Design token architecture:
  - Primitive and semantic token layers
  - Canonical token format
  - Transformation pipeline that generates CSS
  - Light/dark mode
  - Theming support (shipped with single theme)
- 3 components:
  - `Button`
  - `TextField`
  - `Dialog`
- Documentation + Storybook
- Automated testing
  - Visual regression testing
  - Accessibility testing
  - Unit/interaction tests
- Governance and operations:
  - Decision records
  - Required CI checks
  - Issue forms

## Next - areas to explore

Once the system has the component coverage to build complete interfaces, the goal will be to explore approaches to encoding richer semantics in design systems and improving outputs of human-AI collaboration with design systems.

### Rules (with enforcement controls) derived from stated design values

#### Problem

In most design systems, usage guidelines and rules are written as prose, and controls to enforce them are built separately, if at all, with no connection to the guidelines they enforce.

Prose documentation can be read and considered by humans, and it can be included in prompt context to _inform_ AI responses. However, prose cannot be used to rigorously constrain generated UIs, nor can it programmatically check them.

#### Explorations

- A structured system-level constitution based on a hierarchy of values and principles:
  - Values -> Principles -> Rules -> Working Enforcement Controls
- Rules as versioned, typed data with stable identifiers
- Rule checkers implemented at multiple levels of the stack: TypeScript compiler, linting, build/CI, and runtime
  - Error messages with full constitutional traces
- A formalized rule "language" lets us state what can and cannot be automatically checked
- A constitutional coverage model enabling analysis:
  - What portion of the stated values do the rules actually cover?
  - What conflicts exist between values and principles, and how are they resolved?
  - Which values can only be protected by human judgment, and how is that made explicit?

### Interaction patterns as data

#### Problem

Design systems document interaction (UX) patterns, such as confirming a destructive action or reviewing before submitting, as prose with examples.

Implemented components carry no knowledge about the patterns in which they may play a role, creating a semantic disconnect between the goal-oriented user journey layer and the user interface layer that enables it.

In most systems, nothing can check whether a rendered interface properly implements an interaction pattern, and design system consumers have no ability to declare the intent of implementing a pattern.

#### Explorations

- A small, closed vocabulary of user intents and system acts (commit, undo, ask, refuse, present)
- Interaction patterns declared as typed data using that vocabulary: the roles involved, states and the transitions between them, and what has to hold at each step
- Components declare which acts they carry, so a pattern can say what it needs
- Pattern integrity as interfaces grow

### Human-AI iterative co-design

#### Problem

Compliance and quality of AI-generated UIs degrades after a single iteration with a designer in the loop. However, navigating complex solution spaces for optimal outputs usually requires iteration.

#### Explorations

- Project idea: workbench for human-AI collaboration to generate DS-compliant UIs.
  - Embedded interaction loop that runs the DS compliance suite
  - Explores ways to maximize creativity throughout iterations while maintaining DS compliance and UX integrity
  - Focus on keeping human designer in charge of choices while offloading tasks to the model based on generative strengths (and design intelligence embedded in the system)

### DS-compliant UI Generation with Small Language Models (SLMs)

#### Problem

Multiple browsers now ship and expose Prompt APIs for Small Language Models which run locally and can perform generative tasks at lower levels of capability than LLMs. They even support the use of JSON schemas to constrain model outputs, an essential feature for generative UI pipelines.

It would be beneficial to reduce resource consumption (bandwidth, compute, electricity) while achieving the same outcomes, for example using a browser-embedded SLM in place of a cloud LLM over the network to produce quality UIs. That raises the question: _"What does an agentic design system need to be like to work well with a resource-constrained generation model?"_

#### Explorations

- How can resource-constrained models (i.e. Small Language Models) generate DS-compliant UIs?
- What architectural or design decisions inherent in the system itself can improve outcomes with a SLM as a consumer? Examples:
  - For the structured vocabulary, does a deeply hierarchical taxonomy perform better than a flatter taxonomy with more qualifiers?
  - How might changes to error outputs improve a less-capable model's ability to recover?
