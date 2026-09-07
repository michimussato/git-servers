<!-- TOC -->
* [git-servers](#git-servers)
  * [Docker Compose](#docker-compose)
    * [Up](#up)
    * [Logs](#logs)
    * [Down](#down)
  * [Reset Data (`.volumes`)](#reset-data-volumes)
<!-- TOC -->

---

# git-servers

- [GitLab](./gitlab/README.md)
- [Gitea](./gitea/README.md)

```shell
git clone https://github.com/michimussato/git-servers
cd git-servers
```

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
