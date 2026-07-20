# 🐳 Docker Commands

## Docker Information

| Command | Purpose |
|---------|---------|
| `docker version` | Show Docker client and server versions. |
| `docker info` | Display Docker system information. |
| `docker system df` | Show Docker disk usage (images, containers, volumes, cache). |

---

## Images

| Command | Purpose |
|---------|---------|
| `docker images` | List downloaded/built images. |
| `docker image ls` | Same as `docker images`. |
| `docker image rm <image>` | Remove an image. |

---

## Containers

| Command | Purpose |
|---------|---------|
| `docker ps` | Show running containers. |
| `docker ps -a` | Show all containers. |
| `docker stop <container>` | Stop a running container. |
| `docker start <container>` | Start a stopped container. |
| `docker rm <container>` | Remove a container. |
| `docker logs <container>` | View container logs. |

---

## Docker Compose

| Command | Purpose |
|---------|---------|
| `docker compose up` | Start services. |
| `docker compose up --build` | Rebuild images and start services. |
| `docker compose down` | Stop and remove containers. |
| `docker compose ps` | Show Compose containers. |
| `docker compose logs` | View logs of all services. |
| `docker compose logs backend` | View backend logs only. |
| `docker compose logs postgres` | View PostgreSQL logs only. |

---

## Cleanup

| Command | Purpose |
|---------|---------|
| `docker image prune` | Remove unused images. |
| `docker container prune` | Remove stopped containers. |
| `docker volume prune` | Remove unused volumes. |
| `docker builder prune` | Remove build cache. |
| `docker system prune` | Remove unused containers, images, and networks. |
| `docker system prune -a` | Remove everything unused, including images. |

---

## Build

```bash
docker build -t sos-backend .
```

Build an image from the Dockerfile.

---

## Run

```bash
docker run -p 8080:8080 sos-backend
```

Create a container from the image.

---

## Useful Inspection Commands

```bash
docker inspect <container>
```

View container configuration.

```bash
docker exec -it <container> bash
```

Open a shell inside a running container.
