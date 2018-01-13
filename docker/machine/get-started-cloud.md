---
description: Using Docker Machine to provision hosts on cloud providers
keywords: docker, machine, amazonec2, azure, digitalocean, google, openstack, rackspace, softlayer, virtualbox, vmwarefusion, vmwarevcloudair, vmwarevsphere, exoscale
title: Use Docker Machine to provision hosts on cloud providers
---

> Try out Docker Cloud!
>
> We suggest using [Docker Cloud](https://cloud.docker.com/) as the
most up-to-date way to run Docker on your cloud providers. To get started, see
[Docker Cloud docs home page](/docker-cloud/index.md), [Docker Cloud Settings
and Docker ID](/docker-cloud/dockerid.md), and [Swarms in Docker Cloud
(Beta)](/docker-cloud/cloud-swarm/index.md). If you are running Edge channel
Docker for Mac or Windows, you can access your Docker Cloud account from those
Docker desktop applications. See Docker Cloud (Edge feature) on
[Mac](/docker-for-mac/index.md#docker-cloud-edge-feature) or
[Windows](/docker-for-windows/index.md#docker-cloud-edge-feature).
>
> Docker Machine will still work as described here, but Docker Cloud supercedes Machine for this purpose.
{: .important}

Docker Machine driver plugins are available for many cloud platforms, so you can
use Machine to provision cloud hosts. When you use Docker Machine for
provisioning, you create cloud hosts with Docker Engine installed on them.

You'll need to install and run Docker Machine, and create an account with the
cloud provider.

Then you provide account verification, security credentials, and configuration
options for the providers as flags to `docker-machine create`. The flags are
unique for each cloud-specific driver. For instance, to pass a Digital Ocean
access token you use the `--digitalocean-access-token` flag. Take a look at the
examples below for Digital Ocean and AWS.

## Examples

### Digital Ocean

For Digital Ocean, this command creates a Droplet (cloud host) called
"docker-sandbox".

```shell
$ docker-machine create --driver digitalocean --digitalocean-access-token xxxxx docker-sandbox
```

For a step-by-step guide on using Machine to create Docker hosts on Digital
Ocean, see the [Digital Ocean Example](examples/ocean.md).

### Amazon Web Services (AWS)

For AWS EC2, this command creates an instance called "aws-sandbox":

```shell
$ docker-machine create --driver amazonec2 --amazonec2-access-key AKI******* --amazonec2-secret-key 8T93C*******  aws-sandbox
```

For a step-by-step guide on using Machine to create Dockerized AWS instances,
see the [Amazon Web Services (AWS) example](examples/aws.md).

## The docker-machine create command

The `docker-machine create` command typically requires that you specify, at a
minimum:

* `--driver` - to indicate the provider on which to create the
machine (VirtualBox, DigitalOcean, AWS, and so on)

* Account verification and security credentials (for cloud providers),
specific to the cloud service you are using

* `<machine>` - name of the host you want to create

For convenience, `docker-machine` will use sensible defaults for choosing
settings such as the image that the server is based on, but you override the
defaults using the respective flags (e.g. `--digitalocean-image`). This is
useful if, for example, you want to create a cloud server with a lot of memory
and CPUs (by default `docker-machine` creates a small server).

For a full list of the flags/settings available and their defaults, see the
output of `docker-machine create -h` at the command line, the
[create](/machine/reference/create/){: target="_blank" class="_" } command in
the Machine [command line reference](/machine/reference/index.md){:
target="_blank" class="_" }, and [driver options and operating system
defaults](/machine/drivers/os-base/){: target="_blank" class="_" } in the
Machine driver reference.

## Drivers for cloud providers

When you install Docker Machine, you get a set of drivers for various cloud
providers (like Amazon Web Services, Digital Ocean, or Microsoft Azure) and
local providers (like Oracle VirtualBox, VMWare Fusion, or Microsoft Hyper-V).

See [Docker Machine driver reference](/machine/drivers/index.md){:
target="_blank" class="_"} for details on the drivers, including required flags
and configuration options (which vary by provider).

## 3rd-party driver plugins

Several Docker Machine driver plugins for use with other cloud platforms are
available from 3rd party contributors. These are use-at-your-own-risk plugins,
not maintained by or formally associated with Docker.

See [Available driver
plugins](https://github.com/docker/docker.github.io/blob/master/machine/AVAILABLE_DRIVER_PLUGINS.md){:
target="_blank" class="_"}.

## Add a host without a driver

You can register an already existing docker host by passing the daemon url. With that, you can have the same workflow as on a host provisioned by docker-machine.

    $ docker-machine create --driver none --url=tcp://50.134.234.20:2376 custombox
    $ docker-machine ls
    NAME        ACTIVE   DRIVER    STATE     URL
    custombox   *        none      Running   tcp://50.134.234.20:2376

## Use Machine to provision Docker Swarm clusters

> Swarm mode supercedes Docker Machine provisioning of swarm clusters
>
> In previous releases, Docker Machine was used to provision swarm
clusters, but this is legacy. [Swarm mode](/engine/swarm/index.md), built
into Docker Engine, supercedes Machine provisioning of swarm clusters. The
topics below show you how to get started with the new swarm mode.
{: .important}

You can use Docker Machine to create local virtual hosts on which to deploy
and test [swarm mode](/engine/swarm/index.md) clusters.

Good places to start working with Docker Machine and swarm mode are these
tutorials:

* [Get started with Docker](/get-started/index.md)

* [Getting started with swarm mode](/engine/swarm/swarm-tutorial/index.md)


## Where to go next
-   Example: Provision Dockerized [Digital Ocean Droplets](examples/ocean.md)
-   Example: Provision Dockerized [AWS EC2 Instances](examples/aws.md)
-   [Understand Machine concepts](concepts.md)
-   [Docker Machine driver reference](drivers/index.md)
-   [Docker Machine subcommand reference](reference/index.md)
-   [Provision a Docker Swarm cluster with Docker Machine](/swarm/provision-with-machine.md)
