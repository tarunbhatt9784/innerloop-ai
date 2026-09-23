# Architecture

## Architectural style

InnerLoop AI uses a deterministic orchestrator with bounded specialist roles rather than a free-form multi-agent swarm.

The orchestrator owns sequencing, state transitions, tool usage, and final output. Specialist agents contribute analysis within narrow contracts. The final decision is made only after evidence extraction and safety review.

## Runtime flow

```text
Claude Project Knowledge (private journal PDFs)
              |
              v
       Journal Reader Agent
              |
        Evidence Packet
              v
      Pattern Analyst Agent <---- relevant private memory only
              |
        Working Hypotheses
              v
  Intervention Designer Agent
              |
      Candidate Experiments
              v
       Safety Reviewer Agent
              |
      approved / modified / stop
              v
          Orchestrator
              |
      Daily Reflection Output
              |
              +----> Memory Curator ----> private innerloop-memory repo
```

## Why this is not a swarm

The task is highly sequential. Later stages depend on validated outputs from earlier stages. Allowing autonomous agents to independently rewrite user models would create unnecessary inconsistency and make provenance harder to audit.

## Enterprise concepts demonstrated

- Orchestrator pattern
- Specialist subagents
- Skills and reusable procedural knowledge
- Explicit specifications and contracts
- Schemas
- Retrieval-augmented memory
- Provenance and confidence
- Human-in-the-loop clarification
- Privacy boundaries
- Idempotency
- Observability
- Evals and red-team cases
- Architecture Decision Records (ADRs)
- Progressive disclosure of context
- Least-privilege retrieval
- Separation of source data from derived state
- Failure-mode handling

## State model

A daily run moves through these states:

`DISCOVER -> INGEST -> EVIDENCE_READY -> MEMORY_RETRIEVED -> HYPOTHESES_READY -> CANDIDATES_READY -> SAFETY_REVIEWED -> OUTPUT_READY -> MEMORY_PROPOSED`

If source quality is too poor, transition to `NEEDS_CLARIFICATION`.

If safety escalation is required, transition to `SAFETY_OVERRIDE` and bypass normal experiment selection.

## Idempotency

A repeated run over the same journal date and same source material should not create duplicate memory entries. Durable memory entries use stable IDs based on date + learning type + short slug.
