# Docker

## Definition

Platform for building, running, and shipping cross-platform applications using
container technology.

## Image

- **Container snapshot/template** containing all necessary files & dependencies
to run an application.
- The [**Docker Hub**](https://hub.docker.com/) is a **public registry of**
**Docker images**.
- Create a **Docker image** with a **Dockerfile**.

### Image commands

| Command                           | Description                        |
|-----------------------------------|------------------------------------|
| `docker images`                   | List all images.                   |
| `docker image build <dockerfile>` | Build an image from a Dockerfile.  |
| `docker image rm <image>`         | Remove an image.                   |
| `docker image tag <image> <tag>`  | Create an alias for an image.      |
| `docker pull <image>`             | Pull an image from the Docker Hub. |

## Container

- **Running instance of an image**.

### Create/Run a container

```console
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```

| Option | Description                                                          |
|--------|----------------------------------------------------------------------|
| `-d`   | Run container in background.                                         |
| `-it`  | Make container interactive through a terminal.                       |
| `-p`   | Publish a container's port(s) to the host: `hostPort:containerPort`. |
| `--rm` | Automatically remove the container when it exits.                    |
| `-v`   | Mount a volume: `hostPath:containerPath`.                            |
| `-w`   | Working directory inside the container.                              |

## Volumes

- **Persistent data storage** for containers.
- **Independent from the container's lifecycle**.
- **Can be shared** between containers.

### Data volumes

- Default Docker storage type;
- Works on both Linux and Windows;
- Easy to move/save;
- Can be used with volumes drivers for remote storage (NFS, SAMBA, cloud, ...).

### Bind volumes

- Map a host directory to a container directory;

### TMPFS volumes

- Stored in the host's memory;
- Faster than data volumes;
- Linux only;
- Same lifecycle as the container;
- Can't be shared between containers.
