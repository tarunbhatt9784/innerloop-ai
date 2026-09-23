# Agent Engineering Glossary

## Agent
An LLM-powered component that can reason about a goal and choose actions or tools within defined boundaries.

## Orchestrator
The component responsible for sequencing specialist work, maintaining state, enforcing policy, and producing the final result.

## Subagent
A bounded specialist role delegated a narrow task, such as evidence extraction or safety review.

## Skill
Reusable procedural knowledge for a recurring task. In this project, the journal-reflection skill defines the daily analysis workflow and references supporting rules.

## Spec
A normative contract describing what a component must do, inputs it accepts, outputs it produces, and invariants it must preserve.

## Schema
A structured definition of an artifact's fields and semantics.

## Tool / Connector
An external capability used to retrieve or mutate data, such as project knowledge search or GitHub access.

## Memory
Persisted derived state used across runs. Memory is not the raw conversation transcript.

## RAG
Retrieval-Augmented Generation: retrieving relevant stored context at run time instead of loading everything into every prompt.

## Provenance
A record of where a conclusion came from.

## Confidence
A calibrated estimate of how strongly evidence supports a derived interpretation. Confidence must never convert a hypothesis into a fact.

## Human-in-the-loop
A checkpoint where user clarification or approval is required because automation would be unsafe or materially uncertain.

## Guardrail
A rule that constrains behaviour, such as no diagnosis or no raw-journal persistence.

## Eval
A repeatable test case used to measure whether the agent follows its intended behaviour.

## Red-team case
An adversarial or failure-oriented eval designed to expose unsafe or brittle behaviour.

## ADR
Architecture Decision Record: a short document explaining a significant design decision and its trade-offs.

## Idempotency
Running the same operation twice should not create duplicate or inconsistent state.

## Observability
The ability to understand what the system did and why through explicit state, provenance, scores, and outputs.

## Context engineering
Designing what information the model receives, in what order, at what granularity, and under what trust assumptions.
