# Skill inventory

Source: `~/.agents/skills` (symlinked into `~/.claude/skills`). Reviewed one by one; status starts at "not reviewed" for everything.

Legend: not reviewed · keep · rewrite · drop

## Engineering

| Skill | Description | Status |
|---|---|---|
| ask-matt | Router over the skills in this repo — asks which skill or flow fits your situation. | superseded by `ask-gjorgji` (`skills/ask-gjorgji`) — final flow written now that the full skill set is settled |
| code-review | Reviews changes since a fixed point along Standards + Spec axes, in parallel sub-agents. | keep — copied to `skills/code-review`; reference updated to `/install-gjorgji-skills` |
| codebase-design | Shared vocabulary for designing deep modules and finding deepening opportunities. | keep — copied to `skills/codebase-design` |
| diagnosing-bugs | Diagnosis loop for hard bugs and performance regressions. | keep — copied to `skills/diagnosing-bugs` |
| domain-modeling | Builds and sharpens a project's domain model (CONTEXT.md, ADRs). | keep — copied to `skills/domain-modeling` |
| grill-with-docs | Relentless interview to sharpen a plan or design; also produces ADRs and a glossary as it goes. | keep — copied to `skills/grill-with-docs`; depends on `grilling` + `domain-modeling` |
| implement | Implements a piece of work based on a spec or set of tickets. | keep — copied to `skills/implement`; depends on `tdd` + `code-review` |
| improve-codebase-architecture | Scans a codebase for deepening opportunities, presents an HTML report, then grills through a pick. | keep — copied to `skills/improve-codebase-architecture`; depends on `codebase-design`, `grilling`, `domain-modeling` |
| prototype | Builds a throwaway prototype to answer a design question. | keep — copied to `skills/prototype` |
| research | Investigates a question against primary sources, writes findings to a markdown file. | keep — copied to `skills/research` |
| resolving-merge-conflicts | Resolves an in-progress git merge/rebase conflict. | keep — copied to `skills/resolving-merge-conflicts` |
| setup-skills-base | One-time setup: issue tracker, triage labels, domain doc layout for the other engineering skills. | renamed to `install-gjorgji-skills`, copied to `skills/install-gjorgji-skills` (third-party references scrubbed from SKILL.md, agents/openai.yaml, triage-labels.md) |
| tdd | Test-driven development: red-green-refactor, integration tests. | keep — copied to `skills/tdd`; depends on `codebase-design`, `code-review` |
| to-spec | Turns the current conversation into a spec and publishes it to the issue tracker. | keep — copied to `skills/to-spec`; reference updated to `/install-gjorgji-skills` |
| to-tickets | Breaks a plan/spec/conversation into tracer-bullet tickets with blocking edges, published to the tracker. | keep — copied to `skills/to-tickets`; references updated to `/install-gjorgji-skills` |
| triage | Moves issues and external PRs through a triage state machine; categorizes, verifies, writes agent-ready briefs. | keep — copied to `skills/triage`; reference updated to `/install-gjorgji-skills`; depends on `grilling`, `domain-modeling` |
| wayfinder | Plans large multi-session work as a shared map of decision tickets, resolved one at a time. | keep — copied to `skills/wayfinder`; reference updated to `/install-gjorgji-skills`; depends on `grilling`, `domain-modeling`, `research`, `prototype` |
| wizard | Generates an interactive bash wizard for steps only a human can perform (infra, credentials, dashboards). | keep — copied to `skills/wizard` |
| find-skills | Helps discover and install skills that match a described need. | drop — generic third-party skills.sh discovery tooling, not a personal/authored skill |
| setup-pre-commit | Sets up Husky pre-commit hooks with lint-staged, type checking, and tests. | keep — copied to `skills/setup-pre-commit` |
| git-guardrails-claude-code | Sets up hooks to block dangerous git commands (push, reset --hard, clean, branch -D). | keep — copied to `skills/git-guardrails-claude-code` |

## Productivity

| Skill | Description | Status |
|---|---|---|
| grill-me | A relentless interview to sharpen a plan or design. | keep — copied to `skills/grill-me`; depends on `grilling` |
| grilling | Grills the user relentlessly about a plan, decision, or idea. | keep — copied to `skills/grilling`; foundational, depended on by triage, wayfinder, improve-codebase-architecture, grill-with-docs |
| handoff | Compacts the current conversation into a handoff document for another agent. | keep — copied to `skills/handoff` |
| claude-handoff | Hands the current conversation off to a fresh background agent that picks up the work immediately. | keep — copied to `skills/claude-handoff` |
| loop-me | Grills about specs for the workflows to build, within the current workspace. | keep — copied to `skills/loop-me`; depends on `grilling` |
| teach | Teaches the user a new skill or concept, within the current workspace. | keep — copied to `skills/teach` |
| to-questionnaire | Turns a decision you can't fully answer into a questionnaire for someone else to fill in. | keep — copied to `skills/to-questionnaire` |
| wait-what | Stops and asks for a re-pitch when the last message didn't land. | keep — copied to `skills/wait-what` |
| writing-for-agents | Writing documents for agents — creating/editing skills, AGENTS.md, CLAUDE.md. | keep — copied to `skills/writing-for-agents` |
| unslop | Cuts AI tells from any writing. Applied globally already via CLAUDE.md. | keep — copied to `skills/unslop` |
| writing-beats | Assembles raw material into a journey of beats, grounding each term before it's leaned on. | keep (draft) — copied to `skills/writing-beats`; carried over as in-progress, overlaps with `writing-shape`, missing its upstream "explore" counterpart (`writing-fragments`) |
| writing-shape | Shapes raw material into an article, paragraph by paragraph. | keep (draft) — copied to `skills/writing-shape`; carried over as in-progress, overlaps with `writing-beats`, missing its upstream "explore" counterpart (`writing-fragments`) |

## Misc / uncategorized

| Skill | Description | Status |
|---|---|---|
| microsoft-foundry | Deploy/evaluate/fine-tune Azure AI Foundry agents end-to-end. Work-specific — likely out of scope for a personal catalog. | drop — vendor-authored (Microsoft, MIT license, v1.1.25), work-specific Azure tooling |

## Not in scope (project-specific, not personal skills)

These live under `~/.claude/skills` as real directories rather than symlinks to `~/.agents/skills`, and are tied to specific client/work codebases rather than being general-purpose: `azure-appservice-databricks`, `databricks-tenant-ingestion`, `hybrid-pg-databricks`, `loyalty-points-platform`.
