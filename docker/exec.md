# [docker exec](https://docs.docker.com/engine/reference/commandline/container_exec/#:~:text=Description,working%20directory%20of%20the%20container.)

Equivalent to  `docker container exec`

The `docker exec` command runs a new command in a running container.

**exemples :**

Open a terminal in `CONTAINER` :
```console
docker exec -it CONTAINER bash
```

**usefull options :**

| option | description |
|--|--|
| `-i` or `--interactive` | Keep STDIN open even if not attached (needed if the command is interactive) |
| `-t` or `--tty` | Allocate a pseudo-TTY (needed with `-i` to open a terminal in a container) |



> Written with [StackEdit](https://stackedit.io/).
