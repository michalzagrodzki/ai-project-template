# Documentation Templates — README

This folder contains reusable templates for consistent project documentation.
They are designed to work together through all phases of your development process — from feature ideation to production deployment.

**Location:** `docs/_templates/`

---

## 📘 1. spec-template.md — Feature Specification

### Purpose

Defines *what* is to be built and *why*. Used before implementation to clarify scope, context, and goals.

### When to Use

* At the start of any new feature or system change
* Before AI-assisted planning or code generation (e.g., Claude, ChatGPT)

### Key Sections

* **Context:** Why this feature exists
* **Goal:** Expected measurable outcomes
* **Scope:** What is and isn’t included
* **Architecture:** Conceptual or high-level design
* **Integration Points:** Affected systems, APIs, or files
* **Acceptance Criteria:** Clear, testable outcomes

### Output

`docs/specs/YYYY-MM-DD-feature-name.md`

---

## 🧩 2. plan-template.md — Implementation Plan

### Purpose

Defines *how* to implement a feature in small, testable increments.
Ensures each step keeps the app working and testable.

### When to Use

* After the specification has been reviewed and approved
* Before writing the first line of implementation code

### Key Sections

* **Purpose:** Why this plan exists
* **Overview:** Guiding approach
* **Step-by-Step Plan:** Each step includes changes and testing
* **Rollback Plan:** Safe revert path
* **Definition of Done:** Final criteria for completion
* **Post-Implementation Validation:** Verification in CI/CD or runtime

### Output

`docs/plans/YYYY-MM-DD-feature-name.md`

---

## 🏗️ 3. adr-template.md — Architectural Decision Record

### Purpose

Captures *why* a specific technical or architectural decision was made.
Documents context, alternatives, and implications for future reference.

### When to Use

* When introducing new technologies, frameworks, or infrastructure
* When rejecting an alternative with long-term implications
* When replacing or superseding an earlier decision

### Key Sections

* **Context:** Problem and background
* **Decision:** Clear final choice
* **Alternatives Considered:** Pros and cons of each option
* **Consequences:** Positive and negative impacts
* **Implementation Notes:** Required setup/configuration
* **Rollback / Supersession Plan:** Future-proof exit strategy

### Output

`docs/adr/ADR-###-decision-title.md`

---

## 🔁 Recommended Workflow

1. **Start with `spec-template.md`** — describe context, goal, and criteria.
2. **Validate with AI (Claude, ChatGPT)** — gather clarifying questions.
3. **Generate `plan-template.md`** — create incremental, testable steps.
4. **Implement and test step-by-step** — ensure every commit works.
5. **Document key decisions using `adr-template.md`.**
6. **Keep everything linked** — each plan references its spec, and ADRs reference both.

---

## 📂 Folder Structure Example

```
docs/
  _templates/
    spec-template.md
    plan-template.md
    adr-template.md
    README.md
  specs/
    2025-10-29-user-session-persistence.md
  plans/
    2025-10-29-user-session-persistence.md
  adr/
    ADR-001-redis-session-storage.md
```

---

## ✅ Tips for Effective Use

* Keep each document concise and focused.
* Link files using relative paths for traceability.
* Always version ADRs (do not overwrite old ones).
* Encourage every contributor to follow the same format.
* Treat documentation as part of the deliverable — not an afterthought.

---

**Authoring tools:** Optimized for AI-assisted workflows with `give-me-markdown.com`, Claude, or ChatGPT.
**Goal:** Clarity, reproducibility, and traceability in every project stage.
