---
description: Copy files among machines
keywords: machine, scp, subcommand
title: docker-machine scp
---

Copy files from your local host to a machine, from machine to machine, or from a
machine to your local host using `scp`.

The notation is `machinename:/path/to/files` for the arguments; in the host
machine's case, you don't have to specify the name, just the path.

## Example

Consider the following example:

```none
$ cat foo.txt
cat: foo.txt: No such file or directory
$ docker-machine ssh dev pwd
/home/docker
$ docker-machine ssh dev 'echo A file created remotely! >foo.txt'
$ docker-machine scp dev:/home/docker/foo.txt .
foo.txt                                                           100%   28     0.0KB/s   00:00
$ cat foo.txt
A file created remotely!
```

Just like how `scp` has a `-r` flag for copying files recursively,
`docker-machine` has a `-r` flag for this feature.

In the case of transferring files from machine to machine,
they go through the local host's filesystem first (using `scp`'s `-3` flag).

When transferring large files or updating directories with lots of files,
you can use the `-d` flag, which uses `rsync` to transfer deltas instead of
transferring all of the files.

When transferring directories and not just files, avoid rsync surprises
by using trailing slashes on both the source and destination. For example:

```none
$ mkdir -p bar
$ touch bar/baz
$ docker-machine scp -r -d bar/ dev:/home/docker/bar/
$ docker-machine ssh dev ls bar
baz
```

## Specifying file paths for remote deployments

When you copy files to a remote server with `docker-machine scp` for app
deployment, make sure `docker-compose` and the Docker daemon know how to find
them. You can specify absolute paths, e.g. `/home/myuser/workspace` in a
[Compose file](/compose/compose-file/index.md), which will be mounted into the
container at `/workspace`, from the absolute path on the remote host where the
Docker daemon is running. Local client paths (e.g., on your laptop) will not
work for daemons running on a remote machine, so avoid using relative paths.

For example, imagine you want to transfer your local directory
`/Users/londoncalling/webapp` to a remote machine and bind mount it into a
container on the remote host. (We'll suppose the remote user is `ubuntu`.) You
could do something like this:

```none
$ docker-machine scp -r /Users/londoncalling/webapp MACHINE-NAME:/home/ubuntu/webapp
```

Then write a docker-compose file that bind mounts it in:

```none
version: "3.1"
services:
  webapp:
    image: alpine
    command: cat /app/root.php
    volumes:
    - "/home/ubuntu/webapp:/app"
```

And we can try it out like so:

```none
$ eval $(docker-machine env MACHINE-NAME)
$ docker-compose run webapp

