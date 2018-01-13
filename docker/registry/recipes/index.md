---
description: Fun stuff to do with your registry
keywords: registry, on-prem, images, tags, repository, distribution, recipes, advanced
title: Recipes overview
---

You will find here a list of "recipes", end-to-end scenarios for exotic or otherwise advanced use-cases.

Most users are not expected to have a use for these.

## Requirements

You should have followed entirely the basic [deployment guide](../deploying.md).

If you have not, please take the time to do so.

At this point, it's assumed that:

 * you understand Docker security requirements, and how to configure your docker engines properly
 * you have installed Docker Compose
 * it's HIGHLY recommended that you get a certificate from a known CA instead of self-signed certificates
 * inside the current directory, you have a X509 `domain.crt` and `domain.key`, for the CN `myregistrydomain.com`
 * be sure you have stopped and removed any previously running registry (typically `docker stop registry && docker rm -v registry`)

## The List

 * [using Apache as an authenticating proxy](apache.md)
 * [using Nginx as an authenticating proxy](nginx.md)
 * [running a Registry on macOS](osx-setup-guide.md)
 * [mirror the Docker Hub](mirror.md)
