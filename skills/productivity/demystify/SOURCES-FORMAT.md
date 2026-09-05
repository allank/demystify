# SOURCES.md Format

`SOURCES.md` is the citation trail backing the domain expert's claims. Renamed from `teach`'s `RESOURCES.md` because the job has shifted: `teach`'s resources are what the agent teaches *from*, since its own knowledge is untrusted; here the expert already is the knowledge source, and these citations exist to back their claims for the reader's benefit and credibility.

## Structure

```md
# {Topic} Sources

## Knowledge

- [Title — Author/Publisher](https://example.com)
  {One line: what it covers, when to cite it}

## Further reading

- [Title](https://example.com)
  {One line: why a curious reader might want this}
```

## Rules

- **Sourced per-lesson, not upfront.** Find citations targeted to a lesson's specific claims as it's drafted — sourcing "the whole domain" before any lesson exists means guessing what will need backing. Findings accumulate into this one course-level file.
- **Trust the expert by default.** This is not `teach`'s untrusted-parametric-knowledge situation — don't fact-check every claim against a source. Only surface a found source if it **directly contradicts** something the expert said; that's a real signal worth raising, not you second-guessing their expertise.
- **No "Wisdom (communities)" section.** `teach` has one because the *learner* needs real-world practice partners to keep growing after the course. There's no such loop here — readers aren't in an ongoing relationship with this skill. `Further reading` is a much lighter thing: a courtesy pointer for a curious reader, not a mechanism this skill drives or maintains.
- **Annotate every entry.** A bare link is useless in three months. One line: what it covers, when to cite it.
- **High-trust only.** Prefer primary sources and recognised experts. If a resource is marketing dressed as education, say so in the annotation or leave it out.
- **Prune ruthlessly.** A source that turned out to be wrong, shallow, or off-topic should be removed, not buried.
