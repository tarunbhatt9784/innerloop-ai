# Rule Tightening Spec

## Purpose

Define how the system's own rules and heuristics evolve based on evidence from multiple journals and experiment outcomes. This is the "learning" part of self-learning.

## Scope of rule tightening

Rules that can be tightened based on user-specific evidence:

1. **Action-selection heuristics**: Which types of experiments work for this user?
2. **Friction reducers**: Which friction-reduction strategies actually stick?
3. **Dose calibration**: What's the right size for an experiment?
4. **Timing and cues**: What times/routines work best for habit attachment?
5. **Mechanism hypotheses**: Which psychological mechanisms seem to apply?
6. **Load assessment**: How much concurrent load can this user handle?

Rules that do NOT change:
- Safety policy (danger assessment, override triggers)
- Privacy policy (never store raw journals)
- Framework boundary (one experiment per run, avoid diagnosis)

## Tightening examples

### Example 1: Micro-habit hypothesis

**Initial rule** (after first journal):
```
For high-burnout users with time/energy scarcity, recommend very small,
low-friction experiments (20-30s, attached to existing routines).
```

**After experiment outcome** (e.g., user struggled to remember):
```
Micro-habits work for this user only when attached to STRONG existing
routines (e.g., toothbrushing, shower start). Weaker attachment points
(e.g., "when I think about rushing") fail. Tighten rule: require routine
strength assessment before micro-habit design.
```

**Evidence basis**: Experiment was completed 1/7 times when attached to shower
(moderate routine), 0/7 times when attachment was mental cue.

### Example 2: Novelty-boredom-burnout cycle

**Initial rule** (after first journal):
```
User follows: excitement → boredom → forced consistency → burnout.
Avoid recommending willpower-based approaches.
```

**After experiment outcome** (user successfully stayed with low-friction action):
```
User CAN stay with things if: (a) extremely low friction, (b) shows
tangible progress/difference quickly, (c) is forgiving of lapses.
Tighten rule: use visible-progress strategies (e.g., tracking, small wins)
to interrupt boredom phase. Forced-consistency remains contraindicated.
```

**Evidence basis**: Micro-task completed when it was trivial (3-second fallback) and
provided immediate sensory feedback (feeling water). Did not complete when
framed as "habit building" (longer-term goal).

### Example 3: Load assessment

**Initial rule** (after first journal):
```
User is carrying high financial + caregiving + health load.
Keep experiments cheap (time, money, emotional cost).
```

**After multiple journals** (e.g., property repairs stabilize, partner recovers):
```
Load reduced from "high" to "moderate". Can recommend slightly larger
experiments (e.g., 10-15 min routines instead of 2-3 min).
Tighten thresholds: re-assess load every 2 weeks.
```

**Evidence basis**: Journal entries from Oct 15, Oct 22 show property issue resolved,
partner back to full activity.

## Process for rule tightening

After each experiment outcome review:

1. **Review the original rule** that guided the experiment design
2. **Compare outcome to prediction** (did the rule work?)
3. **Extract the refined rule** if evidence contradicts or extends the original
4. **Document the refinement** in innerloop-memory/rule-tightening-log.md
5. **Apply the refined rule** to the next experiment design

## Rule tightening log

Maintain a decision log in `innerloop-memory/rule-tightening-log.md`:

```yaml
date: 2026-09-30
original_rule: "Micro-habits work for users with high burnout + scarcity"
experiment_reviewed: "single-hand shower awareness"
outcome: "partial (1/7 completion rate, all on days with strong routine presence)"
refined_rule: "Micro-habits viable ONLY if routine strength >= 'daily automatic' (shower, tooth-brushing). Avoid mental-cue attachment for this user."
confidence: medium (based on 1 experiment; need 2-3 more data points)
next_check_date: 2026-10-21
applied_to: "exp-002 (coffee-based routine instead of mental cue)"
```

## Confidence in refined rules

A refined rule is more confident when:
- **Multiple experiments** follow the same pattern (not just one outcome)
- **Multiple mechanisms** tested and show consistent result (e.g., tried 3 different micro-habits, all succeeded only with strong routines)
- **Contradictory evidence** ruled out (you thought it was duration, but it was actually routine strength; confirm this with follow-up experiment)

A refined rule should be **downgraded or reversed** if:
- A later experiment contradicts it (tried micro-habit with weak routine, user nailed it anyway)
- Context changed (load went down, or user's capacity changed)
- Sample size too small (only 1 experiment; don't over-interpret)

## Interaction with case formulation

Rules and case formulation evolve together but serve different purposes:

- **Case formulation**: Evolves understanding of *this user's* psychology (what patterns are real, what mechanisms drive them)
- **Rule tightening**: Evolves understanding of *what interventions work* for this user

Example:
```
Case formulation: "Rushing is driven by both habit and avoidance of discomfort"
Rule tightening: "For this user, micro-habits fail unless attached to strong routines"

These are complementary. The first is a hypothesis about cause. The second is
a principle about treatment design. Both update based on evidence.
```

## Privacy and minimization

Do not store:
- Raw experiment details or journal quotes
- Unnecessary user characteristics
- Intermediate rejected hypotheses

Do store:
- What the rule was
- What evidence tightened it
- What the refined rule is
- Confidence level
- Next review date

## Red flags for over-fitting

Avoid over-tightening based on:
- Single experiment (need 2-3 data points minimum)
- Unconfirmed mechanism (you think you know why; confirm)
- Correlation vs. causation (weather improved; did that change results, or was it the experiment?)
- Sample size of one (the entire system is built on N=1, but wait for pattern repetition before over-confident rule refinement)

## Generalization beyond this user

Rules learned from this user should NOT be applied to other users without careful consideration. They are user-specific. If releasing a framework based on this user, mark these as "observed with one user" not "universal best practice."
