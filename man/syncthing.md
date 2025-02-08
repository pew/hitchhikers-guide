---
date created: Saturday, February 8th 2025, 9:52:40 am
date modified: Saturday, February 8th 2025, 9:57:06 am
tags: 
---

# syncthing

## get folder label and id

this will create an output like this: `my-folder: foo-id`

```shell
curl -s -H "Authorization: Bearer your-api-key-here" https://syncthing.example.com/rest/config | jq -r '.folders[] | "\(.label): \(.id)"'
```

## pause / resume folder sync

I use this with home-assistant to pause/resume folder syncing to avoid starting up my NAS drives when syncthing does a rescan. Replace `your-folderID` at the end of the url with the ID of your folder (see [get folder label and id](#get%20folder%20label%20and%20id))

**pause syncthing:**

```shell
curl -s -H "Authorization: Bearer your-api-key-here" -H "content-type: application/json" -X PATCH -d '{"paused": true}' https://syncthing.example.com/rest/config/folders/your-folderID
```

**resume syncthing:**

```shell
curl -s -H "Authorization: Bearer your-api-key-here" -H "content-type: application/json" -X PATCH -d '{"paused": false}' https://syncthing.example.com/rest/config/folders/your-folderID
```
