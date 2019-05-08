# jq

* [jq is like sed for JSON data](https://stedolan.github.io/jq/)

## you might not need `jq`

```
curl -sS https://abc.json | python -m json.tool
```

## pretty print json

```
your-json | jq
```

or:

```
jq . file.json
```

## get the first element

```
jq .[0] file.json
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

## merge multiple json files

for example: fitbit export, separated by day but same format otherwise. I wanted one file out of 4 years of data:

```
jq -s . heart_rate*.json > ../heart_rate.json
```

or just use **flatten** like this:

```
jq -c --slurp 'flatten' steps-*.json > ../steps.json
```
