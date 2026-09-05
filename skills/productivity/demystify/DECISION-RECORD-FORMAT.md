# Decision Record Format

Decision records live in `decision-records/` and use sequential numbering: `0001-slug.md`, `0002-slug.md`, etc. Create the directory lazily — only when the first one is written.

Renamed from `teach`'s `learning-records/` — there's no learning happening here, so nothing is being *learned*. What survives is the ADR-style shape: durable, decision-grade notes from reviewing a lesson, not a session-by-session activity log.

Unlike `teach`'s learning records, these play **no role in deciding what's next** — that's fully owned by `PLAN.md`'s `Planned lessons` pool and the domain expert's own choice (see `PLAN-FORMAT.md`). This is purely status-adjacent capture: what came out of review that should steer something beyond the lesson currently in front of you.

## Template

```md
# {Short title of the decision}

{1-3 sentences: what was decided or corrected, and why it matters for future lessons.}
```

## When to write one

Write a full record when:

1. **The expert corrects a factual/technical detail** in a drafted lesson.
2. **The expert reveals a cross-cutting scope or tone preference** that should steer *other* lessons, not just the one under review. (A cross-cutting *terminology* preference goes straight to `reference/glossary.md` instead — see `GLOSSARY-FORMAT.md` — not here, to avoid recording the same decision in two places.)
3. **The outline or `PLAN.md` structure changes** as a result of drafting or reviewing a lesson.

A plain lesson approval is **not** a record — just flip its status marker to `approved` in `PLAN.md`. If the approval carries a caveat worth remembering, that caveat is really case 1 or 2 above, and gets a record.

## Supersession

When a later record contradicts an earlier one — the expert's stated preference evolved, even though their domain understanding didn't need to — mark the old record `Status: superseded by DR-NNNN` rather than deleting it. The history of how preferences moved is itself useful signal for later lessons.

## Numbering

Scan `decision-records/` for the highest existing number and increment by one.
