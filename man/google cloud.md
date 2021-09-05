# google cloud

all the things. or none.

## google cloud container registry / artifact repositories

the current google cloud registry of the day is called artifacts.

### create docker repository

```
gcloud artifacts repositories create your-repo-name --repository-format=docker --description="Docker repository" --location=europe-west2
```

### authenticate docker against google cloud registry

```
gcloud auth configure-docker europe-west2-docker.pkg.dev
```

### tag your local image

tag your local image (`offlineimap:latest`) with the docker registry url you've got from google cloud

```
docker tag offlineimap:latest europe-west2-docker.pkg.dev/<project-id>/offlineimap/offlineimap:latest
```

### push image

```
docker push europe-west2-docker.pkg.dev/<project-id>/offlineimap/offlineimap
```
