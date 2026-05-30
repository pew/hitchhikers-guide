---
date created: Sunday, June 29th 2025, 9:30:25 am
date modified: Sunday, June 29th 2025, 9:31:09 am
tags:
  - testing
  - playwright
---

# playwright

## run a single test

with the `--grep` flag you can just execute a single test:

```shell
npx playwright test e2e/myapp.spec.ts --project=chromium --grep "should create a new note and display it"
```
