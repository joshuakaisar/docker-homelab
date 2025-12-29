# Glance Startpage Notes

## Required environment variables
Add these to your `.env` or environment configuration for the Glance container:

- `JELLYFIN_URL`
- `JELLYFIN_API_KEY`
- `RADARR_URL`
- `RADARR_API_KEY`
- `SONARR_URL`
- `SONARR_API_KEY`
- `QBITTORRENT_URL`
- `QBITTORRENT_USER`
- `QBITTORRENT_PASS`
- `GLUETUN_URL`
- `GLUETUN_API_KEY`
- `SPEEDTEST_URL`
- `SPEEDTEST_TRACKER_API_TOKEN`

Optional (already used elsewhere in the dashboard):
- `PROWLARR_URL`, `PROWLARR_API_KEY`, `LIDARR_URL`, `READARR_URL`, `BAZARR_URL`,
  `JELLYSEERR_URL`, `NGINX_PROXY_MANAGER_URL`, `AUDIOBOOKSHELF_URL`

## qBittorrent API auth
The qBittorrent widget calls `/api/v2/transfer/info` and `/api/v2/torrents/info`.
If your qBittorrent instance requires authentication, provide a reverse proxy or
sidecar that handles login using `QBITTORRENT_USER`/`QBITTORRENT_PASS`, or expose
an unauthenticated read-only endpoint.
