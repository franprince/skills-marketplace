---
name: download-queue
description: Inspect and control the qBittorrent torrent queue (pause/resume, single or all) and read the NZBGet download queue and status.
---

# Download Queue Skill

Mechanical download-queue operations against qBittorrent and NZBGet — listing,
pausing, and resuming. No judgment calls; suited for direct invocation
without an AI model in the loop.

## Utilities Included

### Download Queues (`media-tools downloads`)
Prints the current qBittorrent torrent list and the NZBGet queue + global
status in one call.

**Usage:**
```bash
bun run bin/media-tools.ts downloads
```

For programmatic use (e.g. from another skill or bot), import
`DownloadQueueManager` directly:

```ts
import { DownloadQueueManager } from "media-tools";

const manager = new DownloadQueueManager();
await manager.getTorrents("downloading");
await manager.pauseTorrent(hash);
await manager.resumeTorrent(hash);
await manager.pauseAllTorrents();
await manager.resumeAllTorrents();
await manager.getNZBGetQueue();
```

All values returned are raw (byte counts, seconds, fractional progress) —
formatting for display is left to the caller.

## Configuration

Reads from the environment — see the main `media-tools` `README.md`:
`QBITTORRENT_URL`/`QBITTORRENT_USERNAME`/`QBITTORRENT_PASSWORD`,
`NZBGET_URL` (`NZBGET_USERNAME`/`NZBGET_PASSWORD` optional).
