# Local Journals Workflow

## Overview

InnerLoop AI now reads journal PDFs — and optional mobile-note images — directly from the local `journals/` folder instead of requiring upload to Claude Project knowledge.

## Folder Structure

```
Psychologist/
├── journals/              # Store your handwritten journal scans and mobile-note photos here
│   ├── 23 September 2026.pdf
│   ├── 24 September 2026.pdf
│   ├── 26 September 2026.pdf
│   ├── 26 September 2026 (1).jpg   # optional mobile note, same day
│   ├── 26 September 2026 (2).jpg   # optional second mobile note, same day
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
- **Do not rely on filename as the authoritative date** — handwritten dates in the journal content take precedence

### 1b. Add Mobile Notes (Optional)

If you jot notes on your phone while out without your journal — a quick photo of a scrap of paper, a note app screenshot, etc. — save it to `journals/` too:

- Name it with the same date as your diary entry, plus a counter if there's more than one that day: `26 September 2026 (1).jpg`, `26 September 2026 (2).jpg`. The counter just avoids filename clashes — it carries no time meaning.
- **Write a time in the note itself whenever you can** (e.g., "10am", "1012am") — this lets the system slot it precisely into that day's sequence alongside your diary entries.
- If you don't write a time, that's fine too — the system will place it relative to the nearest timed notes around it (see below), and only puts it at the end of the day, clearly marked as unclear timing, if there's genuinely nothing to anchor it to.

**How ordering works**: all your timed notes for a day — whether from the PDF or from photos — get merged into one single chronological sequence. An untimed note slots into the gap between whichever timed notes come immediately before and after it (in the order you wrote it), not wherever the file happens to sit alphabetically or by upload order. Full detail in `specs/JOURNAL_INGESTION_SPEC.md`, Section 29.

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

- The system **does not** rely on PDF/image filename or file modification date as the journal date
- The **handwritten/written date** in the journal content is the source of truth
- If a journal spans multiple handwritten dates, it is split into separate dated entries
- Journal transcriptions are never persisted — only derived evidence and learnings
- Mobile-note images are treated as private raw source material, exactly like the PDF — never copied into any repository
- If you add a mobile-note image for a date that's already been processed (e.g., you journal in the PDF at night, then remember a photo from earlier that day), the system updates the existing record rather than creating a duplicate
