---
title: Deploy application resources to a collection
description: Learn how to manage user access to application resources by using collections.
keywords: UCP, authentication, user management, stack, collection, role, application, resources
---

Docker Universal Control Plane enforces role-based access control when you
deploy services. By default, you don't need to do anything, because UCP deploys
your services to a default collection, unless you specify another one. You can
customize the default collection in your UCP profile page.
[Learn more about access control and collections](../../access-control/manage-access-with-collections.md).

UCP defines a collection by its path. For example, a user's default collection
has the path `/Shared/Private/<username>`. To deploy a service to a collection
that you specify, assign the collection's path to the *access label* of the
service. The access label is named `com.docker.ucp.access.label`.

When UCP deploys a service, it doesn't automatically create the collections
that correspond with your access labels. An administrator must create these
collections and [grant users access to them](grant-permissions.md). Deployment
fails if UCP can't find a specified collection or if the user doesn't have
access to it.

## Deploy a service to a collection by using the CLI

Here's an example of a `docker service create` command that deploys a service
to a `/Shared/database` collection:

```bash
$ docker service create \
  --name redis_2 \
  --label com.docker.ucp.access.label="/Shared/database"
  redis:3.0.6
  ```

## Deploy services to a collection by using a Compose file

You can also specify a target collection for a service in a Compose file.
In the service definition, add a `labels:` dictionary, and assign the
collection's path to the `com.docker.ucp.access.label` key.

If you don't specify access labels in the Compose file, resources are placed in
the user's default collection when the stack is deployed.

You can place a stack's resources into multiple collections, but most of the
time, you won't need to do this.

Here's an example of a Compose file that specifies two services, WordPress and
MySQL, and gives them the access label `/Shared/wordpress`:

```none
version: '3.1'

services:

  wordpress:
    image: wordpress
    ports:
      - 8080:80
    environment:
      WORDPRESS_DB_PASSWORD: example
    deploy:  
      labels:
        com.docker.ucp.access.label: /Shared/wordpress
  mysql:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: example
    deploy:  
      labels:
        com.docker.ucp.access.label: /Shared/wordpress

```

To deploy the application:

1. In the UCP web UI, navigate to the **Stacks** page and click **Create Stack**.
2. Name the app "wordpress". 
3. From the **Mode** dropdown, select **Services**.
4. Copy and paste the previous compose file into the **Compose.yml** editor.
5. Click **Create** to deploy the application, and click **Done** when the
   deployment completes.

If the `/Shared/wordpress` collection doesn't exist, or if you don't have
a grant for accessing it, UCP reports an error.

To confirm that the service deployed to the `/Shared/wordpress` collection:

1. In the **Stacks** page, click **wordpress**.
2. In the details pane, click **Inspect Resource** and select **Services**.
3. On the **Services** page, click **wordpress_mysql**. In the details pane,
   make sure that the **Collection** is `/Shared/wordpress`. 

![](../../images/deploy-stack-to-collection.png){: .with-border}

## Compose files with legacy access labels

If your Compose file has access labels for versions earlier than UCP 2.2.0,
you have three options:

- **Keep the existing access labels.** In this case, UCP deploys resources
  to the `/Shared/Legacy/<your-label>` collection. An administrator must create
  the legacy collection and grant permissions before you can deploy to it.

- **Deploy to the default collection.** To specify the user's default
  collection instead of a legacy collection, remove the 
  `com.docker.ucp.access.label` keys from the Compose file. In this case,
  UCP deploys resources automatically to the default collection, and no
  administrator action is required. 

- **Update the collection.** Change the access label to refer to a new
  collection. Be sure to use path notation. For example,
  `com.docker.ucp.access.label: /Shared/database` deploys to a child of the
  built-in `/Shared` collection. An administrator must create the child
  collection and grant permissions before you can deploy to it.

## Where to go next

- [Manage access to resources by using collections](../../access-control/manage-access-with-collections.md)
- [Set metadata on a service (-l, –label)](/engine/reference/commandline/service_create/#set-metadata-on-a-service--l-label)
- [Docker object labels](/engine/userguide/labels-custom-metadata.md)
