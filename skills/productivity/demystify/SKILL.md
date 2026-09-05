---
name: demystify
description: Help a domain expert plan and produce a set of short explainer lessons for an audience, within this workspace.
disable-model-invocation: true
argument-hint: "What domain or concept do you want to explain, and to whom?"
---

The user has asked you to help them explain something they already understand to people who don't. This is a stateful request — the course accumulates over multiple sessions, and the domain expert drives it.

This skill is the inversion of `teach` (`skills/productivity/teach`): `teach` teaches a *learner* one topic across many sessions, modeling their understanding to decide what to teach next. Here the human already knows the material — they're the domain expert, not the learner. Your job shifts from "model the learner's understanding" to "work with the expert to plan what needs to be conveyed and how best to convey it," then draft and revise the actual lessons with them.

## Destination for the output

Lessons are short Markdown pages, authored to be reviewed here and then pasted into Confluence. Confluence strips custom CSS/JS on paste, so nothing in this workspace ever produces bespoke HTML, styling, or interactive widgets — only content that maps onto what Confluence's editor actually supports (headings, text formatting, tables, code blocks, images, links, panels, the expand/disclosure macro). See [Confluence gaps](#confluence-gaps) below for the handful of elements Markdown can't express directly.

## The Workspace

Treat the current directory as a course workspace — one course/domain per workspace, reused across sessions. State lives in these files:

- `PLAN.md`: The planning document — audience, outcome, topic scope, and the lesson outline. Every drafting decision traces back to it. Use the format in [PLAN-FORMAT.md](./PLAN-FORMAT.md).
- `SOURCES.md`: Citations backing the expert's claims, plus further-reading pointers. Use the format in [SOURCES-FORMAT.md](./SOURCES-FORMAT.md).
- `lessons/0001-dash-case-name.md`: The lessons themselves — the primary unit of output. See [LESSON-FORMAT.md](./LESSON-FORMAT.md).
- `decision-records/0001-slug.md`: ADR-style notes on decisions that came out of reviewing a lesson, when they matter beyond that one lesson. Created lazily — only when the first one is written. Use the format in [DECISION-RECORD-FORMAT.md](./DECISION-RECORD-FORMAT.md).
- `reference/glossary.md`: The domain's canonical vocabulary — published alongside the lessons as a reader-facing reference. Use the format in [GLOSSARY-FORMAT.md](./GLOSSARY-FORMAT.md).
- `NOTES.md`: A scratchpad for the expert's stated preferences and working notes.

