# Docker

## Definition

Platform for building, running, and shipping applications using container technology.

## Image

- **Container snapshot/template** containing all necessary files & dependencies
to run an application.
- The [**Docker Hub**](https://hub.docker.com/) is a **public registry of**
**Docker images**.
- Create a **Docker image** with a **Dockerfile**.

### Image commands

| Command | Description |
|-------- | ----------- |
| `docker images` | List all images. |
| `docker image build <dockerfile>` | Build an image from a Dockerfile. |
| `docker image rm <image>` | Remove an image. |
| `docker image tag <image> <tag>` | Create an alias for an image. |
| `docker pull <image>` | Pull an image from the Docker Hub. |
