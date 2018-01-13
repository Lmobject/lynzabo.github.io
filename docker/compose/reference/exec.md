---
description: docker-compose exec
keywords: fig, composition, compose, docker, orchestration, cli, exec
title: docker-compose exec
notoc: true
---

```
Usage: exec [options] SERVICE COMMAND [ARGS...]

Options:
-d                Detached mode: Run command in the background.
--privileged      Give extended privileges to the process.
-u, --user USER   Run the command as this user.
-T                Disable pseudo-tty allocation. By default `docker-compose exec`
                  allocates a TTY.
--index=index     index of the container if there are multiple
                  instances of a service [default: 1]
```

This is equivalent of `docker exec`. With this subcommand you can run arbitrary
commands in your services. Commands are by default allocating a TTY, so you can
do e.g. `docker-compose exec web sh` to get an interactive prompt.
