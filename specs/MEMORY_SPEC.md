# Durable Memory Spec

## Purpose

Persist only information that will improve future reflection quality.

## Memory tiers

### Working observations
Short-lived interpretation from recent entries. Keep in the daily output; do not automatically promote.

### Candidate learning
A potentially useful pattern supported by limited evidence. Store with low/medium confidence only if likely to matter soon.

### Durable pattern
A recurring, behaviourally useful pattern supported across multiple dates or by unusually strong evidence.

### Experiment history
Record what was tried, completion status if known, and observed effect. Failed experiments are valuable data and must not be framed as personal failure.

## Promotion rule

A learning may become durable when at least one is true:

- the same pattern is independently supported on at least three journal dates;
- the user explicitly confirms it as accurate and useful;
- it is a stable preference or constraint repeatedly affecting action design.

One dramatic entry alone does not establish a durable personality trait.

## Storage minimization

Persist the minimum useful abstraction. Avoid verbatim sensitive details and third-party identifiers.

Preferred:
`Evening work conflict often leads to rumination that delays sleep.`

Avoid:
A detailed narrative naming colleagues, locations, and quotations.

## Memory contradictions

If new evidence conflicts with an existing memory, do not overwrite silently. Add contrary evidence, lower confidence if appropriate, and preserve the evolution.

## File strategy

Use one topic-oriented file per durable pattern where possible, plus append-only experiment history. Use stable IDs from `schemas/MEMORY_ENTRY_SCHEMA.md`.
