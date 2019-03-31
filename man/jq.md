# jq

* [jq is like sed for JSON data](https://stedolan.github.io/jq/)

# pretty print json

```
your-json | jq
```

or:

```
jq . file.json
```

# get the first element

```
jq .[0] file.json
```

# get multiple items

just comma separate what you want

```
bw list items --search zoho|jq '.[].login.username, .[].login.password'
```

# get raw output

... instead of JSON strings for example

```
-r               output raw strings, not JSON texts;
```

```
jq -r '.[].login.username, .[].login.password'
```
