# Spring Boot starter: GitHub Actions + GHCR

This repo is a minimal Spring Boot app wired for containerization and publishing images to GitHub Container Registry (GHCR). It also exposes Spring Boot Actuator and uses two simple profiles for local and Docker runs.

## Quick start

- Run with Docker Compose (uses `docker` profile):

```bash
docker compose up -d
```

## Profiles

This project uses two profiles defined by properties files under `src/main/resources`:

- `application.properties` (default):
  - Used when running locally via Maven or your IDE.
  - Uses H2/in-memory DB (see repository tests), and default server port.

- `application-docker.properties` (activated when running in a container):
  - Uses MySQL database configured in `docker-compose.yml`.

## Actuator

Actuator endpoints expose health and basic diagnostics:

- Base path: `/actuator`
- Common endpoints: `/actuator/health` (only one enabled)

In dev, you can curl them:

```bash
curl -s http://localhost:8080/actuator/health
```

Note: Additional endpoints can be enabled or secured via properties; by default only safe endpoints are exposed.

## Endpoints:
- `GET /hello` simple hello route
- `GET /books` sample CRUD backing via JPA repository
- `GET /actuator` Actuator base endpoint
- `GET /actuator/health` health check endpoint (only one enabled)