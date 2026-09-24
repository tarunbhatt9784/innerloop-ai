# Experiment Outcome Spec

## Purpose

Define how to interpret and learn from the results of behavioural experiments. This is how InnerLoop closes the loop between hypothesis (previous journal) and reality (did the user actually do the thing? what happened?).

## Outcome categories

When reviewing an experiment, classify the result:

### 1. Completed as designed
The user did the action with high fidelity to the agreed design.

Example: "Noticed water on my hand for 20-30 seconds at shower start, 6/7 mornings."

**Learning opportunity**: Did it feel different? Was there any shift in rushing afterward? Refine duration or attachment point if needed.

### 2. Partial completion
The user attempted the action but with reduced fidelity (fewer repetitions, shorter duration, with modifications).

Example: "Attempted 3/7 mornings. When I did it, was fine. But I forgot 4 days."

**Learning opportunity**: The action is feasible but may not be attached to the cue correctly. Test stronger routine attachment (e.g., tied to toothbrush).

### 3. Completed with modification
The user did something similar but changed the design meaningfully.

Example: "Tried it in the shower but it felt too short, so I extended to 2 minutes instead."

**Learning opportunity**: The micro-dose wasn't sufficient for this user. May need longer experiment or different mechanism. Update case formulation: "user's baseline attention span is longer than expected" or "user prefers sustainable effort over micro-habits."

### 4. Not attempted
The user did not try the experiment.

**Acceptable reasons** (not failure):
- Life event (travel, illness, crisis) made the experiment impossible
- Previous experiment revealed the design wouldn't work
- User deprioritized in favor of a more urgent need

**Non-excuse reasons** (still informative):
- "Forgot about it" → attachment to cue was insufficient
- "Didn't feel motivated" → mechanism (why this experiment) wasn't compelling
- "Too much going on" → context changed; recalibrate load assessment

**Learning opportunity**: Why didn't it happen? Design problem, motivation problem, or context problem? Tighten the next experiment accordingly.

### 5. Abandoned mid-way
The user started the experiment and stopped before completing it.

Example: "Tried the shower focus for 2 days, then it felt pointless and I stopped."

**Learning opportunity**: The action itself may be sound, but the hypothesis wasn't compelling. Or the dose was too low to feel effective. Or external resistance was higher than expected. Refine the mechanism and try a different angle.

## Information to gather when reviewing an outcome

When the user reports back on an experiment, elicit:

1. **Adherence**: On how many days/attempts did you do the action? (fraction or list)
2. **Fidelity**: Did you do it exactly as designed, or with changes?
3. **Experience**: What did it feel like? Was there any shift in the target pattern?
4. **Obstacles**: What made it hard or impossible?
5. **Surprise**: Anything unexpected?

Do not treat low adherence as user failure. Treat it as data about design or fit.

## Learning synthesis

After reviewing outcome, synthesize into the case formulation:

### Pattern confirmation or contradiction

If the outcome supports the original pattern hypothesis:
- Raise confidence in that pattern slightly
- Look for next, related pattern to test

If the outcome contradicts the pattern:
- Lower confidence in that pattern
- Test an alternative hypothesis next

### Intervention effectiveness

Did the experiment work (reduce the target pattern or the user felt better)?
- If yes: candidate for refinement and repeat
- If no: was the design sound? Was the pattern right? Adjust for next cycle

If unclear:
- Extend the experiment one more time with a tweak
- Add a measurement signal ("notice whether rushing happens or doesn't")

### Mechanism validation

The original experiment was designed based on a hypothesized mechanism (e.g., "shorter focus will stick better than sustained mindfulness"). Did the outcome validate the mechanism?

- If mechanism validated: use it again for similar patterns
- If mechanism not validated: test alternative (e.g., maybe the issue is cue attachment, not duration)

## Confidence adjustments

Update confidence in case formulation components:

```
Pattern: rushing-past-process
Date: 2026-09-23, confidence: medium (single entry, consistent across activities)
Date: 2026-09-30, after outcome review, confidence: medium-high
  (pattern confirmed in new journal, experiment showed it's modifiable,
   but micro-dose hypothesis incomplete — need stronger routine anchor)
```

## Edge case: No feedback from user

If the user journals again without reporting back on the previous experiment:
- Note that outcome is unknown
- Assume partial completion (the pattern was important enough to journal about, so probably some engagement happened)
- Gently ask for outcome review next run

Do not assume failure if there's no report.

## Privacy and minimization

Do not store:
- Unnecessary details of the user's attempts (e.g., "I was wearing a blue shirt when I tried")
- Emotional self-criticism (e.g., "I'm such a failure because I didn't do it")
- Raw journal quotes about the experiment

Do store:
- Whether completed, partial, modified, abandoned
- Apparent reason (design, motivation, context)
- Learning extracted
- Confidence adjustment justified

## Idempotency

If the same experiment outcome is reported twice (e.g., user journals twice before I review it), do not create duplicate learning entries. Use the experiment ID and outcome date to detect duplicates.
