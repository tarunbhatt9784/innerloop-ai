# ADR 002 - Prefer a Deterministic Orchestrator over a Multi-Agent Swarm

## Status
Accepted.

## Decision
Use one orchestrator with bounded specialist roles.

## Rationale
Journal analysis is sequential and safety-sensitive. A swarm adds coordination cost, inconsistent state, and unclear provenance without corresponding benefit.

## Consequences
The system is easier to test and audit, while still teaching delegation and subagent concepts.
