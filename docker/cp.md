# [docker cp](https://docs.docker.com/engine/reference/commandline/container_cp/)

Equivalent to  `docker container cp`

The `docker cp` utility copies the contents of `SRC_PATH` to the `DEST_PATH`. You can copy from the container's file system to the local machine or the reverse.

**exemples :**

Copy a local file into container :
```console
 docker cp SRC_PATH CONTAINER:DEST_PATH
```

Copy files from container to local path :
```console
docker cp CONTAINER:DEST_PATH SRC_PATH
```

> Written with [StackEdit](https://stackedit.io/).
