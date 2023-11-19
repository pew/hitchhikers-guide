---
date created: Thursday, November 17th 2022, 4:57:39 am
date modified: Sunday, November 19th 2023, 6:26:22 pm
tags:
  - sqlite
---

# sqlite

## show headers

```
.headers ON
```

## display columns

```
.mode columns
```

## import csv

```
sqlite3 db.sqlite
.mode csv
.import filename.csv table
```

## export sqlite as json

```
sqlite3 sqlite.db '.mode json' '.once data.json' "select * from images where user_id=1"
```
