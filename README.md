# Agentic Engineering Workshop

April 10, 2026, by Ludvig Renbo Olsen, Mathilde Hartvig Diekema, and Codex.
---

This repository contains a good initial project structure for working with agents such as codex and claude code. The outer layer describes the structure and the workshop tasks, while the content in `project_structure/` is ready to be copied to your own project.

See the `DEMO.md` file for steps to take to get up and running. The rest of this file describes the `project_structure/` contents.

## What is here

- `WORKSHOP_BEST_PRACTICES.md`
  A readable guide to effective agent workflows, planning, verification, and shared instructions.
- `project_structure/`
  A Python-focused starter template meant to be copied into a fresh repo after `uv init`.

## What the template includes

`project_structure/` is the product. It is meant to become the starting point of a new repo, not just describe one.

```text
project_structure/
├── AGENTS.md
├── CLAUDE.md
├── README.md
├── docs
│   ├── CODE_REVIEW.md
│   ├── PROMPT_EXAMPLES.md
│   ├── TESTING.md
│   ├── plans
│   │   └── README.md
│   ├── research
│   │   └── README.md
│   ├── resources
│   │   └── README.md
│   └── specs
│       ├── README.md
│       └── SPEC_TEMPLATE.md
├── src
│   └── your_project
│       └── __init__.py
└── tests
    └── test_smoke.py
```

- `README.md`
  A minimal project README that can stay in the new repo and be edited into the real one.
- `AGENTS.md`
  Shared repo instructions for coding agents: core rules, commands, and references.
- `CLAUDE.md`
  Claude Code entry point. It stays small and points to `AGENTS.md`.
- `docs/specs/`
  Project and feature specs. This is where larger work gets scoped before implementation.
- `docs/plans/`
  Execution plans, task breakdowns, status notes, and hand-over docs for ongoing work.
- `docs/research/`
  Longer research write-ups, such as paper summaries, tool comparisons, or API deep dives.
- `docs/resources/`
  Source material copied into the repo, such as PDFs, manuals, articles, or other reference documents.
- `docs/TESTING.md`
  Testing expectations and verification guidance.
- `docs/CODE_REVIEW.md`
  Review priorities and checklist.
- `docs/PROMPT_EXAMPLES.md`
  Reusable prompts for explore, plan, implement, and review workflows.
- `src/your_project/`
  Placeholder Python package location for application code.
- `tests/`
  A minimal `pytest` starting point.

## Suggested flow

1. Create a fresh repo.
2. Run `uv init`.
3. Add development tools such as `pytest`, `ruff`, and `ty`.
4. Copy the contents of `project_structure/` into the new repo.
5. Rename `src/your_project/` and update the placeholder code and tests.

The intended Python default is:

- `pytest` for tests
- `ruff` for linting and formatting
- `ty` for type checking

The template encourages typed Python for new and modified code, small verifiable changes, and keeping specs, plans, research notes, and source materials organized enough that either a human or an agent can resume work later.
