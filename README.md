docker-commands

A quick reference for building, running, and managing your project via Docker.

---

## 1. Build Image

Use a build‑time argument (ARG) to pass in your environment, then tag the image:

    docker build . --build-arg ENV=production -t my-app:test

## 2. Run Container

Start an interactive shell in your container:

    docker run -it my-app:test

## 3. Inspect

- List images: `docker images`
- List running containers: `docker ps`

## 4. Exec Into Container

    docker exec -it <container_id> sh

*(Replace `<container_id>` with the ID from `docker ps`.)*

## 5. Cleanup

- Stop: `docker stop <container_id>`
- Remove container: `docker rm <container_id>`
- Remove image: `docker rmi my-app:test`

---

## ARG vs ENV

- `ARG`: build‑time only (e.g., `--build-arg ENV=production`)
- `ENV`: available at runtime inside the container

---

## Example Dockerfile Snippet

```dockerfile
FROM node:18

ARG ENV
ENV NODE_ENV=$ENV

WORKDIR /app
COPY . .
RUN echo "Building with ENV=$ENV"
CMD ["node", "index.js"]
```
