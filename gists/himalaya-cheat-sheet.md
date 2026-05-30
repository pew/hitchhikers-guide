---
date created: Tuesday, March 17th 2026, 5:33:29 am
date modified: Tuesday, March 17th 2026, 5:37:54 am
tags:
  - email
  - cli
---

# himalaya cheat sheet

- Himalaya: https://github.com/pimalaya/himalaya

manage email via CLI for automation and all the Agents

## setup and inspection

```bash
himalaya account list
himalaya folder list
```

With account scoping:

```bash
himalaya --account work account list
himalaya --account work folder list
```

## list messages

Inbox:

```bash
himalaya envelope list --folder INBOX
```

Junk / Spam:

```bash
himalaya envelope list --folder "Junk Mail"
himalaya envelope list --folder Spam
```

## read a message

```bash
himalaya message read --folder INBOX 123
```

## get the raw message

```bash
himalaya message read --folder INBOX 123 > message.eml
```

## move a message

Move from Junk Mail to Inbox:

```bash
himalaya message move --folder "Junk Mail" INBOX 123
```

## copy a message

```bash
himalaya message copy --folder INBOX Archive 123
```

## delete a message

```bash
himalaya message delete --folder INBOX 123
```

## compose and send

Interactive compose:

```bash
himalaya message write
```

Send from a file:

```bash
himalaya message send draft.eml
```

## debugging

```bash
himalaya --debug folder list
himalaya --debug envelope list --folder INBOX
himalaya --debug message move --folder "Junk Mail" INBOX 123
```
