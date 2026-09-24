# Self-Learning System for InnerLoop AI

## Overview

InnerLoop AI now includes a **progressive case formulation** layer that mirrors how clinical psychologists work with clients over multiple sessions: hypothesis, test, observe outcome, refine understanding.

Instead of treating each journal in isolation, the system now learns and tightens its rules based on what actually works for you.

## How it mirrors clinical psychology

| Clinical Practice | InnerLoop AI |
|---|---|
| Session 1: Take history, form initial hypotheses | Journal 1: Extract patterns, propose first experiment |
| Sessions 2-N: Test hypotheses, adjust treatment plan | Journals 2+: Review experiment outcome, update case model, refine next experiment |
| Longitudinal tracking: Build a coherent case model | Case formulation file: Evolves with each journal, tracks confidence, records what changed |
| Treatment effectiveness: Did the therapy work? | Rule tightening: Did the experiment work? What should we adjust? |

## Key concepts

### 1. Case Formulation

A coherent model of **how your patterns fit together** and **what might help**.

- Not a diagnosis (no disorder labels)
- A working hypothesis about mechanisms, contexts, and what's been tested
- Evolves with each journal entry as evidence accumulates
- Stored in: `innerloop-memory/case-formulation/current-formulation.md`

Example formulation components:
```
Pattern: rushing-past-process
Possible mechanism: habit + avoidance of discomfort
Evidence quality: high (self-observed, real-time, across multiple activities)
Tested with: exp-001 (micro-attention), outcome pending

Pattern: novelty → boredom → forced consistency → burnout
Evidence quality: medium (self-identified, not yet tested)
Next test: interrupt boredom phase with visible progress signal
```

### 2. Experiment Outcomes

After you try an experiment, the system reviews:
- **Did you do it?** (completed, partial, modified, abandoned)
- **What happened?** (felt different? pattern changed? or no shift?)
- **What does this tell us?** (validates or contradicts the hypothesis)

Recorded in: `innerloop-memory/case-formulation/experiments-outcome-log.md`

Example:
```
exp-001: Single-hand shower awareness
Hypothesis: shorter focus will stick better than sustained attention
Completed: 4/7 mornings
Result: worked when attached to shower (strong routine), didn't work as standalone practice
Learning: routine strength matters; micro-habits need strong anchor points
Confidence adjustment: raised confidence that routine-attachment is key for this user
```

### 3. Rule Tightening

The system's own action-design rules evolve based on what actually works for you.

- **Initial rule** (from first journal): "For high-burnout users, use very short experiments"
- **After exp-001 outcome**: "Short experiments work IF attached to a daily automatic routine. Mental-cue attachment fails."
- **Refined rule** (going forward): design micro-habits around shower/toothbrushing, not abstract cues

Recorded in: `innerloop-memory/case-formulation/rule-tightening-log.md`

## How it changes your experience

### First journal (now completed)
- System builds initial case formulation
- Proposes first experiment
- You see: initial hypotheses, first experiment design, and what we're testing

### Second journal and beyond
- **Before** reading your new journal, system reviews: "Did exp-001 happen? What was the outcome?"
- System **updates case formulation**: confidence goes up/down based on evidence
- System **refines rules**: "Here's what we learned about what works for this user"
- System **designs exp-002 better**: informed by what exp-001 taught us
- You see: outcome review, case updates, more tailored next experiment

## Folder structure for self-learning

```
innerloop-memory/
├── case-formulation/
│   ├── current-formulation.md       # Current model of your patterns/mechanisms
│   ├── experiments-outcome-log.md   # What happened with each experiment
│   └── rule-tightening-log.md       # How the system's rules evolved
├── patterns/
│   └── [candidate and durable patterns, indexed]
├── experiments/
│   └── [experiment history and outcomes]
└── processed-journals/
    └── [one file per journal date]
```

## How confidence evolves

```
Pattern: Rushing-past-process

Date 2026-09-23, confidence: MEDIUM
  (First observation. Consistent across 4 activities in single entry. 
   Real-time self-awareness. Awaiting multi-date confirmation.)

Date 2026-09-30, confidence: MEDIUM-HIGH
  (Confirmed again in new journal. exp-001 showed it's modifiable.
   Routine-attachment hypothesis partially validated.)

Date 2026-10-07, confidence: HIGH
  (Now seen in 3+ journal dates. Multiple experiments support 
   the routine-attachment mechanism. Likely a real, modifiable pattern.)
```

Low confidence → Medium confidence → High confidence (as evidence accumulates)

**Bonus**: If new evidence contradicts the pattern, confidence goes back down. The system is honest about uncertainty.

## What does NOT change

These remain constant regardless of your data:
- **Safety policy**: Risk assessment and emergency procedures
- **Privacy policy**: Raw journals never stored, no unnecessary identifiers
- **One-change rule**: Exactly one experiment per journal, not five
- **No diagnosis**: The system does NOT assign disorder labels, even if patterns fit textbook conditions
- **Clinical boundary**: Serious conditions get referred to professionals, not experimented on

## For the next journal entry

When you write your next journal (ideally within 7-10 days), the system will:

1. Ask about **exp-001 outcome** (the shower awareness practice)
   - How many days did you attempt it?
   - What happened when you did?
   - What got in the way when you didn't?

2. **Update the case formulation**:
   - Raise/lower confidence in patterns based on outcome
   - Flag any surprises or contradictions
   - Refine mechanisms based on what the experiment revealed

3. **Tighten the rules**:
   - If routine-attachment mattered, next experiment will use it
   - If duration was the issue, next experiment adjusts dose
   - If the pattern didn't show up, reconsider the hypothesis

4. **Design exp-002** better than exp-001, informed by what happened

## Red flags to avoid (built-in safeguards)

The system won't:
- Over-fit to one experiment ("you did it once, so micro-habits are perfect for you")
- Confuse correlation with causation ("the weather was nice, so that's why it worked")
- Ignore contradictory evidence ("you said it didn't work, but I'm going to recommend it anyway")
- Over-diagnose ("you're rushing + anxious, so you have ADHD")

Instead, it waits for patterns to repeat, stays honest about sample size ("this is based on 1 experiment; need more data"), and follows evidence.

## Privacy with learning

The self-learning system stores only:
- Derived patterns, not raw journal text
- Mechanism hypotheses, not case details
- Experiment outcomes, not unnecessary personal context
- Confidence levels and evidence source, not stories

Raw journals stay private. All learning is abstracted, minimized, and derived.

## Questions for your next journal

To make the learning system work well, when you journal next, consider noting:

1. **On exp-001 (shower focus)**:
   - Did you attempt it? How many times?
   - If yes: what did it feel like? Any shift in rushing or anxiousness?
   - If no: what got in the way? Forgot? Didn't seem relevant? Something else?

2. **Pattern check**:
   - Did you notice yourself rushing this week? Same contexts or different?
   - Did the novelty-boredom-burnout cycle show up? What triggered it?

3. **Surprises**:
   - Anything that contradicted what you expected?
   - Any wins or things that went better than expected?

(These are optional prompts, not requirements. Just journal naturally; the system will extract what's relevant.)

## How this improves the exercise over time

- **Week 1**: System makes educated guesses based on limited data
- **Week 3-4**: Patterns confirmed/contradicted, rules tightened
- **Month 2**: Experiments increasingly tailored to what works for you
- **Month 3+**: Case formulation converges on a robust model; experiments become more effective

The longer you engage, the more personalized and effective the recommendations become — because the system is learning *about you specifically*, not applying generic advice.
