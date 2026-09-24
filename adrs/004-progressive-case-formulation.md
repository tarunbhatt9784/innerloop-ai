# ADR 004 - Progressive Case Formulation and Rule Tightening

## Status
Proposed.

## Decision
Add a self-learning layer that maintains a dynamic case formulation and progressively tightens rules and heuristics based on experiment outcomes and observed patterns.

## Context
Clinical psychologists refine their understanding of a client over multiple sessions:
- Session 1: Form initial hypotheses from history and presentation
- Sessions 2-N: Test hypotheses against outcomes, revise formulation
- Longitudinal: Build a robust model of what patterns are real, what works, what doesn't

InnerLoop currently does session 1 (initial analysis + one experiment) but lacks the feedback loop and progressive refinement that makes therapy effective.

## Decision
Introduce a **Case Formulation Agent** and **Experiment Outcome Reviewer** that:

1. After each journal: review what happened with the previous experiment
2. Update confidence in candidate patterns based on evidence
3. Promote patterns to durable status when sufficiently supported
4. Flag contradictions or surprises (hypothesis-breaking evidence)
5. Tighten action-selection heuristics based on what experiments actually worked
6. Maintain a "case model" that evolves with each journal entry

This mirrors the clinical practice of "adaptive treatment planning" — the formulation improves as data accumulates.

## Rationale
- Without feedback, the system cannot learn what works for this specific user
- Clinical effectiveness requires testing hypotheses, not just forming them
- Progressive refinement prevents "stale" beliefs from old entries
- A user-specific case model beats generic advice

## Consequences
- Additional storage in innerloop-memory: experiment outcomes, case formulation snapshots, rule tightening log
- New agents and specs required
- Memory writes must track confidence and evolution (not just overwrite)
- Orchestrator must retrieve prior experiments and their outcomes
- The system becomes personalized over time, but slower to bootstrap (needs multiple journals to warm up)
