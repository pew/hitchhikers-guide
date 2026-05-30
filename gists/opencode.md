---
date created: Sunday, May 3rd 2026, 6:00:00 pm
date modified: Sunday, May 3rd 2026, 5:42:30 pm
tags:
  - ai
  - cli
---

# opencode

a AI (coding) agent. for CLI, TUI, Web, and Desktop. This page focuses on **headless / non-interactive** usage without the TUI.

## one-off prompts

### basic usage

```shell
opencode run "explain this code"
```

### pipe content

```shell
cat main.ts | opencode run "refactor this to use async/await" -
```

### attach files

```shell
opencode run -f README.md -f src/main.ts "update the readme based on the code"
```

### specify a model

```shell
opencode run -m anthropic/claude-sonnet-4 "write tests for utils.ts"
```

### use a specific agent

```shell
opencode run --agent task "summarize the last 3 commits"
```

### json output (for scripting)

streams newline-delimited JSON events:

```shell
opencode run --format json "what is 2+2?"
```

### auto-approve permissions (dangerous!)

useful in CI or trusted scripts where you can't interact with permission prompts:

```shell
opencode run --dangerously-skip-permissions "run npm test"
```

### show thinking blocks

```shell
opencode run --thinking "solve this leetcode problem"
```

### continue a previous session

```shell
opencode run --continue "and now add error handling"
```

or continue a specific session:

```shell
opencode run --session ses_xxx "what was the next step?"
```

fork a session before continuing:

```shell
opencode run --session ses_xxx --fork "try a different approach"
```

### set a session title

```shell
opencode run --title "refactor auth" "clean up the login flow"
```

### run in a specific directory

```shell
opencode run --dir ~/projects/api "check for outdated dependencies"
```

## providers & auth

### list providers

```shell
opencode providers list
```

### log in to a provider

```shell
opencode providers login
```

### log out

```shell
opencode providers logout
```

## models

### list available models

```shell
opencode models
```

### list models for a specific provider

```shell
opencode models anthropic
```

### show model costs & metadata

```shell
opencode models --verbose
```

### refresh model cache

```shell
opencode models --refresh
```

## sessions

### list sessions

```shell
opencode session list
```

### delete a session

```shell
opencode session delete ses_xxx
```

## stats & export

### show token usage and costs

```shell
opencode stats
opencode stats --days 7
opencode stats --models
```

### export a session

```shell
opencode export ses_xxx > session.json
```

redact sensitive data:

```shell
opencode export ses_xxx --sanitize
```

## headless server

useful for running opencode as a background service or connecting from another machine:

### start server

```shell
opencode serve --port 4096
```

### attach to a running server

```shell
opencode attach http://localhost:4096
```

### run via remote server

```shell
opencode run --attach http://localhost:4096 "hello from the client"
```

## debugging

### show resolved config

```shell
opencode debug config
```

### show paths

```shell
opencode debug paths
```

### show startup timing

```shell
opencode debug startup
```

## misc

### upgrade

```shell
opencode upgrade
```

### shell completions

```shell
opencode completion bash
opencode completion zsh
opencode completion fish
```

### database tools

```shell
opencode db path
opencode db "SELECT * FROM messages LIMIT 5"
```

## global flags

- `-h, --help` — show help
- `-v, --version` — show version
- `--print-logs` — print logs to stderr
- `--log-level DEBUG|INFO|WARN|ERROR` — set log level
- `--pure` — run without external plugins
- `-m, --model provider/model` — model to use
- `--prompt <string>` — prompt to use
- `--agent <string>` — agent to use
