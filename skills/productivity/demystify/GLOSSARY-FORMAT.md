# GLOSSARY.md Format

`reference/glossary.md` is the domain's canonical vocabulary. Every lesson adheres to its terminology. Unlike `teach`'s `GLOSSARY.md`, this is published alongside the lessons as a reader-facing reference — a fast lookup, not just an internal authoring aid.

## Structure

```md
# {Topic} Glossary

{One or two sentence description of the topic this glossary covers.}

## Terms

**Hypertrophy**:
Muscle growth driven by mechanical tension and metabolic stress over repeated training sessions.
_Avoid_: Bulking, getting big

**Progressive overload**:
Systematically increasing the demand on a muscle over time — via load, volume, or intensity.
_Avoid_: Pushing harder, levelling up
```

## Rules

- **Seeded upfront, not promoted retrospectively.** `teach` only adds a term once the *learner* demonstrates understanding — that trigger doesn't apply here, since the domain expert already knows the material; there's no comprehension gate to wait on. Seed the glossary with the domain's key terms during `PLAN.md`'s stage-two content-mapping interview (see `PLAN-FORMAT.md`), before any lesson is drafted. This matters more here than in `teach`: lessons are drafted non-linearly (the expert explores the outline outward, not top-to-bottom), so two lessons drafted far apart with no shared anchor risk inventing different terms for the same concept.
- **Definitions can still sharpen retrospectively** as lessons get drafted — the glossary just doesn't start empty.
- **Pure terminology decisions land here, not in a decision record.** If a term needs a definition, a rename, or an "avoid this synonym" call, that's a glossary edit. `decision-records/` is reserved for what the glossary can't hold — tone, scope, factual corrections (see `DECISION-RECORD-FORMAT.md`).
- **Be opinionated.** When several words exist for the same concept, pick the best one and list the rest as aliases to avoid.
- **Keep definitions tight.** One or two sentences. Define what the term IS, not what it does or how to do it.
- **Use the glossary's own terms inside other definitions.** Once a term is in the glossary, prefer it everywhere, including inside other definitions.
- **Group under subheadings** when natural clusters emerge. A flat list is fine when terms cohere.
- **Flag ambiguities explicitly.** If a term is used loosely in the wider field, note the resolution in this workspace.
- **Revise in place as understanding deepens.** Update a definition rather than leaving a stale one.
- **No clickable cross-links** — neither between glossary terms nor from a term to the lesson that introduces it. Confluence can only anchor-link to real headings (a native hover-and-click affordance, not something Markdown source can produce) or via its Anchor macro at a non-heading point — impractical to place at dozens of individual bold-text terms. Refer to another term or a lesson by name in plain prose instead (e.g. "the **reservation price** shifts..." or "(introduced in the lesson on measuring volatility)") — a mention by name stays true regardless of how the published pages end up organized, and needs no fixup after publishing.
- **A term's definition can include a `panel:` placeholder**, same fenced convention as lessons (see `LESSON-FORMAT.md`), when something about it is worth calling out — e.g. flagging that a commonly-cited source is inconsistent on this exact point.
