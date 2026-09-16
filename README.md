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

## FAQ

**Can I install just one skill instead of the whole thing?**
Not through the plugin — `/plugin install` pulls in every skill in the repo. To take one, copy or symlink its `skills/<name>` directory into `~/.claude/skills/<name>` by hand (see [Install](#install)).

**Will this overwrite skills I already have with the same name?**
`/plugin install` namespaces everything as `/mini-gjorgji:<skill-name>`, so it won't collide with anything in `~/.claude/skills`. Manual copies into `~/.claude/skills` do overwrite same-named directories — check first.

**Do the skills depend on each other?**
Some do — [INVENTORY.md](./INVENTORY.md) notes it per skill (e.g. `tdd` depends on `codebase-design` and `code-review`; `triage` depends on `grilling` and `domain-modeling`). Installing the whole plugin covers all of them; installing skills one by one, pull in what they depend on too.

**What's `agents/openai.yaml` in each skill directory?**
A display name and short description for surfacing the same skill in OpenAI's agent builder. Claude Code ignores it entirely — it's there so the skill content works as a tool definition on either platform.

**Do these skills call external services or cost extra tokens beyond normal usage?**
No network calls beyond what your own prompts already trigger (e.g. `WebFetch`/`WebSearch`, when a skill tells Claude to use them). A skill is a markdown file injected into context when it's invoked, not a separate process.

**How do I get updates after I've already installed?**
Plugin install: `/plugin update mini-gjorgji`. Manual install: re-copy or re-symlink the changed `skills/<name>` directory.

**How do I remove a skill?**
Plugin install: `/plugin uninstall mini-gjorgji`. Manual install: delete or unlink `~/.claude/skills/<name>`.

**Why is `skills/` flat instead of grouped by category?**
Claude Code plugins auto-discover skills as `skills/<name>/SKILL.md` directly under the plugin root — no nested category folders. The categories still exist, just as metadata in [INVENTORY.md](./INVENTORY.md) rather than as directories.
