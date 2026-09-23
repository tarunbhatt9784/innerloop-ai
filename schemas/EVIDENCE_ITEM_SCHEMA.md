# Evidence Item Schema

```yaml
id: ev-YYYYMMDD-NNN
journal_date: YYYY-MM-DD | unknown
source_file: string
source_page: integer | unknown
category: event | thought | emotion | body | behaviour | urge | value | coping | outcome | tension | strength | unknown
summary: string
transcription_confidence: low | medium | high
interpretation: string | null
interpretation_confidence: low | medium | high | null
```

`summary` should paraphrase where possible. Use verbatim text only when necessary to preserve meaning.
