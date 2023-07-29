---
date created: Saturday, July 29th 2023, 10:19:37 am
date modified: Saturday, July 29th 2023, 10:28:26 am
tags:
  - linux
  - raid
  - megacli
---

# MegaCli64

- [MegaCLI cheat sheet](https://www.broadcom.com/support/knowledgebase/1211161498596/megacli-cheat-sheet--live-examples)

## listing all drives

```
MegaCli64 -PDList -aALL
```

## adapter information

```
MegaCli64 -AdpAllInfo -aALL
```

## virtual drive / adapter information

```
MegaCli64 -LDInfo -Lall -aALL
```

## battery backup unit (bbu) status

```
MegaCli64 -AdpBbuCmd -aALL
```
