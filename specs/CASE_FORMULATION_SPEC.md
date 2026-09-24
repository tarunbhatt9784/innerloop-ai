# Case Formulation Spec

## Purpose

Maintain and evolve a coherent case formulation (model of the user) that improves with each journal entry. A case formulation is a psychologist's working hypothesis about how the client's patterns fit together, what drives them, and what's most likely to help.

## What is a case formulation

A case formulation is NOT a diagnosis. It is:

- A narrative model linking presenting patterns (e.g., rushing, burnout, distraction)
- Inferred root mechanisms (e.g., desire for control + fear of failure)
- Environmental/contextual factors (e.g., financial pressure, caregiving load)
- What interventions have been tested and what the user's response was
- Confidence levels for each component (backed by journal evidence, not assumption)

Example of a formulation component:
```
Pattern: "Rushes to finish tasks rather than stay in process"
Possible mechanism: May reflect avoidance of present-moment discomfort or perfectionism
Evidence: Reported in 3 journal dates, observed in real time during journaling
Confidence: medium (appears across multiple activities but still in early data)
Tested intervention: "single-hand shower awareness 20-30 sec" — outcome pending
Alternative hypothesis: Habit driven by deadline-driven work history (testable with more data)
```

## Structure

A case formulation lives in `innerloop-memory/case-formulation/` and contains:

### 1. Core formulation (`current-formulation.md`)

Maintains the **current best hypothesis** about how the user's key patterns fit together.

```yaml
version: 1
last_updated: YYYY-MM-DD
confidence: low | medium | high  # overall confidence in the model
primary_themes:
  - name: "rushing-past-process"
    confidence: medium
    supporting_evidence:
      - source: 2026-09-23 (shower, kitchen, walking, journaling)
      - observed: in real-time by user
    tested_interventions:
      - experiment_date: 2026-09-23
        action: "single-hand shower 20-30s"
        outcome: pending
    alternative_hypotheses:
      - "may be avoidance of discomfort rather than pure habit"
      - "may relate to work-history with deadlines"
    
  - name: "novelty-excitement-boredom-burnout"
    confidence: medium
    supporting_evidence:
      - source: 2026-09-23 (direct self-report, "standard case with me")
    tested_interventions: []
    note: "Self-identified pattern; needs validation across dates"

contextual_factors:
  - financial_pressure: high (3 mortgages, recurring repairs)
  - caregiving_load: moderate (partner post-surgery, aging parents)
  - health_focus: active (pre-diabetic follow-up, symptom monitoring)
  - prior_therapy_history: "10+ years CBT; not currently engaged"

summary: |
  User experiences burnout characterized by rushing past experiences
  to reach objectives, interrupted attempts at mindfulness, and a
  self-reinforcing cycle where forcing consistency triggers more burnout.
  High concurrent load (financial, caregiving, health) reduces available
  energy for habit change. Prior therapy experience suggests capacity
  for insight and behavior change; current energy constraints argue for
  very low-friction experiments.
```

### 2. Experiment journal (`experiments-outcome-log.md`)

Track what was tried, what happened, and what was learned.

```yaml
- date: 2026-09-23
  experiment_id: exp-001
  action: "single-hand shower awareness, 20-30s at shower start, one-breath fallback"
  hypothesis_tested: "shorter, single-object focus will stick better than sustained mindfulness"
  outcome_status: pending
  
- date: 2026-09-30  # example future entry
  experiment_id: exp-001
  outcome_status: completed
  what_happened: "Attempted 3/7 mornings. Got interrupted twice (partner), intentionally skipped twice (rushed mood), completed as designed once."
  learning: "Fallback worked when resistance high. Duration too short to attach to routine memory. Consider attaching to toothbrush or coffee instead."
  next_refinement: "exp-002: water awareness during tooth-brushing (longer existing routine)."
  case_formulation_update: "Rushing pattern confirmed. Micro-duration experiments vulnerable to being skipped if not anchored to strong existing habit."
```

### 3. Confidence evolution (`confidence-log.md`)

Track how confidence in each pattern changes over time. This prevents stale beliefs.

```yaml
pattern: rushing-past-process
entries:
  - date: 2026-09-23
    confidence: medium
    reason: "First observation, consistent across 4 activities in single entry. Real-time self-observation. Awaiting multi-date confirmation."
  
  - date: 2026-09-30  # example
    confidence: high
    reason: "Confirmed again in new journal. Experiment revealed micro-habits are vulnerable to skipping. Mechanism likely both habit + avoidance of discomfort."
    
  - date: 2026-10-07  # example
    confidence: medium-to-high
    reason: "Still present but user successfully completed 1/7 attempts despite constraints. May be modifiable. Hypothesis about 'attachment to stronger routine' supported."
```

## When to update the case formulation

**After each new journal entry**, run through:

1. **Outcome review**: Did the previous experiment happen? What resulted?
2. **Pattern confirmation**: Did patterns observed in prior journals show up again?
3. **New evidence**: Any new patterns, contradictions, or surprises?
4. **Confidence adjustment**: Raise, lower, or hold confidence based on evidence
5. **Hypothesis refinement**: Update alternative hypotheses based on outcome

## Promotion rules for formulation components

A pattern or mechanism may be promoted from candidate to "core formulation" when:

- **Repeated across 3+ journal dates** (shows stability, not just one-day state)
- **Successfully predicted** (formulation said X would happen, X happened)
- **Tested experimentally** (an intervention was designed from the pattern; outcome known)
- **User-confirmed** (user agrees "yes, that's accurate and useful")

A pattern or mechanism should be **downgraded or archived** when:

- **Contradicted by new evidence** (appears once, then stops appearing)
- **Outcome didn't support the hypothesis** (thought rushing was avoidance, but user showed up fully present when task was low-friction)
- **Superseded by a better explanation** (simpler mechanism that explains same evidence)

## Contrast with memory spec

- **Memory spec** (`MEMORY_SPEC.md`) governs individual pattern entries and learnings
- **Case formulation spec** governs the coherent whole — how patterns relate to each other and to interventions

A single memory entry (e.g., "rushing-past-process" pattern) is a building block. The case formulation is the assembled model.

## Privacy

The case formulation is derived information only — no raw journal text, no unnecessary third-party names, no sensitive details (e.g., account names, specific addresses, medical diagnoses). The goal is a usable model, not a case file.

## Idempotency

Updating the case formulation twice on the same date should not duplicate entries. Use timestamps and version fields to prevent duplicate snapshots.
