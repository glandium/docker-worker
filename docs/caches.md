---
title: Caches
order: 30
---

Caches require scopes: `docker-worker:cache:<cache name>`

Docker-worker has the ability to provide volumes mounted within the task container that can persist between tasks. This provides a way of caching large often used files (repos, object directories) and share them between tasks.

Volume caches falls under the garbage collection policies when diskspace threshold is reached. Any cached volumes that are no longer mounted within a container are removed from the host system when this event occurs.

Tasks need to define a name for the cache that will be used for other tasks requiring the same cached volume as well as a mount point for where the volume will be mounted within the task container.

Example:

```js
{
  "scopes": [
    "docker-worker:cache:b2g-object-directory"
  ],
  "payload": {
    "cache": {
      "b2g-object-directory": "/path/for/mount/point"
    }
  }
}
```

