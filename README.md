# InnerLoop AI

InnerLoop AI is a privacy-first, journal-driven personal reflection agent designed to turn unstructured handwritten journal entries into one small, evidence-informed behavioural experiment at a time.

It is built as an educational, enterprise-style agent architecture: explicit orchestration, specialist agents, reusable skills, schemas, safety boundaries, durable memory, provenance, evals, and architectural decision records.

## What InnerLoop AI does

1. Reads one or more scanned handwritten journal PDFs from Claude Project knowledge.
2. Separates transcription uncertainty from interpretation.
3. Detects the actual journal dates represented in the file, including gaps or multiple days.
4. Extracts observations, recurring patterns, needs, triggers, coping strategies, strengths, and open questions.
5. Retrieves only relevant prior learnings from the private memory repository.
6. Selects exactly one next behavioural experiment with the highest probability of completion and useful learning.
7. Explains why that experiment was selected, what evidence supports it, and how to make success easy.
8. Updates durable memory only when a learning is sufficiently supported and useful.

## Important boundary

InnerLoop AI is not a licensed psychologist, does not diagnose mental disorders, and is not a substitute for professional care. Its role is reflective analysis, behaviour-change experimentation, pattern tracking, and preparation for conversations with qualified professionals. Safety-critical concerns override the normal "one experiment" workflow.

## Privacy model

Raw journals never belong in this repository.

Use two repositories:

- `innerloop-ai` — public framework: prompts, specs, agents, skills, schemas, docs, evals.
- `innerloop-memory` — private personal memory: carefully derived learnings and experiment history.

Raw scanned journals stay inside the user's private Claude Project knowledge. The public repository must never contain raw journal files, direct personal journal transcripts, or secrets.

## Repository map

See `ARCHITECTURE.md` for the runtime design and `docs/SETUP_CLAUDE_PROJECT.md` for setup.
