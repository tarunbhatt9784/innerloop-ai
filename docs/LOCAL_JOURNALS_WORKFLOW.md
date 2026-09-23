# Local Journals Workflow

## Overview

InnerLoop AI now reads journal PDFs directly from the local `journals/` folder instead of requiring upload to Claude Project knowledge.

## Folder Structure

```
Psychologist/
├── journals/              # Store your handwritten journal scans here
│   ├── 23 September 2026.pdf
│   ├── 24 September 2026.pdf
│   └── ...
├── innerloop-ai/          # Public framework
└── innerloop-memory/      # Private memory repository
```

## Workflow

### 1. Add Your Journal

Save scanned handwritten journal PDFs to the `journals/` folder.

**Naming convention** (optional but recommended):
- Use the journal's handwritten date: `23 September 2026.pdf`
- Or use any clear naming scheme that you can identify later
- **Do not rely on filename as the authoritative date** — handwritten dates in the journal take precedence

### 2. Run Journal Analysis

When ready to analyze your latest journal:

1. Open Claude Code or your Claude Project with access to the `innerloop-ai` framework
2. Paste the content of `innerloop-ai/prompts/DAILY_RUN.md` as your prompt
3. Claude will:
   - Read the journal PDF from the local `journals/` folder
   - Follow the analysis workflow defined in `PROJECT_INSTRUCTIONS.md`
   - Return one focused behavioural experiment
   - Propose memory updates to `innerloop-memory/` if supported by evidence

### 3. Using With Claude Project

Even with local journals:

- Add `innerloop-ai` files to your Claude Project knowledge (for framework access)
- Add `innerloop-memory` files to your Claude Project knowledge (for prior learnings)
- Claude will read journal PDFs from the local `journals/` folder
- Processed journal records are stored in `innerloop-memory/processed-journals/`

## Privacy

- Raw journal PDFs remain local and private — not copied to any repository
- Only processed, derived records (without raw transcriptions) go to `innerloop-memory/`
- Framework files in `innerloop-ai/` are public
- Memory files in `innerloop-memory/` are private

## Key Files to Know

- `innerloop-ai/PROJECT_INSTRUCTIONS.md` — The system's operating rules
- `innerloop-ai/specs/JOURNAL_INGESTION_SPEC.md` — How journals are processed
- `innerloop-ai/prompts/DAILY_RUN.md` — The daily analysis prompt
- `innerloop-memory/processed-journals/INDEX.md` — Record of all processed journals

## Important Notes

- The system **does not** rely on PDF filename or file modification date as the journal date
- The **handwritten date** in the journal content is the source of truth
- If a journal spans multiple handwritten dates, it is split into separate dated entries
- Journal transcriptions are never persisted — only derived evidence and learnings
