# gstack

Guillem's Claude Code skills, packaged as a plugin.

## Install

Add the marketplace once, then install the plugin:

```
/plugin marketplace add GuillemGarciaDev/gstack
/plugin install gstack@gstack
```

Or from a shell:

```
claude plugin marketplace add GuillemGarciaDev/gstack
claude plugin install gstack@gstack
```

## Try it without installing

```
claude --plugin-dir ./plugins/gstack
```

Run `/reload-plugins` inside the session after editing a skill.

## Layout

- `plugins/gstack/` is the plugin. Its `.claude-plugin/plugin.json` is the manifest and `skills/` holds one folder per skill.
- `skills/` at the repo root is a symlink to `plugins/gstack/skills`, so both paths edit the same files.
- `.claude-plugin/marketplace.json` makes this repo a marketplace that serves the plugin.

## Skills

User-invocable:

- `g-mode`: the agent style that ties the rest together.
- `blast-radius`, `tdd`, `create-verification-skill`
- `unslop`, `deslop`, `no-comments`, `bro`
- `get-pr-comments`, `fix-merge-conflicts`

Principles the model applies on its own (`user-invocable: false`): fix root causes, guard the context window, laziness protocol, make operations idempotent, never block on the human, subtract before you add.
