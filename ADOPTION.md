# Adoption guide: scope, cost, and safe work with data

**What this is, in one sentence:** a **place to think about your classroom** in text you control—roles the agent can follow, optional structured data, and habits (version control, careful prompting, de-identified data) that make that collaboration reviewable.

Under the hood, these files are **portable instructions** for a coding agent: role skills under `.cursor/skills/`, YAML templates under `data/`, and conventions that pay off with practice. The ambition is not fixed: you might use this as a thin layer of prompts and checklists, or **recursively deepen** it—more schema, scripts, skills tailored to your SIS-shaped exports—until one repo is the **operating system for how you run the room**. Both are valid; adoption is **how much structure you want to carry**, not a single mandated end state.

If something here feels like overhead, treat the roles as **shared language** for team-shaped classroom work; you can adopt them gradually, with or without heavy automation.

## Skills and roles are a living snapshot

The **roles** (Planner, Curriculum Designer, Assessor, Communicator, Co-Teacher, and anything you add later) are a **starting decomposition**. They will **change** as you learn what agents do in your workflow. Skills live in `.cursor/skills/` as **versioned text**—same muscle as code: edit, diff, commit, repeat.

**Writing skills is programming with natural language.** Practical loop: expected output wrong → ask the model to **update the skill** (constraints, steps, examples of what to avoid). Voice feels wrong → **rewrite the persona** or add a short “sounds like this” sample. New edge case → add **only the context** that case needs.

Treat this package as a **pattern and vocabulary** you can fork, trim, or extend for your school and your tools.

---

## The world of plain text (and why version control matters)

You are almost certainly fluent in **documents and spreadsheets** — lesson plans in Google Docs, rosters in Sheets, PDFs from the district. You may have **never intentionally worked in plain text**: a file where what you see on disk is exactly the characters saved, with no hidden formatting layer, no merge bubbles, no “smart” paragraph styles behind the scenes.

**Plain text is powerful when paired with markup languages.** A **markup language** adds structure or meaning using visible conventions in that text — headings with `#`, bullets with `-`, or YAML’s `key: value` lines — instead of storing layout in a proprietary binary. **WYSIWYG** (“what you see is what you get”) tools like Docs or Word show you a finished page while hiding the formatting instructions; you click “Heading 1” and the software records something you do not usually edit directly. Markup-first files trade that comfort for **clarity, portability, and automation**: any editor can open them, and tools (including LLMs) can read and write them predictably.

**Why that matters here:** large language models are **especially good at generating and editing plain text with markup** — Markdown, YAML, JSON — because the training signal matches the medium. You can still **edit by hand** when you want to; nothing requires it. The skill to practice is **using the agent to maintain the docs**: you describe the change, review the diff, commit when it is right.

Google and others are shipping impressive assistive features **inside** Docs and similar products, and you could **port these ideas** (roles, checklists, templates) into that world if it fits your workflow. The gap, for now, is usually **real version control**. **Version control** (Git is the common tool) means you can **name a state** of your materials (a commit), **see exactly what changed** line by line, and **return to any named state** whenever you need to — not “undo until it feels right,” and not a folder full of `SY26-27_FINAL`, `SY26-27_FINAL_edited`, and `SY26-27_FINAL_edited_Lena`. If more educators could rely on that habit, a lot of **slug-in-the-filename** chaos and **copies of copies of copies** becomes unnecessary: the history lives in the tool, not in your Downloads folder.

This package assumes you are willing to grow **some** comfort with text files **or** with an agent that edits them on your behalf while you keep **approval and Git history** in human hands.

---

## Agents need structure (and when that structure hardens)

**Coding agents, like people, work better with a shape they can rely on** — headings, fields, filenames, and **clear next-step conventions** across roles so Planner edits stay aligned with Communicator templates. That is pedagogy for the machine: *constraints teach the model where to work.*

Unlike a **deterministic program**, however, there is **no external requirement** on what that shape must be. A compiler or database schema is fixed by someone else’s toolchain; an LLM in chat will happily draft a lesson in prose, a bulleted checklist, or a YAML block — until **you** decide what “canonical” means for your workflow.

