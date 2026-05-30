---
title: vscode snippets
tags:
  - vscode
date created: 2022-11-15
---

# vscode snippets

you can create [snippets in vscode](https://code.visualstudio.com/docs/editor/userdefinedsnippets#_create-your-own-snippets) and insert them into your code.

with `cmd+shift+p` you can easily create and insert snippets. If everything goes according to plan, I'll put some snippets here…

there's a handy web app to help you generate snippets: [snippets generator](https://snippet-generator.app/)

## YAML front matter

this will just create a yaml front matter header with a few fields: title, tags and date created.

```
{
	"YAML front matter": {
		"prefix": "",
		"body": [
			"---",
			"title: ",
			"tags:",
			"  - ",
			"date created: ${CURRENT_YEAR}-${CURRENT_MONTH}-${CURRENT_DATE}",
			"---"
		],
		"description": "YAML front matter"
	}
}
```
