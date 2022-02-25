# gh - github cli

## removed starred repo

turns out, you can't unstar a repo on the web which was taken down by a DMCA request

```
gh api -X DELETE user/starred/username/repo
```