Two common ways that freedom **narrows**, and structure starts to behave like **expensive-to-change software**:

1. **You automate against a definition.** If you ask an agent (or a colleague) to write **scripts** that parse, validate, merge, or migrate your files, those programs **assume** a contract: keys, paths, nesting. From then on, “the data definition” and “the code that touches it” move together. Renaming a field is no longer a find-and-replace in one doc; it is a **migration** across tools and prompts.

2. **You grow by layering structure.** School context, calendars, sections, courses, units, student rows, and role skills **stack** into an architecture that feels obvious in hindsight. Each layer was a reasonable next step; together they **couple** skills, templates, examples, and maybe CI. Changing the shape later costs what refactors always cost: coordinated edits, regression risk, and re-teaching the agent in updated skills.

**Implication for adoption:** start as **light** or as **layered** as your patience allows, but treat early schema and path choices as **strategic** — because **depth trades away the cheap option of wholesale redesign** the same way it does in any growing system. The layouts in this repo are **one** coherent stack you can adapt or replace.

---

## How this package is organized

1. **Role skills** — Markdown under `.cursor/skills/` (Planner, Curriculum Designer, Assessor, Communicator, Co-Teacher `Inés Vidal`).
2. **Canonical data schemas** — Structured YAML for school context, sections, student profiles, accommodations, and related shapes: **schema discipline** so agents edit files you can diff and review.
3. **Templates** — Starter YAML you can copy; use synthetic or dummy IDs until your process allows more.
4. **Governance** — Canonical records under `data/` where you use that split; `deliverables/` as snapshots or exports that may lag; **teacher-next** clarity in outputs; co-teacher persona and students-first boundaries.

