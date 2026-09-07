# git-servers

- [GitLab](./gitlab/README.md)
- [Gitea](./gitea/README.md)

## Docker Compose

### Up

```shell
docker \
    compose \
    --progress plain \
    --file $(pwd)/docker-compose.yml \
    --project-name git-servers-evaluation \
    up \
    --remove-orphans \
    --detach
```

### Logs

```shell
docker \
    compose \
    --progress plain \
    --file $(pwd)/docker-compose.yml \
    --project-name git-servers-evaluation \
    logs \
    --follow
```

### Down

```shell
docker \
    compose \
    --progress plain \
    --file $(pwd)/docker-compose.yml \
    --project-name git-servers-evaluation \
    down
```

## Reset Data (`.volumes`)

```shell
sudo git clean -X --force --dry-run ./.volumes
```
