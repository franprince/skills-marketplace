# skills-marketplace

A personal [Claude Code plugin marketplace](https://docs.claude.com/en/docs/claude-code/plugins). One repo, one `.claude-plugin/marketplace.json` catalog, a `plugins/` directory per plugin — install any of them with two commands, no cloning, no manual file drops.

## Install

```
/plugin marketplace add franprince/skills-marketplace
/plugin install <plugin-name>@skills-marketplace
```

## Plugins

| Plugin | Description |
|---|---|
| [`chowa-skill`](plugins/chowa-skill/) | Spec → plan → execute pipeline, atomic Conventional Commits, PR generation, and mechanical sub-task delegation — pure skill, no CLI or bundled engine. A lean sibling of [chowa](https://github.com/franprince/chowa) (the CLI-backed original); this variant intentionally leaves out model routing against live provider data and quota-aware session auto-resume, both of which need more than a skill can do on its own. |

## Adding a plugin

Each plugin lives under `plugins/<name>/` with its own `.claude-plugin/plugin.json`, and gets a row in `.claude-plugin/marketplace.json`. See `chowa-skill` for the shape: a `skills/<name>/SKILL.md`, optionally an `agents/` subagent definition or `hooks/` for mechanical enforcement, no dependency on anything outside the plugin's own directory.

## License

MIT
