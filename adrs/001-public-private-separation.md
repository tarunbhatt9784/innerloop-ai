# ADR 001 - Separate Public Framework from Private Memory

## Status
Accepted.

## Decision
Use a public framework repository and a separate private memory repository. Raw journals remain in Claude Project knowledge only.

## Rationale
The agent is intended for public release, while journals and derived personal learnings are sensitive. Repository separation reduces accidental disclosure and keeps the framework reusable.

## Consequences
Users must configure two trust domains. Automated writes require careful repository targeting and connector permissions.
