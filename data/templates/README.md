# Fill-in templates

Copy these files into the matching paths under **`data/`** at your project root (create folders if missing). Rename placeholders (`section_TEMPLATE.yaml` → `algebra_period_1.yaml`, etc.). You can edit YAML **by hand** or **through a coding agent** (describe the change, review the diff); the latter is the main habit this kit is built for. See [`../README.md`](../README.md) and [`../../ADOPTION.md`](../../ADOPTION.md#the-world-of-plain-text-and-why-version-control-matters) for why plain text + version control matter.

| Template | Copy to |
|----------|---------|
| `school/context.yaml` | `data/school/context.yaml` |
| `school/calendar_2026-27.yaml` | `data/school/calendar_<YOUR-YEAR>.yaml` — then set `academic_calendar.calendar_reference` in `context.yaml` |
| `sections/section_TEMPLATE.yaml` | `data/sections/<section_id>.yaml` |
| `courses/example_course/scope.yaml` | `data/courses/<course_id>/scope.yaml` — replace `example_course` with your slug |
| `courses/example_course/units/unit_01.yaml` | `data/courses/<course_id>/units/unit_01.yaml` |
| `students/STUDENT_ID_TEMPLATE.yaml` | `data/students/<opaque_id>.yaml` — **one file per student** |

**Fictional school** — The sample `context.yaml` uses a **made-up** institution name for safe demo use. Replace every field with your real (or your own fictional) context.

**Student files** — Start with synthetic IDs only. Expand fields only as your process allows; see `schema/student_profile.yaml` for the full shape.
