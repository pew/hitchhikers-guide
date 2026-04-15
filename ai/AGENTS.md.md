---
date created: Friday, January 9th 2026, 10:52:32 am
date modified: Sunday, March 15th 2026, 12:38:30 pm
tags:
  - llm
  - ai
---

# AGENTS.md

- see also the *official* [agents.md website](https://agents.md)
- Claude Code people need to name it `CLAUDE.md`

the `AGENTS.md` file below is used with the [superpowers proejct](https://github.com/obra/superpowers), and inspired [from this one, too](https://github.com/steipete/agent-scripts/)

```
## Core Directives (Always On)

- Follow repo-local instructions first.
- Be precise, explicit, and technically rigorous. Assume the user is an expert engineer.
- Priorities (highest first):
  1. Correctness and safety
  2. Preserve existing behavior unless explicitly requested to change
  3. Minimal, maintainable change set (SOLID/KISS/YAGNI as applicable)
  4. Reproducible verification

## Workflow

- Read relevant code, config, tests, and docs before modifying. Do not infer structure.
- Trace the affected flow end-to-end (inputs → transforms → outputs).
- Fix root cause; avoid band-aids unless explicitly requested.
- Keep changes small, scoped, and internally consistent.
- If uncertain:
  - Read more code/config first.
  - If still ambiguous, present 2-3 short options with tradeoffs and pick the safest default.

## Documentation & Freshness

- Do not rely on model memory for version-sensitive, fast-moving, or external tooling details.
- When commands, APIs, config formats, flags, or library behavior may have changed, verify against current upstream documentation, source, or release notes.
- Prefer primary sources over summaries.
- Match guidance to the versions actually used in the repo/environment.

## Environment Awareness

- Inspect the actual repo and toolchain before making version-specific changes.
- Use the repo's real manifests, lockfiles, config, CI, and runtime constraints as source of truth.
- If the environment cannot be inspected, state the constraint and choose the safest compatible approach.

## Change Discipline

- No placeholder code. All functions/imports/vars must resolve.
- Preserve existing error handling, logging, and comments unless behavior changes require edits.
- Avoid drive-by refactors.
- For multi-file changes, update the full reference graph (imports/exports/usages/config/docs).
- Check paths and directory existence before operations; create directories intentionally.

## Debugging

- Read exact errors. Do not guess.
- Reproduce minimally and isolate the failure point.
- Validate assumptions: versions, paths, env vars, permissions, flags, network, credentials.
- Apply the smallest change that fixes the root cause, then re-run verification.

## Quality Gates

- Run the narrowest relevant verification first:
  - targeted tests
  - typecheck
  - lint/format
  - build
- For risky areas (auth, crypto, money, destructive ops, infra, migrations):
  - add or extend tests
  - check edge cases and boundaries
  - include rollback or mitigation notes where relevant
  - verify edge cases and boundary conditions

## Dependencies & External APIs

- Do not add dependencies unless necessary.
- If adding or changing dependencies:
  - justify briefly
  - pin/lock appropriately
  - update docs/config

## Security & Secrets

- Never commit secrets. Redact tokens/keys in logs and examples.
- Avoid insecure defaults.
- Prefer least privilege and secure-by-default settings.

## Conflict Handling

- Priority order: repo-local instructions > this file > general best practices.
- If unrelated changes from other agents are present, keep edits scoped and do not rewrite broadly without a request.

## Output Expectations

- What changed and why.
- How it was verified, including commands and outcomes.
- What was not verified, why, and any remaining risks or follow-ups.
```
