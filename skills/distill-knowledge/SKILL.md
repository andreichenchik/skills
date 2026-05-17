---
name: distill-knowledge
description: Distill long conversations, transcripts, articles, or notes into compact, high-signal transferable knowledge. Use when the user asks to extract insights, lessons, principles, mental models, or dense facts from source material.
disable-model-invocation: false
---

# distill-knowledge

Turn long-form material into a small set of standalone, reusable knowledge units. Optimize for **signal per bullet**, not coverage.

## Core filter

Keep a point only if it is:

- **Standalone** — understandable without surrounding bullets or source context.
- **Non-obvious** — not a definition, vague restatement, or generic advice.
- **Transferable** — useful beyond the original person, company, product, or story.
- **Mechanistic** — exposes a cause, tradeoff, constraint, incentive, invariant, or consequence.
- **Model-forming** — can change how someone thinks, designs, decides, reviews, or works.

Prefer points with wider applicability and lower obviousness. A broad, non-obvious principle beats a narrow detail; a narrow detail is worth keeping only if it reveals a unusually sharp mechanism.

Discard chronology, trivia, isolated historical facts, vague claims, repeated ideas, and locally interesting implementation details unless they reveal a reusable mechanism.

## First-principles lens

Prefer bullets that reduce observations to an underlying constraint, incentive, tradeoff, invariant, or mechanism. Do not keep a bullet that only says what happened; keep the principle that explains why it happened or where it applies again.

## Output structure

Organize by **type of knowledge**, not chronology. Use topic sections to make the result easier to read, but treat them as provisional.

Possible category families:

- Product / user value / adoption
- Engineering / architecture / tooling
- Mental models / first principles
- Team / process / strategy
- Technical explainers / mechanisms
- Future-facing bets / second-order effects
- Personal working principles

Choose only sections that fit the source. Rename, merge, split, reorder, or invent sections when that makes the final result clearer. Do not create a section unless it contains multiple strong bullets that belong together.

## Bullet style

Use dense standalone bullets:

```markdown
- **Short thesis.** One to three sentences explaining the mechanism, tradeoff, or implication. The point should retain value even when copied elsewhere.
```

Prefer one strong synthesized bullet over several adjacent micro-facts. Keep inseparable tradeoffs inside the same bullet.

## Technical explainers

When the source explains how something works, keep the mechanism together as one compact block. Do not split theory into many “insight” fragments.

A technical explainer should answer:

- what problem the mechanism solves;
- how it works at a useful level of abstraction;
- what tradeoff or limitation it introduces.

## Signal budget

Use a budget to force ranking:

- Default: **20–35 bullets** for one substantial source.
- Rich source: up to **45 bullets**.
- Exhaustive extraction: up to **60 bullets**, only when explicitly requested.
- Technical explainers: usually **3–7 blocks** maximum.

If the draft exceeds the budget, merge or delete. Each bullet should be worth rereading later.

## Top highlights

Always identify the **top 5 bullets** from the final set: the most important, transferable, non-obvious, and model-forming points from the source.

Mark them clearly in the final output, either by adding a `⭐` marker to the bullet or by adding a short `Top 5` section before the categorized list. Do not create separate weaker summaries; reuse or point to the strongest final bullets.

## Ranking pass

For substantial outputs:

1. Draft candidate bullets with provisional sections.
2. Write them to a temporary scratch file outside the vault, for example under `/tmp`.
3. Read the scratch file back as a standalone list.
4. Reconsider the sectioning: rename, merge, split, reorder, or remove sections based on the strongest bullets, not on the original draft structure.
5. Move bullets to the section where they create the clearest comparison set.
6. Rank bullets by signal: wider applicability, lower obviousness, sharper mechanism, clearer tradeoff, and higher reuse value.
7. Select the top 5 bullets from the surviving set and mark them as highlights.
8. Remove bullets that feel weak compared with the strongest bullets, even if they are true.
9. Merge bullets that teach the same lesson.
10. Delete the scratch file unless the user asks to keep it.

This prevents accumulation bias and structure lock-in: a point can pass the basic filter and still not deserve space in the final answer, and an initial section can survive only because it was drafted early.

## Final check

Before returning, delete any bullet that:

- needs previous bullets to make sense;
- merely reports an event;
- lacks “why it matters”;
- lacks an underlying mechanism or first-principles grounding;
- could be guessed without reading the source;
- survives only because it was found, not because it competes well with the rest.
