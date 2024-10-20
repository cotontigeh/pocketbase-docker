# Pocketbase docker 
Just set of dockerfiles for [pocketbase](https://github.com/pocketbase/pocketbase) starting from 0.22 
You can find hosted image on [dockerhub](https://hub.docker.com/r/cotontigeh/pocketbase/tags)

# Dev commands

## Build image 
replace `latest` by any version you want
```bash
docker build -f dockerfiles/0.22-alpine3.20.dockerfile . -t your_namespace/pocketbase:latest
```

### With args
```bash
docker build -f dockerfiles/0.22-alpine3.20.dockerfile . --build-arg MIGRATIONS_DIR=./pb_migrations --build-arg HOOKS_DIR=./pb_hooks -t your_namespace/pocketbase:latest
```

- **MIGRATIONS_DIR** pocketbase migration directory, see [the doc](https://pocketbase.io/docs/going-to-production/#using-docker)
- **HOOKS_DIR** pocketbase hooks directory, see [the doc](https://pocketbase.io/docs/going-to-production/#using-docker)

## Start image 
```bash
docker run -v ./pb_data:/pb/pb_data -p 8080:8080 -d your_namespace/pocketbase:latest
```

### Start image with shared volumes
```bash
docker run -v ./pb_data:/pb/pb_data -v ./pb_hooks:/pb/pb_hooks -v ./pb_migrations:/pb/pb_migrations -p 8080:8080 -d your_namespace/pocketbase:latest
```

## Publish to dockerhub
```bash
docker push your_namespace/pocketbase:0.22-alpine3.20 
```

