# Module 04 — Specialist agents

## Goal

Delegate independent work while keeping ownership, review, and decisions visible.

## Practice

Define three roles:

- **Explorer:** maps the code and reports evidence without changing files.
- **Builder:** implements an approved, limited plan.
- **Reviewer:** checks the diff against requirements and tests.

Give each role a distinct handoff. For example, the explorer returns file paths and unanswered questions; the builder returns changed files and test output; the reviewer returns findings ordered by severity.

## Guardrail

Do not delegate two agents to edit the same files at once. Split work by boundary, then integrate deliberately.

## Next step

Add a source-of-truth integration only where it reduces uncertainty.
