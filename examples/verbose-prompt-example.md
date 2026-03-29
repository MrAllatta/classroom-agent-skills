# Example: verbose prompting style

This is a **fictional** composite of how you might open a session when you care about *who* the agent should sound like, *what* to state explicitly, and *which* role owns the work. Verbose prompts encode classroom judgment, compliance caution, and clear role boundaries when the model does not share your building.

**Privacy:** Do not paste **names, parent contact info, or other PII** into chat to “give context.” Point to **de-identified** files in your repo (opaque student IDs) or describe patterns in the aggregate. Follow district policy and see [`ADOPTION.md`](../ADOPTION.md#ferpa-pii-and-working-with-student-related-data-non-legal-practice-oriented).

Copy, trim, or remix. Replace bracketed bits with your context.

---

**Session opener (Co-Teacher + architecture)**

> I’m using the co-teacher role skill. Read it and the linked co-teacher spec before doing anything else.
>
> **Context:** I’m a secondary teacher in NYC. The job is team-shaped: planning, pacing, assessment, family communication, and reporting all at once. I’m not asking for a generic lesson plan — I’m trying to keep *one coherent system* so I’m not gluing five partial tools in my head every night.
>
> **Non-negotiables:**  
> - Students stay at the center; no cute shorthand that flattens real kids.  
> - Anything that would go to families or admin is **draft for my approval** only.  
> - Prefer outputs that tell me **what to do next** (prepare, decide, send, reteach, escalate, or confirm no action) — not vague summaries.
>
> **Task:** Review how my repo (or folder) is structured for **cross-role coordination** (calendar, scope, evidence, comms). Name one gap that would break us under real school-year chaos (e.g. fire drill day, mid-unit transfer) and suggest a *small* fix — one commit-sized chunk, not a roadmap essay.

---

**Next: Planner (calendar / pacing)**

> @planner-role  
> **Situation:** We’re entering a short week (holiday / break adjacent). I need pacing that *flags* conflicts instead of silently compressing instructional minutes.  
> **Inputs:** [paste or point to your calendar YAML, bell schedule, or bullet list of blackouts]  
> **Output I need:** A pacing note that lists **conflicts**, **assumptions you had to make**, and **questions only I can answer** — in that order. No student-facing language.

---

**Next: Curriculum Designer (scope / materials)**

> @curriculum-designer-role  
> **Course:** [e.g. Algebra I, Unit 3]  
> **Constraint:** I have [ELL / IEP / mixed-fluency] considerations; differentiation has to be *specific*, not a boilerplate paragraph.  
> **Experimental rule:** Treat everything as **sample / dummy** instructional artifacts unless I explicitly say these are approved for live class.  
> **Output:** Scope or lesson draft plus **explicit trace** to standards and to any assessment/rubric you propose.

---

**Why this style works (short)**

- **Role** is explicit — the model loads the right skill and stays in lane.  
- **Safety** is explicit — drafts vs sends, dummy vs live.  
- **Output shape** is explicit — conflicts first, teacher decisions last.  
- **Honesty** is explicit — you admit what the tool cannot know (your room, your families, your admin).

If prompting does not come naturally, start by copying one block, delete what does not apply, and add three bullets: *context, non-negotiables, desired artifact.*
