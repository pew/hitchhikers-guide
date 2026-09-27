---
date created: Sunday, September 27th 2026, 12:25:58 pm
date modified: Sunday, September 27th 2026, 12:38:43 pm
tags:
  - encryption
  - security
  - git
---

# sops

SOPS encrypts secret values in configuration files so you can safely store and version them in git etc.

## convert / encrypt an `.env` file

assuming you already have a `.env` file in a project with some api keys/values stored, this way you can convert this using `sops` into a `.env.sops.json` file and add that to git:

```shell
sops encrypt \
  --age 'age1YOUR_PUBLIC_RECIPIENT'
  --input-type dotenv \
  --output-type json \
  --output .env.sops.json \
  .env
```

if you have a `.sops.yaml` with a creation rule which perhaps already defines the age recipient, you can convert a file like so:

```shell
sops encrypt \
  --filename-override .env.sops.json \
  --input-type dotenv \
  --output-type json \
  --output .env.sops.json \
  .env
```

the `.sops.yaml` looks like so to match the above `filename-override`:

```yaml
creation_rules:
  - path_regex: '\.sops\.env\.json$'
    age: >-
      age1YOUR_PUBLIC_RECIPIENT
```

## add / edit / update entries in `.env.sops.json`

```shell
sops edit .env.sops.json
```
