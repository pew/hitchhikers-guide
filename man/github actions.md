# GitHub actions

## local environment variables

set and get/use local environment variables within the workflow. let's say you want to run a curl command in GitHub actions to get a version number and use it later on.

the example below will get the latest version of syncthing and put it into the environment variable `SYNCTHING_VERSION`, it can then be read with: `${{ env.SYNCTION_VERSION }}`

```yaml
- name: get latest syncthing version
  run: |
    echo "SYNCTHING_VERSION=$(basename $(curl -fs -o/dev/null -w %{redirect_url} https://github.com/syncthing/syncthing/releases/latest))" >> $GITHUB_ENV
    
- name: build syncthing container
  uses: docker/build-push-action@v2
  with:
    context: dockerfiles/syncthing
    platforms: linux/amd64
    build-args: |
      SYNCTHING_SOURCE=${{ env.SYNCTHING_VERSION }}
    push: true
    tags: ghcr.io/user/container:latest
```