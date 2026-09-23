# Folder Structure

```text
Psychologist/
├── journals/              # Local private journal PDFs (not in git)
├── innerloop-ai/          # Public framework
└── innerloop-memory/      # Private memory (separate repository)

innerloop-ai/
├── README.md
├── CLAUDE.md
├── PROJECT_INSTRUCTIONS.md
├── ARCHITECTURE.md
├── SECURITY_PRIVACY.md
├── LICENSE.md
├── .claude/
│   ├── agents/
│   │   ├── orchestrator.md
│   │   ├── journal-reader.md
│   │   ├── pattern-analyst.md
│   │   ├── intervention-designer.md
│   │   ├── safety-reviewer.md
│   │   └── memory-curator.md
│   └── skills/
│       └── journal-reflection/
│           ├── SKILL.md
│           ├── agents/openai.yaml
│           └── references/
│               ├── EVIDENCE_RULES.md
│               └── ACTION_DESIGN.md
├── specs/
│   ├── JOURNAL_INGESTION_SPEC.md
│   ├── DAILY_REFLECTION_SPEC.md
│   ├── MEMORY_SPEC.md
│   ├── SAFETY_SPEC.md
│   ├── OUTPUT_SPEC.md
│   ├── QUESTION_POLICY.md
│   └── GITHUB_MEMORY_WRITE_SPEC.md
├── schemas/
│   ├── EVIDENCE_ITEM_SCHEMA.md
│   ├── MEMORY_ENTRY_SCHEMA.md
│   └── DAILY_OUTPUT_SCHEMA.md
├── prompts/DAILY_RUN.md
├── docs/
│   ├── SETUP_CLAUDE_PROJECT.md
│   ├── OPERATING_MODEL.md
│   ├── GLOSSARY.md
│   └── FOLDER_STRUCTURE.md
├── evals/EVALS.md
├── adrs/
│   ├── 001-public-private-separation.md
│   ├── 002-deterministic-orchestrator.md
│   └── 003-one-change-policy.md
├── examples/SYNTHETIC_DAILY_OUTPUT.md
└── .github/PUBLICATION_CHECKLIST.md

innerloop-memory/  # separate PRIVATE repository
├── README.md
├── PROFILE.md
├── .gitignore
├── patterns/INDEX.md
├── experiments/INDEX.md
├── weekly/README.md
├── decisions/README.md
└── processed-journals/
    ├── INDEX.md
    └── [dated-records]
```

## Note on journals/ folder

The `journals/` folder at the project root contains raw scanned journal PDFs. This folder should:

- Be in `.gitignore` (not tracked in any repository)
- Remain private and local
- Not be synced to GitHub
- Only be read by the analysis workflow
