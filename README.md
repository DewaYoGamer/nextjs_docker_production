# Next.js Docker Production Template

Production-ready Next.js 15 (App Router) project configured for containerized deployment using a multi-stage Docker build and `docker compose`.

## Features

- Next.js 15 App Router with `output: 'standalone'` for minimal production image
- Multi-stage Dockerfile (deps → builder → runner) using `node:18-alpine`
- Turbopack enabled for `dev` and `build`
- Healthcheck in `compose.yml`
- Environment variable layering (`.env.local`, Docker `environment`, build-time vs runtime considerations)
- Clean `.gitignore` (env files ignored by default)


## Build & Run with Docker

```bash
# Build image
docker build -t my-next-app:latest .
# Run container
docker run -p 3000:3000 my-next-app:latest
# Visit http://localhost:3000
```

## Using docker compose

`compose.yml` already maps container port 3000 to host 60001.

```bash
docker compose build
docker compose up -d
# Open http://localhost:60001
```

Stop & clean:

```bash
docker compose down
```

## Extending

- Add a reverse proxy (e.g., Nginx or Traefik) in `compose.yml`
- Add a separate service for a database (Postgres, Redis, etc.)
- Add CI pipeline to build and push the image

