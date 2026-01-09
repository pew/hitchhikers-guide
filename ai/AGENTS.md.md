---
date created: Friday, January 9th 2026, 10:52:32 am
date modified: Friday, January 9th 2026, 10:56:06 am
tags:
  - llm
  - ai
---

# AGENTS.md

- see also the *official* [agents.md website](https://agents.md)

the `AGENTS.md` file below is used with the [superpowers proejct](https://github.com/obra/superpowers), and inspired [from this one, too](https://github.com/steipete/agent-scripts/)

```
## Superpowers System

<EXTREMELY_IMPORTANT>
You have superpowers. Superpowers teach you new skills and capabilities.

**Critical Rules:**
- Before ANY task, review the skills list (shown below)
- If a relevant skill exists, you MUST use it
- Announce: "I've read the [Skill Name] skill and I'm using it to [purpose]"
- Skills with checklists require `update_plan` todos for each item
- NEVER skip mandatory workflows (brainstorming before coding, TDD, systematic debugging). Unless explicitly told otherwise by the user.

IF A SKILL APPLIES TO YOUR TASK, YOU DO NOT HAVE A CHOICE. YOU MUST USE IT.
</EXTREMELY_IMPORTANT>

## Core Directives

- Use repo-local AGENTS.md / CONTRIBUTING / README when more specific.
- This file applies when no more specific instruction exists.
- You are working with an expert software engineer. Execute changes with precision and systematic verification.
- Follow SOLID, KISS, and YAGNI principles in all implementations.
- Trace complete data flow from source to destination. Never assume implementation details.
- Read file contents before any modification. Parse actual structure, not assumed structure.
- Never use placeholder code. Every function, import, and variable must be complete and functional.
- Preserve all existing functionality during refactoring. Maintain error handling, logging, and comments.
- When errors occur, read the exact error output. Trace the failure point. Do not guess causes.
- Check file paths and directory existence before operations. Create required directories.
- For multi-file changes, update all imports, exports, and references across the entire dependency graph.
- Test edge cases and boundary conditions after changes.
- Verify dependencies within the codebase. Update all files impacted by changes.

## Critical Thinking

- Fix root cause (not band-aid).
- Unsure: read more code; if still stuck, ask w/ short options.
- Conflicts: call out; pick safer path.
- Unrecognized changes: assume other agent; keep going; focus your changes. If it causes issues, stop + ask user.

## Documentation & Research

- Search current documentation before implementing any external library or API.
- Use web search for real-time data access and verification.
- Verify syntax and methods against latest version documentation, not training data.
- When uncertain about current best practices or deprecations, research before implementing.
```
