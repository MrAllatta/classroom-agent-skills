# Canonical data layout (templates + schemas)

This folder holds **schemas and starter templates** for structured school and course metadata that align with the role skills. Use it to **fill in your own school context** beside the skills in your project.

## YAML in one breath

**YAML** (the format of these templates) is **both human-readable and machine-readable**: indentation and `key: value` lines are meant for people to scan, while scripts and agents can parse them reliably. You **may** open a template in any text editor and type by hand; you **do not** have to. In this workflow the practical skill is often **asking a coding agent to apply edits** (“add these no-school dates,” “insert student `1000042` into section `SEC-01`”) and then **reading the diff** before you save. That pairs YAML’s clarity with the fact that **LLMs handle plain structured text well**. For the bigger picture — plain text vs WYSIWYG, Docs vs Git — read [`../ADOPTION.md`](../ADOPTION.md#the-world-of-plain-text-and-why-version-control-matters).

### Same facts in prose vs YAML

In a Google Doc you might write: *Course: Algebra I. Sections: Period 1, Period 3. School year: 2026–27.*

The same information in YAML looks like this — same facts, structured so both you and an agent can find them by name:

```yaml
course: Algebra I
sections:
  - Period 1
  - Period 3
school_year: "2026-27"
```

Lists use indentation under a key; quotes around `school_year` keep the hyphen from being read as syntax.

| Path | What it is |
|------|------------|
| `schema/` | **Field definitions and conventions** — what each key *means* (not student records). These files document the intended shape; they are **not** JSON Schema or another machine-enforced format unless **you** add a validator. Safe to read in agent context. |
| `templates/` | **Starter YAML** — copy into `school/`, `sections/`, `courses/`, `students/` and edit. See `templates/README.md`. |

**You do not need to read everything in `schema/` to start.** Copy and edit `templates/` (or ask an agent to edit them); open `schema/` when you need the full meaning of a field or are aligning custom keys with the role skills.

## Layers

1. **School** (`school/`) — identity, calendar pointer, privacy gate. No student PII.  
2. **Sections** (`sections/`) — one file per class section; roster as **opaque IDs** only.  
3. **Students** (`students/`) — one file per learner. **High sensitivity**; see [`../ADOPTION.md`](../ADOPTION.md).  
4. **Courses** (`courses/<course_id>/`) — shared `scope.yaml` and optional `units/` unit plans.

**Why “layers” matter for design:** each level is useful on its own, but together they form a **stack** that skills and any **automation** you add will assume. If you later rename keys or split folders, you are not only editing YAML — you are maintaining **contracts** (scripts, prompts, role paths). For the fuller idea — agents need structure, but nothing forces one schema until you **code against it** or **grow depth** — see [`../ADOPTION.md` § Agents need structure](../ADOPTION.md#agents-need-structure-and-when-that-structure-hardens).

**Canonical `data/` vs exports:** If you also keep a `deliverables/` (or similar) export tree, see [`../ADOPTION.md` § Canonical data vs deliverables](../ADOPTION.md#canonical-data-vs-deliverables) and [`../.cursor/rules/canonical-data-vs-deliverables.mdc`](../.cursor/rules/canonical-data-vs-deliverables.mdc).

## Privacy

- Follow your district’s data rules. Do not put **names, contacts, or dates of birth** into model prompts; keep them in files you control (and consider `.gitignore` for real rosters).  
- `schema/student_profile.yaml` marks **sensitive** fields and experimental/production expectations.

## Skills alignment

Role skills reference paths like `data/school/calendar_<year>.yaml` and `data/courses/.../scope.yaml`. If you use this layout under your project root, those references stay meaningful. **Schemas and templates evolve** with the skills that mention them — update both when your workflow discovers a gap (see [`../README.md`](../README.md) and [`../ADOPTION.md`](../ADOPTION.md#skills-and-roles-are-a-living-snapshot)).
