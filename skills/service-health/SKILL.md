---
name: service-health
description: Check whether Radarr, Sonarr, Plex, qBittorrent, or NZBGet is online, and inspect free disk space across Radarr/Sonarr root folders.
---

# Service Health Skill

Mechanical, read-only checks against the media stack — no judgment calls, just
"is it up" and "how much space is left." Suited for direct invocation without
an AI model in the loop.

## Utilities Included

### 1. Check Service Health (`media-tools health <service>`)
Confirms a named service responds. Supported services: `Radarr`, `Sonarr`,
`Plex`, `qBittorrent`, `NZBGet`.

**Usage:**
```bash
bun run bin/media-tools.ts health Radarr
```

Returns online/offline; an unsupported service name is a hard error, not a
silent "offline."

### 2. Disk Space (`media-tools disk-space`)
Reports free space (in bytes) for every root folder configured in Radarr and
Sonarr.

**Usage:**
```bash
bun run bin/media-tools.ts disk-space
```

## Configuration

Reads from the environment — see the main `media-tools` `README.md` for the
full list (`RADARR_URL`/`RADARR_API_KEY`, `SONARR_URL`/`SONARR_API_KEY`,
`PLEX_URL`/`PLEX_TOKEN`, `QBITTORRENT_URL`/`QBITTORRENT_USERNAME`/
`QBITTORRENT_PASSWORD`, `NZBGET_URL`). Only the variables for the service(s)
you actually call need to be set.
