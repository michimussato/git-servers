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
    # `--pull always` to set pull policy to always
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
