# PLAN.md Format

`PLAN.md` lives at the workspace root. It captures who the course is for, what they'll take from it, and the outline of how it gets there. Every drafting decision traces back to it.

## Template

```md
# Plan: {Topic}

## Audience
{The single reader persona: who they are, what they already know, why they'd read this}

## What readers can do after
{The concrete outcome the finished course delivers}

## Topic scope
{The domain/concept being explained}

## Lesson outline

### Planned lessons
{Numbered list, one-line description + status marker (draft/reviewed/approved) each — this numbering is the FINAL reading order for the finished course}

### Not yet specified
{Topics known to matter, not yet sharp enough to state as a concrete lesson — fog, not a blank}

## Constraints
{Format, length, tone, time-budget, diagram support (see below), anything else that bounds the approach}

## Out of scope
{Adjacent topics explicitly excluded from this course}
```

## Producing it: a two-stage interview

1. **Environment check, first**: does the expert's Confluence instance have a Mermaid-rendering marketplace app installed? This is a fact about the target platform, not a content decision — ask it before anything else and record the answer under `Constraints`. It decides how every diagram in the course gets drafted and published (see `SKILL.md`'s Confluence gaps section).
2. **Stage one — audience and outcome.** Pin down `Audience` and `What readers can do after` before anything else. You can't sensibly map content territory until you know who it's for and what "done" looks like for them.
3. **Stage two — breadth-first content mapping.** Fan out across the domain with the expert — the same shape as charting a wayfinder map: destination first, then frontier. Seed `Planned lessons` with what's already sharp enough to draft, and `Not yet specified` with what's real but not yet nameable. Seed `reference/glossary.md` with the domain's key terms at the same time (see `GLOSSARY-FORMAT.md`) — non-linear drafting later needs a shared vocabulary anchor from the start.

## The outline is a pool, not a syllabus

`Planned lessons` and `Not yet specified` work like a wayfinder map's frontier and fog. Some lessons are sharp enough to draft now; others are real but not yet nameable. This flexibility is scoped to the **authoring** process only: the domain expert picks a starting point and explores outward, drafting whichever planned lesson interests them next — driven by their own judgment, not an algorithm. Drafting one lesson can graduate nearby fog into new planned entries, or reshape existing ones.

The **published** course is always strictly sequential for the reader, regardless of drafting order. The numbering in `Planned lessons` is that final reading order, decided (and revised) as the plan evolves — not a mandate on which order to write them in.

## Status tracking

Each entry in `Planned lessons` carries a status: `draft` / `reviewed` / `approved`. This lives here, in `PLAN.md` — not as frontmatter in the lesson file (which pastes straight into Confluence and shouldn't carry workflow metadata), and not in a separate status file (would just duplicate this list).

## Rules

- **One plan per workspace.** If the expert wants to explain two unrelated things, that's two workspaces.
- **Concrete over abstract**, same discipline as any planning interview: push back if the audience or outcome is vague. "New engineers on the team who've never touched market microstructure" beats "people who want to learn finance."
- **Revise in place as the outline evolves.** Confirm with the domain expert before structural changes to `Planned lessons` or `Not yet specified` — don't silently restructure their course.
- **Keep it short.** If `PLAN.md` runs past a couple of screens, the `Lesson outline` has probably grown lesson-length content that belongs in the lessons themselves.
