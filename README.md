# Docker Homelab

A collection of Docker Compose stacks for a self-hosted homelab. Each service lives in its own folder with a dedicated compose file, so you can bring up only what you need.

## What's inside

- **Nginx Proxy Manager** (`nginx/docker-compose.yml`) for reverse proxy + TLS
- **Media & requests**
  - **Jellyfin** (`jellyfin/docker-compose.jellyfin.yml`)
  - **Jellyseerr** (`jellyseerr/docker.compose.jellyseerr.yml`)
  - **AudioBookShelf** (`audioBookShelf/docker-compose.audiobook.yml`)
- **Photo management**
  - **Immich** (`immich/docker-compose.immich.yml`) with Postgres + Redis/Valkey
- **Arr stack behind VPN**
  - **Gluetun + qBittorrent + *arr** (`gluetun-arr/docker-compose-gluetun-arr.yml`)
  - Includes: Prowlarr, Sonarr, Radarr, Lidarr, Readarr, Bazarr, FlareSolverr
- **Dashboard**
  - **Glance** (`glance/docker-compose.yml`)
- **Remote access**
  - **Twingate connector** (`twingate/docker-compose.twingate.yml`)
- **Watchtower** (`watchtower/docker-compose.watchtower.yml`) for auto updating containers

## Quick start

> These stacks are tailored to a specific host layout (e.g., `/mnt/nas`, `/mnt/immich-photos`). Review and adjust volumes and environment variables before running.

1. Install Docker + Docker Compose (or use Portainer).
2. Create any required environment variables (for Portainer, set these in the stack's environment variables).
3. Start a stack:

```bash
docker compose -f nginx/docker-compose.yml up -d
```

Repeat with the compose file for any other service you want to run.

## Environment variables

Several compose files reference environment variables (e.g., `TZ`, `APPPATH`, `ARRPATH`, `WIREGUARD_PRIVATE_KEY`, `DB_*`). Define these in your shell or in a `.env` file next to the compose file you are running. If you are using Portainer, define them in the stack's environment variable section.

## Notes

- Many services are attached to the external Docker network `nginxproxymanager_default` to integrate with Nginx Proxy Manager.
- Paths under `/mnt` are expected to be mounted on the host. Update them if your storage layout differs.

## Repository layout

```
.
├── audioBookShelf/
├── gluetun-arr/
├── jellyfin/
├── jellyseerr/
├── immich/
├── glance/
├── nginx/
├── twingate/
└── watchtower/
```
