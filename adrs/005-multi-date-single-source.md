# ADR 005 - Multi-Date Single-Source Processing

## Status
Accepted.

## Context
`JOURNAL_INGESTION_SPEC.md` Section 20 already specified how to *detect and
split* a single PDF containing more than one handwritten journal date
(explicit handwritten date starts a new date scope; printed stationery never
does). What it did not specify was what happens *after* detection:

- how the derived `processed-journals/` records and `INDEX.md` represent a
  source that maps to more than one journal date, and
- how the one-experiment invariant (ADR 003) applies when one processing run
  covers more than one journal date at once (e.g., the user journaled on
  paper for two days before the first run that reads either of them).

`schemas/DAILY_OUTPUT_SCHEMA.md` already had a `journal_dates: []` array at
the top level, suggesting a multi-date run was anticipated at the data-
contract level, but this was never connected to prose in
`PROJECT_INSTRUCTIONS.md`, `DAILY_REFLECTION_SPEC.md`, `orchestrator.md`, or
the processed-journal/INDEX.md convention. `rule-tightening-log.md`
separately states the one-change rule as "exactly one experiment per run" —
consistent with the schema, but likewise never wired through. This gap was
found and closed while processing the framework's first true multi-date
source (`journals/Journal 29-30 september 2026.pdf`, containing handwritten
dates 2026-09-29 and 2026-09-30).

## Decision
1. **Processed records: one file per journal date, not per source file.**
   A multi-date source produces one `processed-journals/YYYY-MM-DD.md` per
   handwritten date it contains, each recording the shared `source_id` and
   its own `page_range`, plus a `companion_dates` field pointing at any
   other date(s) sharing that source. This preserves the existing
   date-keyed convention used everywhere else (pattern `supporting_dates`,
   case-formulation dates, experiment-history rows) instead of introducing
   a second, incompatible per-file addressing scheme.
2. **INDEX.md: one row per journal date, Source ID repeated.** A multi-date
   source appears as N rows sharing one Source ID, each with its own
   Journal Date and Processed Record link.
3. **One-experiment invariant is scoped to the run's output, not to each
   journal-date segment within it.** When a run's evidence spans multiple
   journal dates (a catch-up run), produce one combined daily output whose
   `journal_dates` field lists all dates covered and whose
   `selected_experiment` is the one forward-looking recommendation — not
   one recommendation per date. Evidence extraction, pattern/contrary-
   evidence tracking, and processed-record creation still happen per date.
   This was already the documented intent (rule-tightening-log.md's "Rules
   NOT to Tighten" already said "one experiment per run"; the schema
   already had `journal_dates: []`) — this ADR makes it explicit in the
   specs and agent files that previously only described single-date runs.

## Rationale
- A multi-day catch-up run is not two independent daily check-ins happening
  to be processed in the same sitting — most of the dates involved are
  already in the past by the time processing occurs, so "one experiment to
  try next" per historical date is not actionable and would either
  duplicate advice or force an artificial choice between two competing
  recommendations in one sitting, which ADR 003 exists specifically to
  avoid.
- Keeping processed records date-keyed (rather than combined into one
  multi-date file) avoids a second addressing convention that every other
  date-indexed reference in the system (patterns, case formulation,
  experiment history) would otherwise need to special-case.

## Consequences
- `JOURNAL_INGESTION_SPEC.md`, `PROJECT_INSTRUCTIONS.md`,
  `DAILY_REFLECTION_SPEC.md`, `OUTPUT_SPEC.md`, `orchestrator.md`, and
  `journal-reader.md` gained explicit multi-date-run language (previously
  implicit or absent).
- `innerloop-memory/processed-journals/INDEX.md` gained a documented
  multi-row-per-source convention.
- A future run that reads a source already partially processed (e.g. a new
  mobile note added for one date of a two-date PDF) must update only that
  date's record, per the existing Section 10/24/29.5 re-read rules — this
  was already true and is unaffected by this ADR.
