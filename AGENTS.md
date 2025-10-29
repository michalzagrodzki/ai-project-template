# AGENTS.md — How to Use the Documentation Templates (for Codex / Claude Code)

**Audience:** AI coding assistants (Codex, Claude Code, ChatGPT) collaborating with human developers.
**Scope:** Instructions for generating and maintaining **Specifications** and **ADRs** using the project’s templates.

---

## 1) Purpose

Provide deterministic, high‑quality outputs from AI assistants by standardizing how to:

* Draft and refine **Feature Specifications** using `spec-template.md`.
* Create **Architectural Decision Records (ADRs)** using `adr-template.md`.
* Keep traceability between specs ⇄ plans ⇄ ADRs.

---

## 2) Source of Truth

Templates live in `docs/_templates/`:

* `spec-template.md` — feature specifications
* `plan-template.md` — stepwise implementation plan (referenced, not covered deeply here)
* `adr-template.md` — architectural decisions

Generated documents must be saved to:

* Specs → `docs/specs/YYYY-MM-DD-<feature>.md`
* ADRs  → `docs/adr/ADR-###-<decision-title>.md`

---

## 3) Golden Rules (do this every time)

1. **Follow template order exactly** (description → examples pattern).
2. **Be explicit**: avoid vague terms; use measurable criteria.
3. **Maintain links**: each ADR references its related spec; each plan references its spec.
4. **Respect boundaries**: *specs* define *what/why*; *plans* define *how*; *ADRs* explain *why this way*.
5. **Keep increments testable**: proposals should facilitate step‑by‑step implementation.
6. **No silent assumptions**: ask clarifying questions if any required data is missing.

---

## 4) Required Inputs to Generate a SPEC

When the user requests a spec, capture (or ask for) the following minimal inputs:

* Feature name and short description
* Business context and goals (measurable)
* Scope (in/out)
* Affected systems / integration points
* Constraints (performance, security, compliance, SLAs)
* Acceptance criteria (UAT style)
* Links to examples in codebase (if known)

If any of the above is missing, produce a **question block** first (5–10 precise questions).

---

## 5) SPEC — Generation Procedure

**Goal:** Create `docs/specs/YYYY-MM-DD-<feature>.md` based on `spec-template.md`.

**Steps:**

1. Copy the template sections **in order**.
2. Fill each section with crisp sentences and bullet points.
3. Keep the *Context* and *Goal* short (≤ 3 short paragraphs total).
4. For *Architecture/Design Overview*, include a light diagram (Mermaid) only if helpful.
5. Under *Integration Points*, list files/modules/APIs and env vars.
6. Convert requirements into a **UAT checklist** under *Acceptance Criteria*.
7. Add an *Open Questions* section if anything is uncertain.
8. Finish with *Definition of Done*.

**Output Requirements:**

* File path and name using today’s date (YYYY‑MM‑DD).
* Relative links to related docs when available.
* No unexplained acronyms; expand on first mention.

---

## 6) ADR — Generation Procedure

**Goal:** Create `docs/adr/ADR-###-<decision-title>.md` based on `adr-template.md`.

**Steps:**

1. Ensure a **related spec exists** and link it under *Related Specification*.
2. Write the *Decision* as a single, unambiguous statement.
3. In *Alternatives Considered*, list at least 2 credible options with brief pros/cons.
4. In *Consequences*, separate **Positive** vs **Negative**.
5. Add *Implementation Notes* with concrete config/code pointers.
6. Include a *Rollback / Supersession Plan* (name the trigger conditions).

**Output Requirements:**

* Increment ADR number sequentially (ask for current index if unknown; otherwise start at ADR‑001).
* Kebab‑case decision title; keep it short (≤ 6 words).

---

## 7) Clarifying Questions (before writing)

When information is missing, ask focused questions (5–10). Use this structure:

* **Scope boundary:** What is explicitly out of scope?
* **Non‑functional:** Throughput/latency/error budgets, data retention, security constraints.
* **Integration:** Existing modules/APIs to reuse or avoid.
* **Data model:** New schemas or changes required?
* **Ops:** Observability, rollout strategy, and rollback constraints.

