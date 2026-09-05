# Lesson Format

Lessons live in `lessons/`, one file per lesson, titled `0001-dash-case-name.md` where the number increments and is the lesson's final reading position (see `PLAN-FORMAT.md` — drafting order and reading order are not the same thing).

## Template

````md
# {Lesson Title}

{One short framing line: why this matters / what you'll take from it}

{Body content, sub-headed as needed}

```expand:{Self-test question}
{Answer}
```

**Further reading**: [{Title}]({url})
````

A lesson may also include, wherever the content calls for it:

````md
```panel:info
{A callout the reader shouldn't miss, or a caveat/aside}
```
````

````md
```mermaid
{Diagram source, when a diagram suits Mermaid's diagram types}
```
````

## Rules

- **One lesson, one tangible concept.** ~300–600 words, completable in one sitting. If a lesson needs more than that, it's probably two lessons.
- **Self-test blocks are not capped at one.** Include as many as the lesson's concept has genuinely distinct nuances worth testing — typically 1–3 given the length — driven by the content, not a fixed count. If every nuance needs its own self-test and that's more than a handful, the lesson is probably covering more than one concept.
- **Self-test format is fixed**: the fenced block's title *is* the question, its body *is* the answer — free-recall retrieval practice, not multiple choice. Confluence's Expand macro is a plain disclosure container, not a quiz widget, so there's no scoring and no options to bias.
- **Cite inline.** Wherever a claim is backed by an entry in `SOURCES.md`, link it directly in the body: `[claim](url)`. Don't push citations to a separate footnote section.
- **One further-reading link per lesson**, pulled from `SOURCES.md`, at the end.
- **No inter-lesson navigation.** Don't author prev/next links to other lesson files — the published pages are separate Confluence pages with their own URLs, unknown until the expert actually creates them there. Confluence's native page hierarchy and breadcrumbs solve sequential navigation for free once the pages are organized; hand-authored relative links would need re-targeting after every single publish.
- **Voice**: general expository prose. Second-person "you" is fine — normal for explainer writing. Never write anything implying a live conversation with an agent: no "as we discussed," no "ask a follow-up," no reference to the authoring process.
- **Nothing else in the file.** No frontmatter, no workflow metadata — a lesson file is exactly what gets pasted into Confluence.
- **Consistency by exemplar, not by shared file.** Once a lesson is approved, use it as a live reference for structure and tone on the next one — there's no shared stylesheet or component library to enforce this mechanically (see `SKILL.md`'s "Consistency without shared code").
