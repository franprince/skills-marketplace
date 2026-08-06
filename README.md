# skills-marketplace

A personal [Claude Code plugin marketplace](https://docs.claude.com/en/docs/claude-code/plugins) — a catalog, not a home for plugin content. Each plugin listed here lives in its own dedicated repo; this repo's `.claude-plugin/marketplace.json` just points at it. Install any of them with two commands, no cloning, no manual file drops.

## Install

```
/plugin marketplace add franprince/skills-marketplace
/plugin install <plugin-name>@skills-marketplace
```

## Plugins

| Plugin | Repo | Description |
|---|---|---|
| `chowa-skill` | [franprince/chowa-skill](https://github.com/franprince/chowa-skill) | Spec → plan → execute pipeline, atomic Conventional Commits, PR generation, and mechanical sub-task delegation — pure skill, no CLI or bundled engine. A lean sibling of [chowa](https://github.com/franprince/chowa) (the CLI-backed original); this variant intentionally leaves out model routing against live provider data and quota-aware session auto-resume, both of which need more than a skill can do on its own. |

## Adding a plugin

Give the plugin its own repo — self-contained, with its own `.claude-plugin/plugin.json` at the root and (recommended) its own `.claude-plugin/marketplace.json` (`source: "./"`) so it installs directly on its own, not only through this catalog. Then add a row here referencing it externally:

```json
{
  "name": "plugin-name",
  "source": { "source": "github", "repo": "franprince/plugin-name" },
  "description": "..."
}
```

See `chowa-skill`'s own repo for the shape: a `skills/<name>/SKILL.md`, optionally an `agents/` subagent definition or `hooks/` for mechanical enforcement.

## License

MIT
