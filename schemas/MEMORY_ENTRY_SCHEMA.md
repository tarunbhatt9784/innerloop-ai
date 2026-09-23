# Memory Entry Schema

```yaml
id: mem-<type>-<slug>
type: candidate-pattern | durable-pattern | preference | constraint | experiment-learning
status: active | contradicted | archived
confidence: low | medium | high
first_observed: YYYY-MM-DD
last_supported: YYYY-MM-DD
supporting_dates:
  - YYYY-MM-DD
contrary_dates: []
summary: string
why_useful: string
next_review: YYYY-MM-DD | null
```

A memory entry must remain a derived abstraction, not a raw journal excerpt.
