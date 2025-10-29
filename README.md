# Project Documentation Framework — Root README

This repository provides a **documentation framework** and reusable **AI-assisted development workflow** designed to make software delivery structured, iterative, and traceable.
It aligns human developers and AI tools (like ChatGPT or Claude Code) around a consistent set of Markdown-based artifacts.

---

## 🎯 Purpose

The goal of this framework is to ensure that every project, regardless of size or technology stack, maintains:

* Clear **problem definition** and **solution intent** (via specifications)
* Predictable **implementation progress** (via step-by-step plans)
* Documented **technical decisions** (via ADRs)
* Continuous validation and testability at every step

This approach is designed to mirror how a senior developer would guide a team — while enabling AI systems to participate effectively in planning, code review, and iteration.

---

## ⚡ Quick Start (10-Step Summary)

1. **Create a spec file** in `docs/specs/...` with examples and documentation links.
2. **(Optional)** Create an ADR in `docs/adr/...` if architectural implications exist.
3. **Send the spec to Claude or Codex** → get clarification questions and update it.
4. **Ask for a step-by-step implementation plan** with “How to test” after each step.
5. **Create a feature branch**: `feat/<short-description>`.
6. **Implement one plan step = one PR**, ensuring each step keeps the app functional.
7. **After each PR**: run local + CI tests to confirm stability.
8. **If something fails** — iterate with AI, refine code/tests, and document changes.
9. **When done**: update `README`, `CHANGELOG`, and ADRs.
10. **Run a short retrospective** to capture lessons learned and improve templates.

---

## 🧭 Guiding Principles

1. **Small, testable increments:** Every implementation step results in a working build.
2. **Documentation as a deliverable:** Specs, plans, and ADRs are part of the release lifecycle.
3. **Human + AI collaboration:** Documentation is structured so AI can ask clarifying questions and generate implementation blueprints.
4. **Traceability:** Every plan references a spec, and every ADR references both.
5. **Simplicity:** Markdown-only, portable across editors, and Git-native.

---

## 📂 Repository Structure

```
docs/
  _templates/               # Reusable templates for new features
    spec-template.md
    plan-template.md
    adr-template.md
    README.md               # Explains how to use templates

  specs/                    # Feature specifications (what/why)
    YYYY-MM-DD-feature-name.md

  plans/                    # Implementation plans (how)
    YYYY-MM-DD-feature-name.md

  adr/                      # Architectural Decision Records (why this way)
    ADR-###-decision-title.md
```

---

## 🧩 Core Documents

### 1. Specification (`specs/`)

Defines **what** needs to be built, **why**, and under what constraints.

* Written before implementation begins.
* Reviewed collaboratively with AI and team members.
* Serves as the foundation for an implementation plan.

### 2. Implementation Plan (`plans/`)

Defines **how** the feature will be built step-by-step.

* Each step keeps the application in a testable state.
* Includes explicit testing and rollback guidance.
* Links directly to its specification.

### 3. ADR (Architectural Decision Record) (`adr/`)

Captures **why** certain architectural or technical choices were made.

* Documents alternatives, tradeoffs, and consequences.
* Prevents knowledge loss over time.

---

## 🧠 Workflow Overview

1. **Start with a Specification** — describe the goal, context, and acceptance criteria.
2. **Validate with AI** — use Claude or ChatGPT to generate clarifying questions.
3. **Create an Implementation Plan** — each step is incremental and testable.
4. **Develop Iteratively** — one PR per step, always ending in a working build.
5. **Capture Decisions** — add ADRs for major architectural or design choices.
6. **Reflect and Improve** — update lessons learned and evolve templates.

---

## 🛠️ Recommended Tools

* **give-me-markdown.com** → for clean Markdown formatting.
* **Claude Code / ChatGPT / OpenAI Codex** → for AI-driven validation and code planning.
* **VS Code + Markdownlint** → for consistent style.
* **GitHub Actions / CI** → to ensure every plan step builds and passes tests.

---

## 🔗 Best Practices

* Each document is a living artifact — commit small, frequent updates.
* Always link related files (spec ↔ plan ↔ ADR).
* Use human-readable dates and IDs for traceability.
* Keep your specs conversational: write for both humans and AI assistants.

---

## 📜 License

This project is licensed under the **MIT License** — you are free to use, modify, and distribute it, provided that the original copyright notice and this permission notice are included in all copies or substantial portions of the Software.

---

> **Author:** Michal Zagrodzki
> **Version:** 1.0.0
> **Last Updated:** 2025-10-29

---

**In summary:** this repository provides a golden path for combining **human insight**, **AI collaboration**, and **structured documentation** — ensuring every project remains understandable, reproducible, and scalable from idea to production.
