---
name: channel-director
description: AI Channel Director skill for ErsatzTV IPTV block scheduling, linear TV channel curation, and daily program guide management.
---

# Channel Director Skill

The **Channel Director** skill (hosted in `media-tools`) enables AI assistants and agents to construct, automate, and orchestrate custom linear IPTV channels in ErsatzTV from your media library (Plex/Jellyfin).

## Capability Overview

1. **Daily Guide Queries**: Retrieve real-time Electronic Program Guide (EPG) schedules across all channels or a specific IPTV channel.
2. **System Health & Status**: Inspect ErsatzTV status, server version, channel counts, and active channel playouts.
3. **Automated Programming Creation**: Automatically configure smart collections, schedule blocks, slot durations, and fillers according to user-specified parameters.

## Tool Invocation Patterns

### 1. Daily Program Guide
To check what's playing today or on a specific date:
- Call `getErsatzTVGuide` with optional `channelId` and `date` (`YYYY-MM-DD`).

### 2. Status & Health
To check ErsatzTV status:
- Call `getErsatzTVStatus`.

### 3. Channel Director Parameterized Programming
To set up a custom IPTV channel, invoke `channelDirector` with:
- `channelName`: Name of the channel (e.g. "90s Saturday Morning Cartoons").
- `channelNumber`: IPTV channel number (e.g. "101").
- `genres`: Array of genre strings (e.g. `["Animation", "Comedy"]`).
- `showTitles`: List of specific show titles.
- `releaseYearMin` / `releaseYearMax`: Decade or year constraints (e.g. `1990` - `1999`).
- `scheduleMode`: `"block" | "chronological" | "random" | "shuffle"`.
- `slotDurationMinutes`: Slot size (default: `30`).
- `includeFillers`: `true` to include bumpers/commercials.
