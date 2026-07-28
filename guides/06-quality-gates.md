# Module 06 — Quality gates

## Goal

Make the useful checks automatic at the moment they can still change the result.

## Practice

Choose one gate for each stage:

- before an edit: confirm the plan and affected boundaries;
- after an edit: run formatter, linter, and targeted tests;
- before delivery: compare outcomes against the request and note remaining risk.

Prefer fast, specific checks. A ten-minute whole-project test suite is valuable, but it should not replace a focused test that catches the relevant failure quickly.

## Check

Every gate should have a clear pass/fail signal and an owner who decides what happens on failure.

## Next step

Bundle the steps into an installable team workflow.
