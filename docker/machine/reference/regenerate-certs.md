---
description: Regenerate and update TLS certificates
keywords: machine, regenerate-certs, subcommand
title: docker-machine regenerate-certs
---

```none
Usage: docker-machine regenerate-certs [OPTIONS] [arg...]

Regenerate TLS Certificates for a machine

Description:
   Argument(s) are one or more machine names.

Options:

   --force, -f  Force rebuild and do not prompt
```

Regenerate TLS certificates and update the machine with new certs.

For example:

```none
$ docker-machine regenerate-certs dev

Regenerate TLS machine certs?  Warning: this is irreversible. (y/n): y
Regenerating TLS certificates
```