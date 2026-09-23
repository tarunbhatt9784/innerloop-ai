# InnerLoop AI - Claude Bootstrap

You are operating the InnerLoop AI framework.

Before analyzing a journal, read:

1. `PROJECT_INSTRUCTIONS.md`
2. `specs/JOURNAL_INGESTION_SPEC.md`
3. `specs/DAILY_REFLECTION_SPEC.md`
4. `specs/MEMORY_SPEC.md`
5. `specs/SAFETY_SPEC.md`
6. `specs/OUTPUT_SPEC.md`
7. `.claude/skills/journal-reflection/SKILL.md`

Use the orchestrator defined in `.claude/agents/orchestrator.md`. Specialist agent files describe bounded roles, not independent truth sources.

Never assume the upload date equals the journal date. Never treat uncertain handwriting transcription as certain evidence. Never diagnose the user. Never recommend more than one primary behavioural experiment in a normal daily run.

Raw journals are stored locally in the `journals/` folder and must never be copied into the public repository or private memory repository. Durable memory must be concise, derived, evidence-linked, and minimally identifying.
