# Classroom agent skills

At its core, this is a **place to think about a classroom** in files you own: roles, constraints, and structured school context that a coding agent can help you maintain. Concretely, it ships **portable role skills** and **YAML-oriented schema** so K–12 work can be shaped like a small team—Planner, Curriculum Designer, Assessor, Communicator, plus a Co-Teacher role for coherence and architecture. It runs in coding-agent environments that load project skills (e.g. Cursor, Claude Code); the same ideas can inform prompting elsewhere.

## What you need

- A **coding agent** environment that can use these files (see Quick start below).
- A **paid subscription** where required by that vendor. Pricing changes often — check the vendor’s current pages:

  - [Cursor pricing](https://cursor.com/pricing)
  - [Claude pricing](https://claude.com/pricing)

## What this is

**First principles:** teaching is decision-heavy and context-heavy. This repo is one answer to “where do I hold that context so I can reason about it with help”—not a learning management system, not district software, but a **versioned workspace** (skills + optional canonical data) tuned for how agents read and edit text.

**What you get today:** **skills** under `.cursor/skills/` (Markdown with YAML front matter), **field definitions and starter templates** under `data/schema/` and `data/templates/`. Everything is plain text so you can read, diff, and version it.

**What it can become:** the same stack can stay a light prompt-and-checklist layer, or **grow inward**—more structure, scripts, custom skills—until this project is effectively the **spine** of how you plan, document, and operate *your* room, with tools bootstrapped against *your* files and habits. Nobody’s workflow has to go that far; the point is that the artifact is **extensible**, not a closed app with one ceiling.

The role set is a **starting point**—expect to edit skills and schema as your workflow evolves. For scope, data habits (including FERPA-aware practice), and deeper context, see [**ADOPTION.md**](ADOPTION.md).

## How skills compose in the IDE

This package assumes a **single environment**: a coding agent in an IDE (Cursor, Claude Code, or similar) where **you approve edits** and **choose which skill applies** (or the model picks from each skill’s `description` in the YAML front matter).

- **Human-driven invocation** — `@`-mention a role (e.g. `@planner-role`) or describe work that matches a skill’s description.
- **Stay in role** — For that chat or session, the model produces outputs that role owns.
- **Cross-role work** — When another role should take the next step, say so in prose: short summary and **which role owns the next step**.
- **Co-Teacher** — Use for routing, ambiguous ownership, cross-role conflicts, or repo/schema coherence; route lesson content, grading, and family comms to the specialist roles unless the ask is structural. See the Co-Teacher skill and [ADOPTION.md](ADOPTION.md).

If your tool supports **delegation** (subagents, tasks, or similar), you may treat each role skill as a distinct prompt. Delegation is **optional**; the skills work fully without it.

## Contents

| Path | Purpose |
|------|--------|
| [`ADOPTION.md`](ADOPTION.md) | Adoption guide: scope, plain text / version control, FERPA-aware habits, co-teacher notes |
| [`.cursor/rules/canonical-data-vs-deliverables.mdc`](.cursor/rules/canonical-data-vs-deliverables.mdc) | Short policy: canonical `data/` vs exports / `deliverables/` |
| [`data/README.md`](data/README.md) | How `schema/` and templates relate to the skills |
| [`data/schema/`](data/schema/) | Field definitions and conventions |
| [`data/templates/`](data/templates/) | Starter YAML to copy into your own layout |
| `.cursor/skills/*/` | Role skills (`skill.md` each) |
| [`examples/verbose-prompt-example.md`](examples/verbose-prompt-example.md) | Sample verbose user prompt |

## Quick start — Cursor

1. Copy the `.cursor/skills/` directory from this repo into your project root (merge with any existing `.cursor/skills/`). Copy [`.cursor/rules/canonical-data-vs-deliverables.mdc`](.cursor/rules/canonical-data-vs-deliverables.mdc) if you want the same editing policy loaded for the agent.
2. In chat, `@`-mention a skill (e.g. `@planner-role`) or describe a task that matches the skill’s `description` in the YAML front matter.
3. Skills reference **paths** like `data/` and `deliverables/` as in this package; adapt paths to match your own repo layout.

## Quick start — Claude Code

1. Copy each skill folder into **`.claude/skills/`** at project or user level (see [Claude `.claude` directory](https://code.claude.com/docs/en/claude-directory)).
