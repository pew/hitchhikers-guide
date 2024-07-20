---
date created: Wednesday, May 8th 2019, 7:14:43 pm
date modified: Saturday, July 20th 2024, 11:12:42 am
tags:
  - jq
  - json
---

# jq

* [jq is like sed for JSON data](https://stedolan.github.io/jq/)

## add or modify json key/value

let's say you want to add `"apitoken": "top-secret"` within `clodflare`.

example `cf.json` test file:

```json
{
  "cloudflare": {
    "TYPE": "CLOUDFLAREAPI",
    "accountid": "foobar"
  }
}
```

do this:

```shell
jq '.cloudflare.apitoken = "top-secret"' cf.json | sponge cf.json
```

with `sponge` the file will be written to disk and updated.

## delete key/value from json file

assume you want to delete the `apitoken` field from `cf.json`, do this:

```shell
jq 'del(.cloudflare.apitoken)' cf.json | sponge cf.json
```

## get multiple items

just comma separate what you want

```
bw list items --search zoho|jq '.[].login.username, .[].login.password'
```

## get raw output

... instead of JSON strings for example

```
-r               output raw strings, not JSON texts;
```

```
jq -r '.[].login.username, .[].login.password'
```

## get the first element

```
jq .[0] file.json
```

## merge multiple json files

for example: fitbit export, separated by day but same format otherwise. I wanted one file out of 4 years of data:

```
jq -s . heart_rate*.json > ../heart_rate.json
```

or just use **flatten** like this:

```
jq -c --slurp 'flatten' steps-*.json > ../steps.json
```

## pretty print json

```
your-json | jq
```

or:

```
jq . file.json
```

## you might not need `jq`

```
curl -sS https://abc.json | python -m json.tool
```
