# Self-Learning Components Added

## Summary

You now have a complete **progressive case formulation system** that enables InnerLoop AI to learn and improve its recommendations over time, mirroring how clinical psychologists work with clients across multiple sessions.

## Files Created

### Specifications (innerloop-ai/specs/)
1. **CASE_FORMULATION_SPEC.md** — How to build and maintain a coherent case model of your patterns
2. **EXPERIMENT_OUTCOME_SPEC.md** — How to interpret what happens after each experiment and what it means
3. **RULE_TIGHTENING_SPEC.md** — How the system's own rules evolve based on evidence from your journal entries

### Architecture Decisions (innerloop-ai/adrs/)
4. **004-progressive-case-formulation.md** — The decision to add this learning layer (with rationale, consequences)

### Agents (innerloop-ai/.claude/agents/)
5. **case-formulator.md** — New agent responsible for maintaining and updating the case model

### Memory Structure (innerloop-memory/case-formulation/)
6. **current-formulation.md** — **Your evolving case model** (already populated with your first journal)
7. **experiments-outcome-log.md** — Track what happens with each experiment
8. **rule-tightening-log.md** — Log of how the system's rules change based on evidence

### Documentation (innerloop-ai/docs/)
9. **SELF_LEARNING_SYSTEM.md** — Complete guide to how this works

### Updated Files
10. **ARCHITECTURE.md** — Now includes the Case Formulator in the runtime flow

## What Changed in the System

### Before
```
Journal → Extract patterns → Design one experiment → Output
(Each journal is isolated; no learning from outcomes)
```

### Now
```
Journal → Review prior experiment outcome → Update case model → Refine rules → 
Extract patterns (informed by prior learnings) → Design better experiment → Output

↑                                                                           ↓
└─── Case formulation evolves ← Experiment outcomes ← Feedback cycle ─────┘
```

## What You'll See Next Journal

### Current state (after Journal 1)
- Initial case formulation with 3 candidate patterns
- exp-001 planned (shower awareness)
- Baseline rules documented

### After Journal 2 (when you submit your next entry)
- System asks: "What happened with the shower experiment?"
- Updates case formulation based on your outcome
- Shows confidence adjustments (medium → high, or medium → low)
- Tightens the rules for next experiment design
- Designs exp-002 using lessons from exp-001
- You see: "Here's what we learned, here's how we're adjusting"

### After Journal 3+
- Pattern predictions become more accurate
- Experiments become increasingly tailored to what works for you
- Case model converges (stabilizes) as evidence accumulates
- System is increasingly personalized

## What's in Your Case Formulation Right Now

From your first journal (2026-09-23):

### Patterns identified:
1. **Rushing-past-process** (medium confidence)
   - Evidence: Observed across shower, kitchen, walking, journaling itself
   - Real-time self-awareness: You noticed it happening while writing

2. **Novelty → Boredom → Forced Consistency → Burnout** (medium confidence)
   - Evidence: Self-identified as "the standard case with me"
   - Not yet tested

3. **Distraction when overwhelmed** (low-to-medium confidence)
   - Evidence: YouTube reels, phone checking during tasks
   - Unclear whether primary avoidance or secondary symptom

### Contextual factors logged:
- Financial pressure (high): 3 mortgages, recurring repairs
- Caregiving load (moderate): partner recovery, aging parents
- Health focus (active): pre-diabetic, symptom monitoring
- Therapy history: 10+ years CBT prior; not currently engaged

### First experiment designed:
- **exp-001**: Single-hand shower awareness (20-30s, one-breath fallback)
- **Why**: You already tried this spontaneously; shrinking dose removes friction
- **Tests**: Whether micro-attention can interrupt rushing pattern
- **Status**: Planned, outcome awaiting

## How to Use This

### For your next journal (ideally in 7-10 days):
1. Write naturally about what happened this week
2. **Brief note on exp-001**: Did you try the shower practice? What happened?
3. Journal normally; the system will extract what's relevant

### What the system will do:
1. Review your experiment outcome
2. Update confidence in patterns (up if confirmed, down if not shown)
3. Note any surprises or contradictions
4. Tighten action-design rules for the next experiment
5. Give you an updated case formulation snapshot
6. Design exp-002 better informed

## Key Points

- **Not a diagnosis system**: Patterns and mechanisms, not disorder labels
- **Personalized over time**: Generic at first (week 1), increasingly tailored (week 4+)
- **Honest about uncertainty**: Confidence goes up with evidence, down if contradicted
- **Privacy-first**: Only derived learnings stored, no raw journal text
- **Safe defaults**: Won't over-fit to one data point; waits for patterns to repeat

## Files to Read First

If you want to understand this system:
1. **SELF_LEARNING_SYSTEM.md** (how it works, overview) ← Start here
2. **CASE_FORMULATION_SPEC.md** (detailed rules for case model)
3. **EXPERIMENT_OUTCOME_SPEC.md** (how outcomes are interpreted)
4. **RULE_TIGHTENING_SPEC.md** (how rules evolve)

Or just write your next journal and let the system show you what it learned.

## Visual Summary

```
Session 1 (Now - completed):
├── Case formulation created ✓
├── 3 patterns identified (with confidence levels)
├── Contextual factors documented
└── exp-001 designed ✓

Session 2 (Next journal):
├── Outcome review (did exp-001 happen?)
├── Case formulation updated (confidence adjusted)
├── Rules tightened (what did we learn?)
└── exp-002 designed (better informed)

Session 3+ (Ongoing):
├── Patterns confirmed or contradicted
├── Confidence converges (higher or lower)
├── Experiments increasingly personalized
└── Case model stabilizes and improves
```

---

**Your system is now ready to learn from experience, just like a clinical psychologist does over months of work with a client.**
