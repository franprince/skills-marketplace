---
name: media-library
description: Manage multimedia library batch MKV default tracks, Bazarr subtitle rules, and container stack services.
---

# Media Library Management Skill

This skill provides utilities, scripts, and workflows to manage the media stack (`Sonarr`, `Radarr`, `Bazarr`, `Jellyfin`, `ErsatzTV`) and perform batch operations on MKV video files.

## Utilities Included

### 1. Batch MKV Track Manager (`media-tools tracks`)
Automatically sets the default audio and subtitle track flags across directories of MKV files in-place using `mkvpropedit` without re-encoding.

**Usage:**
```bash
bun run bin/media-tools.ts tracks "/mnt/anime/Anime Shows" --exclude=Envious
```

**Selection Rules:**
- **Audio**: Automatically sets Japanese audio (`jpn`, `ja`) as `default=1`.
- **Subtitles**: Evaluates subtitle tracks in strict priority:
  1. **Latin Spanish** (`es-419`, `es-mx`, `latino`, `latam`)
  2. **Spanish** (`spa`, `es`)
  3. **English** (`eng`, `en`)

### 2. Bazarr API Manager (`media-tools bazarr`)
Connects to Bazarr's REST API at `http://127.0.0.1:6767` to inspect system status, series/movies counts, and language profiles.

**Usage:**
```bash
bun run bin/media-tools.ts bazarr
```

### 3. Media Stack Systemd User Services
Containers are managed via `podman` systemd user services located in `~/.config/systemd/user/`:
- `container-sonarr.service`
- `container-radarr.service`
- `container-bazarr.service`
- `container-jellyfin.service`
- `container-overseerr.service`
- `container-prowlarr.service`
- `container-tautulli.service`
- `container-kometa.service`
- `container-nzbget.service`

**Restarting a service:**
```bash
systemctl --user restart container-bazarr.service
```

**Backing up configuration:**
```bash
/home/fran/Documentos/media-stack/backup-media-stack.sh
```
