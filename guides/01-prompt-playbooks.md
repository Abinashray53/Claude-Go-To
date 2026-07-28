# Module 01 — Prompt playbooks

## Goal

Move from a fresh request every time to a small collection of prompts that reliably start common work.

## Practice

Create a `prompts/` folder. Write one short prompt for each of these jobs:

1. Explain an unfamiliar part of the codebase.
2. Propose a minimal implementation plan before editing.
3. Review a changed file for edge cases and missing tests.

Each playbook should name the expected output. For example: “Return three risks, an implementation sequence, and the files likely to change.”

## Make it durable

Keep prompts narrow. A reusable prompt explains the role, the boundaries, and the response format; it does not try to predict every future task.

## Next step

When you can reuse a prompt twice without changing its structure, move on to project context.
