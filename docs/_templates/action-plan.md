# Action Plan (End-to-End Template)

## Stage 0 — Preparation (one-time setup)
- [ ] Repository structure:
  - `docs/adr/` – architectural decision records (ADRs)
  - `docs/specs/` – feature specifications (MD)
  - `docs/plans/` – step-by-step implementation plans
  - `tests/` – unit and functional tests
- [ ] Naming convention: `YYYY-MM-DD-feature-name.md`
- [ ] Place reusable templates under `docs/_templates/`
- [ ] Branching: `feat/<short-description>` + small PRs with a Definition of Done checklist
- [ ] “Safety rails”: CI runs linting and tests on every PR

---

## Stage 1 — Analysis & Specification
**Goal:** Clearly describe what you want to build — as if explaining it to a junior developer, including code references and documentation links.

### Steps
1. Create an ADR (if applicable) and a specification file: `docs/specs/YYYY-MM-DD-<feature>.md`.
2. Do quick research (including existing code references and patterns).
3. Include minimal code examples that show where similar logic already exists.
4. Add relevant documentation or API references.
5. Commit the draft and send it to Claude (or another assistant).

### Definition of Done
- [ ] Specification file includes context, goals, scope, and constraints.
- [ ] Contains code examples or file references.
- [ ] Contains documentation or guideline links.
- [ ] ADR exists if the change introduces architectural implications.

### Template: Specification (MD)
```markdown
# <Feature Name> — Specification
**Date:** YYYY-MM-DD  
**Author:** <Your name>  
**Context:** Describe the business or technical background (1–3 short paragraphs).  
**Goal:** Clear, measurable outcomes.  
**Scope:** In-scope / Out-of-scope bullet points.  
**Architecture / Patterns:** Describe or draw the flow.  
**Integration points:** Modules, services, or DBs affected.  
**Existing code examples:** file paths + short snippets.  
**Risks and alternatives:** brief summary.  
**References:** documentation links, standards, guides.  
**Acceptance Criteria (UAT):** checklist of expected outcomes.
```

## Stage 2 — Analysis & Specification
**Goal:** Ensure full understanding and identify missing details before coding.

### Steps
Read this specification.
1) Confirm whether you understand the scope and goals.
2) List missing information required to implement it (critical first, nice-to-have second).
3) Ask 5–10 precise questions to clarify anything ambiguous.

### Definition of Done
- [ ] You received a list of relevant questions and answered them clearly.
- [ ] The specification has been updated with the missing details (commit done).

## Stage 3 — Step-by-Step Implementation Plan
**Goal:** Produce a Markdown plan where after every step, the app builds and runs successfully, and each change can be tested independently.

### Steps
Based on this specification and my answers, create a detailed step-by-step implementation plan in Markdown.
- Split into small, self-contained steps (1–2 hours each).
- After each step, the app should still run.
- Each step should include: code/file changes, migrations, contract updates, and which tests to add.
- Add "How to test" for every step.
- At the end, include a Definition of Done checklist and rollback plan.

### Definition of Done
- [ ] Plan is incremental and testable after each step.
- [ ] Each step includes “How to test” (manual + hints for automated tests).
- [ ] Includes a list of unit/functional tests to be added.

### Template: Specification (MD)
```markdown
# Implementation Plan — <feature>
## Step 1: <title>
Changes: …  
Files: …  
Tests to add/update: …  
**How to test:** commands, endpoints, and expected results.

## Step 2: …
...

## Definition of Done (Overall)
- [ ] All unit/functional tests pass in CI.
- [ ] No regressions on critical paths.
- [ ] Acceptance Criteria (from spec) verified as OK.

## Risks and Rollback
- Risk A → Rollback B
```

## Stage 4 — Step-by-Step Development Loop
**Goal:** Commit and test incrementally; after each PR, the app works and can be verified.

### Best Practices
- One plan step = one PR (small and focused).
- Every PR must include:
    - “How to test” section (copied from the plan),
    - clear change summary,
    - link to the relevant specification.

### PR Checklist
- [ ] Matches corresponding step in `docs/plans/...`
- [ ] Unit/functional tests updated or added
- [ ] “How to test” verified locally
- [ ] No breaking changes without versioning contracts

### Template: Specification (MD)
```markdown
```

## Stage 5 — Iterations and Fixes
**Goal:** Close gaps, improve code quality, and add missing tests efficiently.

### Steps
Based on this code and implementation plan, propose a set of unit and functional tests
that cover the acceptance criteria.
For each test, include: case, setup, execution, and assertions.
Focus on simple, stable tests and include negative scenarios.

### Definition of Done
- [ ] Flaky tests eliminated or tagged with @flaky and a fix plan.
- [ ] Key paths are covered (pragmatically, not blindly chasing coverage).
- [ ] CI green, PR merged.

## Stage 6 — Closure & Knowledge Preservation
**Goal:** Keep documentation consistent and lessons learned recorded.

### Steps

### Definition of Done
- [ ] Update the specification with a “Differences vs Plan / Lessons learned” section.
- [ ] Update ADRs if any architectural decisions changed.
- [ ] Add a short note to README or CHANGELOG.
- [ ] Mark the issue/ticket as “Done” with links to PRs/commits.