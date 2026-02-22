---
date created: Sunday, February 22nd 2026, 8:45:32 am
date modified: Sunday, February 22nd 2026, 8:49:06 am
tags:
  - goodreads
---

# extract goodreads want to read list

you need to request an archive of your data from goodreads.com, after a day or two they'll send an email with a zip file full of zip files.

1. extract the `activity.zip`, you'll then get an `activity.json` file

this json file has - I guess - all your goodreads activity stored with different activity types, for example:

```
"activity_type": "BookStatusReading"
"activity_type": "BookStatusWantToRead"
```

you can use something like [jq](/man/jq/) to extract the data.

## list all "Want to Read" books

```shell
jq -r '
  [ .[]
    | select(has("activities"))
    | .activities[]
    | select(.activity_type == "BookStatusWantToRead")
    | .product
  ]
  | unique
  | sort
  | .[]
' activity.json
```
