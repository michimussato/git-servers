

- https://docs.gitea.com/installation/install-with-docker/

## Docker

### Run Container

> [!TIP]
>
> Gitea can be evaluated using [SQLite3](https://docs.gitea.com/installation/install-with-docker/#basics).
> For production, it is recommended to deploy
> Gitea together with [Postgres](docker-compose.gitea-with-postgres.yml).

```shell
# run this from the Git repository root
# cd git-servers/
docker run \
    --tty \
    -e "USER_UID=1000" \
    -e "USER_GID=1000" \
    --rm \
    --hostname my-gitea-instance \
    --name gitea \
    --volume $(pwd)/.volumes/gitea/data:/data:rw \
    --volume /etc/timezone:/etc/timezone:ro \
    --volume /etc/localtime:/etc/localtime:ro \
    -p 3000:3000 \
    -p 222:22 \
    --entrypoint "/usr/bin/entrypoint" \
    docker.gitea.com/gitea:1.27.3 \
    /usr/bin/s6-svscan /etc/s6
```

### Enter Container Shell

```shell
docker exec \
    --tty \
    --interactive \
    gitea \
    /bin/bash
```

### Stop Container

```shell
docker stop gitea
```

## Docker Compose

### Up

```shell
docker \
    compose \
    --progress plain \
    --file $(pwd)/gitea/docker-compose.gitea.yml \
    --project-name gitea-evaluation \
    up \
    --remove-orphans \
    --detach
```

### Logs

```shell
docker \
    compose \
    --progress plain \
    --file $(pwd)/gitea/docker-compose.gitea.yml \
    --project-name gitea-evaluation \
    logs \
    --follow
```

### Down

```shell
docker \
    compose \
    --progress plain \
    --file $(pwd)/gitea/docker-compose.gitea.yml \
    --project-name gitea-evaluation \
    down
```