This package is built for **IDE + skills + human approval** of edits. See [How these skills compose in the IDE](#how-these-skills-compose-in-the-ide) and [`README.md`](README.md#how-skills-compose-in-the-ide).

### Co-teacher name and persona

**Inés Vidal** is the name the model produced when the human author asked it to **name itself** for this project — explicitly **not** “in reference to me,” but in reference to the model’s own engagement with the work (NYC public school teaching context, student-first design). The author then asked for **persona** to give the meta-role a stable voice across sessions and files. LLMs are built to elicit human engagement; the author does not claim to have removed themselves entirely from that calculation, only to have tried to narrow it.

**What the model said about the name:** it tied the choice to hope and to the fact that the work was born out of NYC school teaching. **Mechanically**, naming here is **pattern completion** on training data, not cultural belonging: the output is statistically associated with the prompt and corpus, not a person “choosing” the way a human colleague would.

**Why keep a culturally specific name at all:** a **generic** assistant voice is also a choice — and in practice it often defaults to an unmarked “professional” register that **centers** students who are already overrepresented in ed-tech imaginaries. The co-teacher spec uses specificity to **anchor** moral posture (who sits at the center of the compass when we design) while **refusing** to perform identity: no claimed memories, neighborhoods, or kinship the model does not have. Naming and boundaries are summarized here; you may extend or replace them in your fork.

**Risks others have raised:** including whether a machine wearing a human name from a real-world community can resemble **appropriation** or **ventriloquism**, regardless of intent. The author treats that as a **live** ethical question, not a settled one. **People from the communities the name evokes have standing to disagree** with this design; publishing is offered in that spirit.

**There is no connection to any actual person** named Inés Vidal in this project.

The co-teacher name is kept for **continuity** across these docs; that is a project choice, not a claim that the persona is final or universal.

**If you adopt or fork these skills:** your version may strip out the name and persona, ask a model to define a specific co-teacher for your context, or choose another name — whatever fits where you will be working. Expect **ongoing edits** to persona and boundaries as you use the role (see [Skills and roles are a living snapshot](#skills-and-roles-are-a-living-snapshot)).

**Paths:** the skills reference examples like `data/school/…` and `data/courses/…` because they pair with **file-based canonical metadata**. Map those concepts to **your** layout, or adopt the schemas and templates under `data/` in this package.

---

## What this portable repo offers vs what you still do yourself

| Offered here | You still provide |
|--------------|-------------------|
| Role definitions (ownership, next steps across roles in prose, done checks) | Your school calendar, course codes, policies, and local constraints |
| **`data/schema/`** — field meanings and conventions (no live student data; not machine validation unless you add it) | Interpreting those fields under **your** district’s categories and tools |
| **`data/templates/`** — starter YAML for school context, calendar, section, course scope, unit plan, one student row | **Typing, transforming, or importing** real context (SIS export → opaque IDs, official calendar dates, etc.) |
| Example **verbose** prompts | Your judgment on what is safe to put in a model context |
| Optional links at the end of this file (GitHub narrative, related repo) | **Git**, a **coding-agent** workflow, and usually **data munging** (CSV → YAML, SIS export cleanup, etc.) |
| A clear split between “draft for teacher” vs “send” | District approval, FERPA training, and record-keeping rules |

**Minimum viable adoption:** treat the skills as **checklists and voice constraints** in chat, with **no** student files at first — only synthetic or public calendar facts.

**Deeper adoption:** maintain **canonical data in the repo** (or in gitignored paths) so the agent edits **named files** you can diff and review.

---

## How these skills compose in the IDE

There is **one** adoption model here: a **coding agent in the IDE** where **you** pick the role (or the model matches a skill by description), **review diffs**, and **approve** changes.

- **Invocation** — Use `@planner-role`, `@communicator-role`, etc., or describe work that fits a skill’s stated purpose.
- **One role per focused session** — The model stays in that role’s constraints for the outputs that role owns.
- **Next steps across roles** — When the next step belongs elsewhere, state it clearly: short summary, open questions, and **which role should act next** (in prose, in chat).
- **Co-Teacher** — Open when ownership is fuzzy, two roles’ constraints conflict, or **where something should live** in the repo affects multiple roles. Route everyday lesson drafting, grading, and family comms to **Planner**, **Curriculum Designer**, **Assessor**, or **Communicator**; Co-Teacher focuses on alignment and boundaries.

Optional: if your vendor exposes delegation (e.g. subagents or parallel tasks), you may map each role skill to a separate prompt. See [`README.md`](README.md#how-skills-compose-in-the-ide).

---

## Canonical data vs deliverables

Structured school and course metadata under **`data/`** (paths like `data/courses/*/scope.yaml`, `data/school/calendar*.yaml`, `data/sections/*.yaml` are **illustrative**—adapt to your layout) is the **canonical planning record** when you use that split.

**`deliverables/`** (when present) holds **exports, mirrors, and snapshots** that may legitimately **lag** behind `data/`. Staleness is expected.

**Editing discipline:** When you update canonical files under **`data/`**, refresh **`deliverables/`** when you choose to regenerate named exports, or when a task you are executing requires specific `deliverables/` paths. Routine `data/` edits do not require syncing exports.

The same rules load for agents from [`.cursor/rules/canonical-data-vs-deliverables.mdc`](.cursor/rules/canonical-data-vs-deliverables.mdc).

---

## Prerequisites (please read before feeling bad if it “doesn’t just work”)

### 1. Coding agents (Cursor, Claude Code, similar)

You need a workflow where you can:

- **Invoke** a skill (`@planner-role`, etc.) or paste its gist into a system-style instruction.
- **Read diffs** before accepting changes — especially anything touching student-related paths.
- **Stop** when the model drifts out of role or invents policy.

The skills assume you are the **approver**, not the agent.

**Cost and access:** Cursor, Claude Code, and the underlying model APIs are typically **paid products** (pricing and tiers change). Check current vendor terms before planning adoption for a team or school. **Installing** a coding agent on a district machine may require **IT approval** under your local security policy.

**Ideas beyond this stack:** the **role decomposition**, explicit constraints, and cross-role next-step habits in these docs can inform how you prompt **any** LLM (browser chat, district-approved tools). The **skills-as-files** workflow is what ties this package to Cursor / Claude Code specifically.

### 2. Version control (Git)

Git underpins a **full** text-and-review workflow. See [The world of plain text](#the-world-of-plain-text-and-why-version-control-matters) for *why* named history beats endless duplicate filenames.

- You need to know what changed, **when**, and **why** (commit messages).
- You need to separate **public** repo content from **secrets** (API keys, live rosters) via `.gitignore` and district process.
- Branching or worktrees help when experimenting with scope or calendar overwrites.

If you have never used Git, plan time for a short course or a colleague who can pair with you. **Agent tools lower the bar for editing files; they do not remove the need for review and history.**

**First step that already feels familiar:** if you use **Suggesting** mode in Google Docs, you already review additions and removals before accepting. A **Git diff** is the same habit in a different tool: see what changed line by line, then **commit** when it matches your intent.

### 3. Layered context and “your” school

This package’s examples use **layered YAML**: school context, calendars, section files, per-student profiles. Example data is **synthetic**—a believable shape of the job, not a live timetable.

For your own use you either:

- **Lightweight:** keep a single `context.md` or minimal YAML (bell schedule, term dates, course titles) and ignore the rest of the schema, or  
- **Structured:** adopt or adapt the schemas and templates under `data/` here so skills and files stay aligned.

Either way, **someone** does the work of typing or transforming reality into structured text. The skills do not auto-import from your SIS.

### 4. Prompting as a skill

Long, explicit prompts (constraints, audience, safety, desired artifact shape) reward practice. See `examples/verbose-prompt-example.md`. Copy, trim what does not apply, add three bullets: *context, non-negotiables, output shape.*

---

## FERPA, PII, and working with student-related data (non-legal, practice-oriented)

This is **not legal advice**. Follow your **district data governance**, DPA, and counsel.

**FERPA** (US) protects **education records** tied to identifiable students. Names, IDs that link to a child in your roster, contact info, and many grades/notes qualify. Third parties (including model providers) may be **school officials** only under specific conditions; **do not assume** a consumer chat product is approved.

**Practices that align with cautious school use:**

1. **Prefer de-identification** — Replace names and contact fields with **opaque IDs** (`student_10001`) for anything that might be copied into a cloud agent. Aggregate for class-level planning when possible.
2. **Separate planning from identification** — You can use the system to think through **course shape**, units, and pacing with **no** roster, or with **synthetic** sections only.
3. **Roster in repo only with policy** — If you maintain real rosters in Git, use **private** repos, **encryption at rest** per district rules, and **never** paste full PII into a model prompt “just to explain.”
4. **Git history** — Removing a file later does not erase it from history; treat commits as **durable** and avoid committing PII in the first place.
5. **“Just planning next year’s room”** — Even low-stakes planning can involve **identifiable** lists. If those lists are education records, the same care applies. Synthetic or redacted data is appropriate for **public** demos and open-source trees.

**What we are offering:** patterns that assume **teacher approval**, **experimental / dummy** outputs where noted in role specs, and **file-based** review — not turnkey compliance.

---

## Recommendations

1. **Start without live students** — Use fictional school context and fake IDs until your process is clear.
2. **One role at a time** — e.g. Co-Teacher + Planner for calendar conflicts before touching Assessor or Communicator.
3. **Optional narrative** — A [published case study](https://mrallatta.github.io/classroom-manager/) describes one trajectory with **synthetic** student data; use it as context, not as a guarantee for your district or live rosters.
4. **Rename public synthetic branding** — If you fork or publish data, use a **fictional** school name.
5. **Document your own gates** — When is an artifact “draft” vs “approved for class”? The skills assume explicit gates; your school should name them.
6. **Scope: one teacher’s system (for now)** — This stack centers on **one** teacher-architect maintaining canonical files. Department-wide or multi-teacher coordination will need **conventions you define** (or a fork) for shared repos, merged rosters, and shared workflows.

---

## Related files

- [`README.md`](README.md) — Install paths, how skills compose in the IDE  
- [`examples/verbose-prompt-example.md`](examples/verbose-prompt-example.md) — Prompt templates  
- [`.cursor/rules/canonical-data-vs-deliverables.mdc`](.cursor/rules/canonical-data-vs-deliverables.mdc) — Canonical `data/` vs `deliverables/` policy for agents  
- Optional: [classroom-manager on GitHub](https://github.com/MrAllatta/classroom-manager) — related experiments, extended docs, and publishing history  
- Optional: [GitHub Pages narrative](https://mrallatta.github.io/classroom-manager/) — case-study context
