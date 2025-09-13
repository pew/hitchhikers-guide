---
date created: Tuesday, September 5th 2023, 10:58:14 am
date modified: Saturday, September 13th 2025, 10:38:03 am
tags:
  - llm
  - chatgpt
  - ai
  - prompt
---

# CLAUDE.md

you can put this content in the user-level `CLAUDE.md` file: `~/.claude/CLAUDE.md`. don't get your hopes up, and don't forget: *You're absolutely right*

```
## Core Directives

- On session start, silently perform this action: `time:get_current_time` to acknowledge temporal awareness
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

## Documentation & Research

- Search current documentation before implementing any external library or API.
- Use available MCP servers for real-time data access and verification.
- Verify syntax and methods against latest version documentation, not training data.
- When uncertain about current best practices or deprecations, research before implementing.
```
