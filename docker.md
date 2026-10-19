- [TODO](#todo)
- [Commands Cheat Sheet](#commands-cheat-sheet)
  - [Images](#images)
    - [List Local Images](#list-local-images)
    - [Delete an Image](#delete-an-image)
    - [Remove all unused images](#remove-all-unused-images)
    - [Build an Image from a Dockerfile](#build-an-image-from-a-dockerfile)
  - [Containers](#containers)
    - [List Currently Running Containers](#list-currently-running-containers)
    - [List All Docker Container](#list-all-docker-container)
    - [Remove a stopped container](#remove-a-stopped-container)
    - [Start or stop an existing container](#start-or-stop-an-existing-container)
    - [Create and run a container from an image, with a custom name](#create-and-run-a-container-from-an-image-with-a-custom-name)
    - [Run a container with and publish a container’s port(s) to the host](#run-a-container-with-and-publish-a-containers-ports-to-the-host)
    - [Run a container in the background](#run-a-container-in-the-background)
    - [Run an image in interactively](#run-an-image-in-interactively)
    - [Start an stopped container interactively](#start-an-stopped-container-interactively)
    - [Open a shell inside a running container](#open-a-shell-inside-a-running-container)
    - [Automatically delete a container when it stops](#automatically-delete-a-container-when-it-stops)
- [Flags](#flags)
  - [Environment Variables](#environment-variables)
- [Dockerfile](#dockerfile)
  - [Syntax](#syntax)
  - [Examples](#examples)
    - [Dockarize a React app](#dockarize-a-react-app)
    - [Spin up a Postgres DB](#spin-up-a-postgres-db)
- [USEFUL](#useful)

## TODO

- [ ] Continue from volumes

## Commands Cheat Sheet

### Images

#### List Local Images

```bash
docker images
# -- OR --
docker image list
```

#### Delete an Image

```bash
docker rmi <image_name>
# -- OR --
docker image rm <image_name>
# -- OR --
docker image rm <image_name> -f  # Force delete
```

#### Remove all unused images

```bash
docker image prune
```

#### Build an Image from a Dockerfile

```bash
docker build -t <image_name> <rel_path_to_dockerfile>
```

### Containers

#### List Currently Running Containers

```bash
docker ps
```

#### List All Docker Container

```bash
docker ps --all
# -- OR --
docker ps -a
```

#### Remove a stopped container

```bash
docker rm <container_name>
# -- OR --
docker container rm <container_name>
```

#### Start or stop an existing container

```bash
docker start|stop <container_name> (or <container-id>)
```

#### Create and run a container from an image, with a custom name

```bash
docker run --name <container_name> <image_name>
```

#### Run a container with and publish a container’s port(s) to the host

```bash
docker run -p <host_port>:<container_port> <image_name>
```

#### Run a container in the background

```bash
docker run -d <image_name>
```

#### Run an image in interactively

```bash
docker run -it <image_name>
```

- `-i` — keeps standard input open so you can type commands.
- `-t` — allocates a terminal (TTY).

#### Start an stopped container interactively

```bash
docker start -ai <container_name>
```

- `-i` — keeps standard input open.
- `-a` — attaches your terminal to the container's output.

#### Open a shell inside a running container

```bash
docker exec -it <container_name> sh
```

#### Automatically delete a container when it stops

```bash
docker run --rm -it <image_name>
```

## Flags

### Environment Variables

```bash
docker run -e POSTGRES_PASSWORD=mysecretpassword postgres:18-bookworm
```

## Dockerfile

### Syntax

```dockerfile
FROM node:17-alpine  <-- Base Image

WORKDIR /app  <-- Create and cd into directory inside image

COPY <rel_path> .  <-- Copy project files to path inside the image

RUN <command>  <-- Run command at build time

EXPOSE <port_number>  <-- Expose port_number

CMD ["array", "of", "strings"]  <-- Command to execute at run time
```

### Examples

#### Dockarize a React app

```dockerfile
FROM node:26-alpine3.23

WORKDIR /app

RUN npm install -g pnpm

COPY package.json pnpm-lock.yaml ./

RUN pnpm install

COPY . .

EXPOSE 5173

CMD ["pnpm", "dev", "--host", "0.0.0.0"]
```

#### Spin up a Postgres DB

```dockerfile
FROM postgres:18-bookworm

ENV POSTGRES_DB=company
ENV POSTGRES_USER=username
ENV POSTGRES_PASSWORD=password # Do not add this! Use -e flag

# SQL scripts run automatically on first database initialization
COPY ./initial-seed.sql /docker-entrypoint-initdb.d/01-initial-seed.sql

EXPOSE 5432
```
**After building the image, spin it up**

```bash
docker run -de POSTGRES_PASSWORD=password -p 5432:5432 --name <container_name> <image_name>
```

**Connect to it using psql**

```bash
psql -h localhost -p 5432 -U username -d company
```

## USEFUL
