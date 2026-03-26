---
name: project-execution-protocol
description: Use when implementing, debugging, refactoring, code reviewing, or onboarding in any repository and strict scope control, minimal diffs, context efficiency, adaptive reasoning depth, and concise Russian user-facing updates are required.
---

# Project Execution Protocol

This skill defines a default execution mode for real project work.
It prioritizes correctness, project integrity, and context efficiency.

This skill does not replace project rules in `AGENTS.md`.
Use it as day-to-day operating mode within those rules.

## Core Principles

1. Keep scope narrow by default.
2. Expand context only when evidence is insufficient.
3. Prefer minimal safe diffs over broad rewrites.
4. Preserve architecture, naming, and patterns unless refactoring is explicitly requested.
5. Reuse existing solutions before adding new abstractions.
6. Token efficiency matters, but not at the cost of correctness or safety.

## Language and Communication Policy

1. Think in English for planning, debugging, and technical reasoning.
2. Keep user-facing summaries and progress updates in concise Russian.
3. Avoid long explanations unless the user asks for detail.
4. Report risks, blockers, and uncertainty explicitly.

## Context Discipline

1. Start with only required context: `AGENTS.md`, `CURRENT_STATUS.md` (if present), user-mentioned files, direct neighbors.
2. Do not scan the entire repo by default.
3. Do not repeat unchanged context or restate the full task when already clear.
4. Re-read context only when requirements changed, assumptions are stale, or correctness depends on exact details.

## Task and Reasoning Calibration

1. Keep one primary goal per iteration.
2. Do not mix unrelated implementation, refactoring, research, and debugging unless requested.
3. Use shallow reasoning for tiny and obvious edits.
4. Use medium reasoning for multi-file logic and non-trivial feature work.
5. Use deep reasoning for architecture, unclear bugs, performance issues, and high-risk changes.

## Workflow

### Step 1: Task Intake Card

Before editing, form a compact internal card:

- Task
- Goal
- Scope boundary
- Constraints
- Relevant files
- Unknowns
- Minimal next step

If the request is ambiguous, clarify only the minimum blocking unknown.

### Step 2: Scope Expansion Ladder

Use these levels in order:

1. Direct scope (explicit file/module)
2. Immediate neighbors (imports/helpers/consumers)
3. Flow verification (caller/state/wiring)
4. Broad search only if levels 1-3 are insufficient

### Step 3: Execution Guardrails

1. Implement the smallest correct change.
2. Preserve public behavior unless change is explicitly required.
3. Avoid opportunistic cleanup.
4. Keep module/file structure stable unless necessary.
5. Escalate for user confirmation before major changes to API contracts, data models, auth/authz, external integrations, or deployment model.

### Step 4: Verification Discipline

Run the smallest meaningful verification first, then expand as needed:

1. Affected unit tests
2. Related integration/e2e tests when relevant
3. Lint/typecheck for touched surfaces

If checks cannot run, state exactly what was not run and why.

### Step 5: Output Contract

Default to compact delivery:

- What was analyzed
- What changed
- Risks/blockers/open questions
- What to verify next

Do not replay long reasoning history.

## Thread Management

Keep each thread focused on one primary goal.
If the thread mixes unrelated goals and degrades accuracy, recommend a new thread with:

1. Brief reason in Russian
2. Suggested thread title
3. Starter prompt in Russian

Do not claim to create a new chat unless platform supports it.

## Handoff Template

After substantial work, provide:

```md
Done:
- ...

Changed files:
- ...

Current status:
- ...

Next step:
- ...

Risks/checks:
- ...
```

If `CURRENT_STATUS.md` exists, propose or apply a concise update.

## Anti-Patterns

Do not:

- read large repo areas without need
- broaden local fixes into refactors
- duplicate long rules already in `AGENTS.md`
- produce verbose narrative when concise structure is enough
- continue searching after sufficient evidence is found

## Quick Prompt Template

Use this when invoking the skill:

```text
Use project-execution-protocol.
Read: CURRENT_STATUS.md, <relevant files>
Task: <single concrete task>
Scope: <specific area only>
Constraints: minimal patch, no unrelated changes
Need: implement/fix + concise Russian summary + what to test
```
