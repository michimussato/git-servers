<!-- TOC -->
* [GitLab](#gitlab)
  * [Docker run](#docker-run)
<!-- TOC -->

---

# GitLab

- https://docs.gitlab.com/install/docker/installation/#install-gitlab-by-using-docker-compose
- [`GITLAB_OMNIBUS_CONFIG`](https://docs.gitlab.com/install/docker/configuration/#pre-configure-docker-container)
- [GitLab Image](https://hub.docker.com/r/gitlab/gitlab-ee)

> [!TIP]
> 
> Instead of configuring via `GITLAB_OMNIBUS_CONFIG`,
> simply edit the `static/etc/gitlab/gitlab.rb` file
> and bind mount it.

## Docker

### Run Container

```shell
# run this from the Git repository root
# cd git-servers/
docker run \
    --tty \
    --rm \
    --hostname my-gitlab-instance \
    --name gitlab \
    --volume $(pwd)/.volumes/gitlab/logs:/var/log/gitlab:rw \
    --volume $(pwd)/.volumes/gitlab/data:/var/opt/gitlab:rw \
    --volume $(pwd)/.volumes/gitlab/etc/:/etc/gitlab/:rw \
    --volume $(pwd)/gitlab/static/etc/gitlab/gitlab.rb:/etc/gitlab/gitlab.rb:ro \
    --shm-size 256m \
    -p 8929:8929 \
    -p 443:443 \
    -p 2424:22 \
    --entrypoint /bin/bash \
    gitlab/gitlab-ee:latest \
    /assets/init-container
```

### Enter Container Shell

```shell
docker exec \
    --tty \
    --interactive \
    gitlab \
    /bin/bash
```

### Stop Container

```shell
docker stop gitlab
```

## Docker Compose

### Up

```shell
docker \
    compose \
    --progress plain \
    --file $(pwd)/gitlab/docker-compose.gitlab.yml \
    --project-name gitlab-evaluation \
    up \
    --remove-orphans \
    --detach
```

### Logs

```shell
docker \
    compose \
    --progress plain \
    --file $(pwd)/gitlab/docker-compose.gitlab.yml \
    --project-name gitlab-evaluation \
    logs \
    --follow
```

### Down

```shell
docker \
    compose \
    --progress plain \
    --file $(pwd)/gitlab/docker-compose.gitlab.yml \
    --project-name gitlab-evaluation \
    down
```
