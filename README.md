<!-- TOC -->
* [git-servers](#git-servers)
  * [Requirements](#requirements)
  * [Clone Repository](#clone-repository)
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

## Requirements

- [Docker](https://docs.docker.com/engine/install/#installation-procedures-for-supported-platforms)

## Clone Repository

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
