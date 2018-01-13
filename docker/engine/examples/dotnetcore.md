---
description: Create a Docker image by layering your ASP.NET Core app on debian for Linux Containers or with Windows Nano Server containers using a Dockerfile.
keywords: dockerize, dockerizing, dotnet, .NET, Core, article, example, platform, installation, containers, images, image, dockerfile, build, asp.net, asp.net core
title: Dockerize a .NET Core application
---

## Introduction

This example demonstrates how to dockerize an ASP.NET Core application.

## Why build ASP.NET Core?

- [Open-source](https://github.com/aspnet/home)
- Develop and run your ASP.NET Core apps cross-platform on Windows, MacOS and
  Linux
- Great for modern cloud-based apps, such as web apps, IoT apps and mobile
  backends
- ASP.NET Core apps can run on [.NET
  Core](https://www.microsoft.com/net/core/platform) or on the full [.NET
  Framework](https://www.microsoft.com/net/framework)
- Designed to provide an optimized development framework for apps that are
  deployed to the cloud or run on-premise
- Modular components with minimal overhead retain flexibility while
constructing your solutions

## Prerequisites

This example assumes you already have an ASP.NET Core app
on your machine. If you are new to ASP.NET you can follow a [simple
tutorial](https://www.asp.net/get-started) to initialize a project or clone our [ASP.NET Docker Sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp).

## Create a Dockerfile for an ASP.NET Core application

1.  Create a `Dockerfile` in your project folder.
2.  Add the text below to your `Dockerfile` for either Linux or [Windows
   Containers](https://docs.microsoft.com/en-us/virtualization/windowscontainers/about/).
    The tags below are multi-arch meaning they will pull either Windows or
    Linux containers depending on what mode is set in [Docker for
Windows](https://docs.docker.com/docker-for-windows/). Read more on [switching containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).
3.  The `Dockerfile` assumes that your application is called `aspnetapp`. Change
   the `Dockerfile` to use the DLL file of your project.

```dockerfile
FROM microsoft/aspnetcore-build:2.0 AS build-env
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

# Build runtime image
FROM microsoft/aspnetcore:2.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "aspnetapp.dll"]
```

4.  To make your build context as small as possible add a [`.dockerignore`
   file](https://docs.docker.com/engine/reference/builder/#dockerignore-file)
   to your project folder and copy the following into it.

```dockerignore
bin\
obj\
```

## Build and run the Docker image

1.  In the command prompt and navigate to your project folder.
2.  Use the following commands to build and run your Docker image:

```console
$ docker build -t aspnetapp .
$ docker run -d -p 8080:80 --name myapp aspnetapp
```

## View the web page running from a container

* Go to [localhost:8080](http://localhost:8080) to access your app in a web browser.
* If you are using the Nano [Windows
  Container](https://docs.docker.com/docker-for-windows/) and have not updated
   to the Windows Creator Update there is a bug affecting how [Windows 10
   talks to Containers via
  "NAT"](https://github.com/Microsoft/Virtualization-Documentation/issues/181#issuecomment-252671828)
  (Network Address Translation). You must hit the IP of the container
  directly. You can get the IP address of your container with the following
  steps:
  1.  Run `docker inspect -f "{% raw %}{{ .NetworkSettings.Networks.nat.IPAddress }}{% endraw %}" myapp`
  2.  Copy the container ip address and paste into your browser.
  (For example, `172.16.240.197`)

## Further reading

  - [ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/)
  - [Microsoft ASP.NET Core on Docker
    Hub](https://hub.docker.com/r/microsoft/aspnetcore/)
  - [ASP.NET Core with Docker Tools for Visual
    Studio](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)
