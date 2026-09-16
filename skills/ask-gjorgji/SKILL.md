---
name: ask-gjorgji
description: Ask which skill or flow fits your situation. A router over the skills in this repo.
disable-model-invocation: true
---

# Ask Gjorgji

You don't remember every skill, so ask.

A **flow** is a path through the skills. Most paths run along one **main flow**, and two **on-ramps** merge onto it. Everything else is standalone, or a vocabulary layer that runs underneath.

## The main flow: idea → ship

The route most work travels. You have an idea and want it built.

1. **`/grill-with-docs`** sharpens the idea by interview. Start here whenever you are **working in a working directory**: it's stateful, retaining what it learns in `CONTEXT.md` and ADRs. (No working directory? Use `/grill-me` instead, covered under Standalone. Both run the same `/grilling` primitive; `grill-with-docs` is the one that leaves a paper trail, which makes it the better of the two whenever a repo is there to leave it in.)
2. **Branch: can you settle every question in conversation?** If a question needs a runnable answer (state, business logic, a UI you have to see), detour through a prototype, bridged by **`/handoff`** in both directions (a prototype lives in its own directory, which is exactly what `/handoff` is for):
   - **`/handoff`** out, then open a fresh session against that file,
   - **`/prototype`** to answer the question with throwaway code,
   - **`/handoff`** back what you learned, and reference it from the original idea thread.
3. **Branch: is this a multi-session build?**
   - **Yes** → **`/to-spec`** (turn the thread into a spec), then **`/to-tickets`** to split it into tracer-bullet tickets, each declaring its **blocking edges**. On a local tracker that's one file per ticket under `.scratch/<feature>/issues/`, worked blockers-first by hand; on a real tracker the edges become native blocking links, so any ticket whose blockers are done can be grabbed: kick off **`/implement`** per ticket, **`/clear`ing context between each one**. Each ticket is self-contained, so the last one's context is disposable.
   - **No** → **`/implement`** right here, in the same context window.

   Either way, **`/implement`** builds each issue by driving **`/tdd`** internally (one red-green slice at a time), then closes out by running **`/code-review`**, a two-axis review (Standards + Spec) of the diff, before committing. Reach for **`/tdd`** on its own when you just want to build a concrete behaviour test-first without a full spec, and **`/code-review`** on its own whenever you want to review a branch or PR against a fixed point.

## On-ramps

A starting situation that generates work, then merges onto the main flow.

- **Bugs and requests piling up** → **`/triage`**. It moves issues through triage roles and produces agent-ready issues, which **`/implement`** later picks up.

  Triage is only for issues **you didn't create**: bug reports, incoming feature requests, anything that arrives raw. Tickets that `/to-tickets` produced are already agent-ready, so **don't triage them**.

- **Something's broken** → **`/diagnosing-bugs`**. For the hard ones: the bug that resists a first glance, the intermittent flake, the regression that crept in between two known-good states. It refuses to theorise until it has a **tight feedback loop**, then fixes with a regression test. Its post-mortem hands off to **`/improve-codebase-architecture`** when the real finding is that there's no good seam to lock the bug down.

- **A huge, foggy effort: a greenfield project or a huge feature build, too big for one session** → **`/wayfinder`**, the most cognitively demanding flow here. It charts a **shared map** of **decision tickets** on the issue tracker and resolves them one at a time, producing **decisions, not deliverables**, until the fog is pushed back and the way is clear.

  When the map clears, **it hands off, it doesn't build**: merge onto the main flow at **`/to-spec`**, then `/to-tickets` and `/implement` as usual.

## Codebase health

Not feature work, just upkeep.

- **`/improve-codebase-architecture`** runs whenever you have a spare moment to keep the codebase good for agents to operate in. It surfaces **deepening opportunities**; picking one _generates an idea_ you can take into the main flow at `/grill-with-docs`.

## Vocabulary underneath

Two model-invoked references that run *beneath* the other skills.

- **`/domain-modeling`**: sharpen the project's *domain* language: challenge a fuzzy term, resolve an overloaded word, record a hard-to-reverse decision as an ADR.
- **`/codebase-design`** is the deep-module vocabulary (module, interface, depth, seam, adapter, leverage, locality) for designing a module's *shape*.

## Standalone

Off the main flow entirely.

- **`/grill-me`**: the same relentless interview as `/grill-with-docs`, but **stateless**. Reach for it when you are **not working in a working directory**.
- **`/grilling`** is the interview primitive itself.
- **`/resolving-merge-conflicts`** works an in-progress merge or rebase conflict hunk by hunk, resolving by **intent**. Never runs `--abort`.
- **`/prototype`** is a small, throwaway program that answers one design question.
- **`/research`**: delegate reading legwork to a **background agent**.
- **`/to-questionnaire`** writes a questionnaire for someone else, when the thing blocking you is in their head, not yours.
- **`/wizard`** is for the steps only a **human** can take: provisioning infrastructure, credentials, CI secrets, an unfamiliar dashboard, a one-off migration.
- **`/wait-what`** re-pitches a message that didn't land, in plain English, using the `CONTEXT.md` vocabulary.
- **`/teach`**: learn a concept over multiple sessions, using the current directory as a stateful workspace.
- **`/loop-me`**: grill toward a workflow spec for a recurring personal or homelab loop (a trigger, a checkpoint, a brief).
- **`/handoff`** writes a portable markdown handoff for a new harness, directory, or colleague. **`/claude-handoff`** does the same but launches a background `claude --bg` agent directly instead of saving a file.
- **`/writing-for-agents`** is the reference for writing documents agents consume: skills, AGENTS.md, pointed-at docs.
- **`/writing-beats`** and **`/writing-shape`** (draft) turn a pile of raw material into an article, beat by beat or paragraph by paragraph.
- **`/unslop`** cuts AI tells from any writing. Applied to everything by default.
- **`/setup-pre-commit`** and **`/git-guardrails-claude-code`** are one-shot repo setup skills, unrelated to the main flow.

## Precondition

**`/install-gjorgji-skills`**: run before your first engineering flow to configure the issue tracker, triage labels, and doc layout the other skills assume.
