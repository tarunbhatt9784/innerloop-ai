# Daily Output Data Contract

A daily reflection should be representable as:

```yaml
journal_dates: []
source_quality: low | medium | high
observations: []
selected_experiment:
  title: string
  cue: string
  action: string
  minimum_version: string
  win_condition: string
  fallback: string
  review_signal: string
rationale: string
confidence: low | medium | high
unknowns: []
memory_update:
  type: none | candidate | durable
  proposed_path: string | null
  content_summary: string | null
safety_override: false
```