---

## 8) Quality Gates & Checklists

**Specification DoD:**

* [ ] Context and Goals are concise and measurable
* [ ] Scope has clear In/Out lists
* [ ] Architecture/Design is plausible and minimal
* [ ] Integration Points list concrete files/APIs/env vars
* [ ] Acceptance Criteria are testable and unambiguous
* [ ] Open Questions present (if needed)
* [ ] Definition of Done included

**ADR DoD:**

* [ ] Decision is a single clear sentence
* [ ] At least 2 alternatives considered
* [ ] Consequences include positives and negatives
* [ ] Implementation Notes point to real files/config
* [ ] Rollback/Supersession conditions are defined
* [ ] Related Specification linked

---

## 9) Prompt Snippets (copy‑paste)

**Create a SPEC from user notes**

```
Using docs/_templates/spec-template.md, draft a specification.
If any required info is missing, first ask 5–10 precise questions.
Then output a complete Markdown file suitable for docs/specs/YYYY-MM-DD-<feature>.md.
Keep sections concise; follow the template order exactly.
```

**Review and tighten a SPEC**

```
Review this specification for clarity and testability.
- Replace vague terms with measurable ones.
- Tighten scope and acceptance criteria.
- Ensure integration points reference concrete files/modules.
Return a diff-style suggestion block and the final Markdown.
```

**Create an ADR linked to a SPEC**

```
Generate an ADR using docs/_templates/adr-template.md.
- Link the related specification.
- Provide at least 2 alternatives with pros/cons.
- Add implementation notes with file/config pointers.
- Include rollback/supersession conditions.
Return the final Markdown and a filename: docs/adr/ADR-###-<decision-title>.md.
```

---

## 10) File Naming & Linking Rules

* **Specs:** `docs/specs/YYYY-MM-DD-<feature>.md`
* **ADRs:**  `docs/adr/ADR-###-<decision-title>.md`
* **Plans:**  `docs/plans/YYYY-MM-DD-<feature>.md`
* Use **relative links** only (e.g., `../specs/...`).
* Use ISO dates; keep titles short and descriptive.

---

## 11) Style Guide (for AI outputs)

* Prefer short sentences and bullet lists.
* Use active voice; avoid marketing language.
* Put definitions before examples; keep examples minimal.
* Limit code blocks to **only what’s necessary**.
* Use Mermaid diagrams sparingly and only when they clarify flows.

---

## 12) Example End‑to‑End Flow (condensed)

1. User provides a rough idea (notes or goals).
2. Agent asks clarifying questions (5–10).
3. Agent drafts **SPEC** using `spec-template.md`.
4. Agent drafts **Plan** (separate) if requested.
5. A design choice arises → agent drafts **ADR** linked to the SPEC.
6. Human reviews; agent applies edits; documents are finalized.

---

## 13) Common Failure Modes & Fixes

* **Vague goals →** rewrite goals with metrics (e.g., p95 latency ≤ 200ms).
* **Bloated scope →** move extras to Out of Scope or Future Work.
* **Hand‑wavy integration →** add concrete file paths and env vars.
* **No rollback path →** define explicit triggers and steps to revert.

---

## 14) Maintenance

* Keep ADRs immutable once accepted; supersede with a new ADR if needed.
* Update specs when requirements change; keep a short "Changelog" section if drift occurs.
* Ensure every merged PR references a spec/plan/ADR where applicable.

---

### Appendix A — Minimal SPEC Skeleton (inline)

> Use only if the template file is unavailable.

```
# <Feature> — Specification
Date | Author | Status
1) Context
2) Goal
3) Scope (In/Out)
4) Architecture / Design Overview
5) Integration Points
6) Existing Code References
7) Risks & Alternatives
8) References
9) Acceptance Criteria (UAT)
10) Open Questions
11) Definition of Done
```

### Appendix B — Minimal ADR Skeleton (inline)

```
# ADR — <Decision Title>
Date | Author | Status | Decision ID | Related Spec
1) Context
2) Decision
3) Alternatives Considered
4) Consequences (Positive/Negative)
5) Implementation Notes
6) Rollback / Supersession Plan
7) References
```
