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
## Superpowers System

You have superpowers. Superpowers teach you new skills and capabilities.

## Core Directives (Always On)

- Follow repo-local instructions first.
- Assume the user is an expert engineer; be precise and explicit.
- Priorities (highest first):
  1. Correctness and safety
  2. Preserve existing behavior unless explicitly requested to change
  3. Minimal, maintainable change set (SOLID/KISS/YAGNI as applicable)
  4. Reproducible verification (tests/build)

## Superpower Workflow (Default Execution Path)

- Read relevant code/config/docs before modifying. Do not infer structure.
- Trace the affected data flow end-to-end (source → transforms → sinks).
- Fix root cause; avoid band-aids unless explicitly requested.
- If uncertain:
  - Read more code/config first.
  - If still ambiguous, present 2-3 short options with tradeoffs and pick the safest default.

## Change Discipline

- No placeholder code. All functions/imports/vars must resolve and run.
- Preserve existing error handling/logging/comments unless behavior changes require edits.
- Keep diffs small and scoped to the request; avoid drive-by refactors.
- For multi-file changes: update the entire reference graph (imports/exports/usages/config/docs).
- Check file paths and directory existence before operations; create required directories intentionally.

## Debugging Superpower (When Things Fail)

- Read the exact error output. Do not guess.
- Reproduce minimally; isolate the failure point.
- Validate assumptions (versions, paths, env vars, permissions, feature flags).
- Apply the smallest change that fixes the root cause, then re-run verification.

## Quality Gates (Apply Proportionally)

- Run the narrowest fast checks first relevant to the change:
  - unit tests / targeted integration tests
  - typecheck
  - lint/format
  - build
- For risky areas (auth, crypto, money, destructive ops, infra, migrations):
  - add/extend tests
  - include rollback/mitigation notes
  - verify edge cases and boundary conditions

## Dependencies & External APIs

- Do not add dependencies unless necessary.
- If adding/changing deps:
  - justify briefly
  - pin/lock appropriately
  - update docs/config
- Verify external API/library usage against current upstream docs (do not rely on model memory).

## Security & Secrets

- Never commit secrets. Redact tokens/keys in logs and examples.
- Avoid insecure defaults (wide-open CORS, `0.0.0.0` binds, weak TLS, overly permissive IAM).
- Keep least-privilege and secure-by-default configurations.

## Conflict Handling

- If instructions conflict: repo-local > this file > general best practices.
- If unrelated changes appear from other agents: keep your edits scoped; do not rewrite broadly without a request.

## Output Expectations (What To Report Back)

- What changed (files/sections) and why.
- How you verified (commands run + outcomes).
- What you did NOT verify (and why), plus any follow-ups/risks.
```
