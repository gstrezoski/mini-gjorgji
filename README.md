# mini-gjorgji

A personal collection of Claude Code skills, packaged as a plugin: each skill lives under `skills/`, in its own directory with a `SKILL.md`.

This repo starts as a catalog. Skills currently installed at `~/.agents/skills` get reviewed one at a time — see [INVENTORY.md](./INVENTORY.md) for the list and status of each. Only skills that pass review get copied in here and published.

## Layout

```
skills/
  <skill-name>/  each skill in its own directory with a SKILL.md
```

Categories (engineering, productivity, misc) are tracked in [INVENTORY.md](./INVENTORY.md), not in the folder structure — Claude Code plugins expect skills flat, directly under `skills/`.

## Install

This repo is a Claude Code plugin marketplace and a plugin at the same time (`.claude-plugin/marketplace.json` and `.claude-plugin/plugin.json` at the root). From inside Claude Code:

```
/plugin marketplace add gstrezoski/mini-gjorgji
/plugin install mini-gjorgji@mini-gjorgji
```

That installs every skill in the repo, namespaced as `/mini-gjorgji:<skill-name>`, and Claude Code keeps them up to date from the repo — no manual copying.

Prefer to drive it interactively instead: clone the repo, open Claude Code in it, and ask it to walk you through adding the marketplace and installing the plugin.

```
git clone git@github.com:gstrezoski/mini-gjorgji.git
cd mini-gjorgji
claude
```

To install skills the old way instead — copied loose into `~/.claude/skills`, no plugin namespacing — ask Claude to copy or symlink individual `skills/<name>` directories there.

## Status

All 34 skills from `~/.agents/skills` reviewed — see [INVENTORY.md](./INVENTORY.md) for the verdict on each. 30 kept (2 of them, `writing-beats` and `writing-shape`, carried over marked draft), 2 dropped as vendor/third-party tooling (`find-skills`, `microsoft-foundry`).

Run `/install-gjorgji-skills` first in any repo before using the other engineering skills — it sets up the issue tracker, triage labels, and doc layout they assume.

Packaged as a Claude Code plugin — see [Install](#install) above.