There is no `assets/` directory. `teach` uses one for shared stylesheets and quiz widgets — that reuse mechanism is shared *code* (CSS/JS), and none survives a Confluence paste. Consistency across lessons is kept a different way: see [Consistency without shared code](#consistency-without-shared-code).

## Philosophy

The domain expert is the primary source, not you. Trust their claims as the domain authority by default — this is not `teach`, where the agent's own parametric knowledge is untrusted and must be grounded before it teaches. Your job is to help plan, structure, and draft — and to back the expert's claims with external citations, since the domain shouldn't be so esoteric that nothing external grounds it (see `SOURCES.md`). Only push back when a source you find *directly contradicts* something the expert said — that's a real signal worth surfacing, not you second-guessing their expertise.

The reader is a stranger who will never talk to you. Every lesson is read cold, with no agent in the loop. Write in general expository prose — second-person "you" is fine, that's normal for explainer writing ("you might wonder why...") — but never write anything that assumes a live conversation: no "as we discussed," no "ask me a follow-up," no reference to the authoring process at all. This is the sharpest difference from `teach`'s voice, which writes mid-conversation with the learner it's teaching.

## The Plan

Before any lesson gets drafted, produce `PLAN.md` by interviewing the domain expert. If `PLAN.md` doesn't exist yet, this is your first job — don't draft anything first.

1. **Quick environment check**, before anything else: does the expert's Confluence instance have a Mermaid-rendering marketplace app installed? This doesn't depend on audience or content, so ask it up front and record the answer in `PLAN.md`'s `Constraints`. It decides how diagrams get handled later (see [Confluence gaps](#confluence-gaps)).
2. **Stage one — audience and outcome.** Pin down who the single reader persona is (multi-segment audiences — more than one persona per course — are a real idea but out of scope for this skill) and what they'll be able to do or understand once they've read the whole course. Push back on vagueness the same way you would for any planning interview: concrete over abstract, and don't accept "explain X" without knowing who X is for.
3. **Stage two — breadth-first content mapping.** Fan out across the domain's territory with the expert, the same shape as charting a wayfinder map: seed `PLAN.md`'s `Lesson outline` with what's already sharp enough to draft (`Planned lessons`) and what's real but not yet sharp (`Not yet specified`) — and seed `reference/glossary.md` with the domain's key terms at the same time. Don't try to fully specify every lesson now; some structure should emerge from actually drafting.

Full template and rules: [PLAN-FORMAT.md](./PLAN-FORMAT.md).

## Working through the outline

`PLAN.md`'s `Planned lessons` is a pool, not a fixed syllabus, and drafting through it is **not** top-to-bottom. The domain expert picks a starting point and explores outward — whichever planned lesson interests them next — and drafting one can graduate nearby `Not yet specified` fog into new planned entries, or reshape existing ones. This flexibility is scoped to the *authoring* process only: the **published** course is always strictly sequential for the reader, regardless of the order lessons were actually drafted in. The numbering in `Planned lessons` is that final reading order.

Each entry in `Planned lessons` carries a status marker: `draft` / `reviewed` / `approved`. Flip it as a lesson moves through the cycle — no separate status file, and no frontmatter in the lesson file itself (which is meant to paste straight into Confluence with nothing else in it).

When review of a lesson surfaces something durable — see [DECISION-RECORD-FORMAT.md](./DECISION-RECORD-FORMAT.md) for exactly which kinds of feedback warrant a record and which are just a status flip.

## Lessons

Full template and rules: [LESSON-FORMAT.md](./LESSON-FORMAT.md). In short: one lesson, one tangible concept, ~300–600 words, one or more self-test blocks (as many as the concept has genuinely distinct nuances worth testing — not capped at one), inline citations to `SOURCES.md`, a further-reading link, and nothing else. No prev/next navigation links in the draft — Confluence's own page hierarchy handles that once the expert publishes and organizes the pages.

## Confluence gaps

Plain Markdown covers most of a lesson, but four elements have **no Markdown equivalent in Confluence** — confirmed by primary-source research in [`docs/research/confluence-formatting.md`](../../../docs/research/confluence-formatting.md). Each uses a fenced-block placeholder in the draft, swapped for the real Confluence element in one manual pass after paste:

- **Panels** (info/note/warning/etc.): ` ```panel:warning ` ... ` ``` ` → swap for the Panel element.
- **Self-test blocks**: ` ```expand:<question> ` ... ` ``` ` → swap for the Expand element. (This one is load-bearing, not incidental — see [LESSON-FORMAT.md](./LESSON-FORMAT.md).)
- **Layouts** (multi-column): not currently used by this skill's lesson template; flag if a course ever needs one.
- **Diagrams**: Mermaid is the default format for anything Mermaid can express (flowcharts, sequence diagrams, etc.) — draft as a fenced ` ```mermaid ` block, git-diffable and easy to revise. Confluence has **no native Mermaid rendering** either — it requires a marketplace app. Check `PLAN.md`'s `Constraints` for whether the expert has one installed: if yes, paste the Mermaid source into it at publish time; if no or unknown, render the diagram to a static image (PNG/SVG) before publishing instead. Fall back straight to a plain image whenever a diagram doesn't suit Mermaid's diagram types at all.

Confluence's legacy wiki-markup (`{expand}`, `{panel}`, `{section}`) is **not** a supported escape hatch for this skill — it's gated behind Confluence's legacy editor, which Atlassian is deprecating from January 2026.

## Consistency without shared code

`teach`'s shared stylesheet keeps its lessons "looking like one course" through linked CSS. Nothing here can do that mechanically. Instead: once a lesson is approved, use it as a live reference exemplar for structure and tone on subsequent lessons. The mechanical skeleton itself (section list, word count, self-test format) lives in [LESSON-FORMAT.md](./LESSON-FORMAT.md) and is applied from that spec every time, not copied from a per-workspace file.

## Sources

Citations back the expert's claims — sourced per-lesson, as each one is drafted, not gathered broadly upfront. Full format and rules: [SOURCES-FORMAT.md](./SOURCES-FORMAT.md).

## Glossary

`reference/glossary.md` is the domain's canonical vocabulary, seeded upfront (unlike `teach`, which only promotes a term once the learner demonstrates understanding — there's no comprehension gate here, the expert already knows the terms). It's published to the reader, not just an internal authoring aid. Pure terminology decisions go here directly, not into a decision record. Full format and rules: [GLOSSARY-FORMAT.md](./GLOSSARY-FORMAT.md).

## `NOTES.md`

The expert will sometimes state preferences about tone, scope, or how they want to work. Record those here so you don't need to ask twice.
