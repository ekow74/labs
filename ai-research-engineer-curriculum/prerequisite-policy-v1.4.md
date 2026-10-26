# Typed Prerequisite Policy — v1.4

The curriculum no longer treats every prerequisite relationship as an equal hard gate.

## Edge types

| Type | Meaning | Blocks course start? |
|---|---|---|
| HARD | Knowledge or skill must be demonstrated first | Yes |
| SOFT | Recommended beforehand or concurrently | No |
| JIT | Learn the relevant concept immediately before the lab/lesson needing it | No |
| ENRICHMENT | Adds theoretical/research depth but is not needed for productive applied work | No |

## Applied-path examples

- `OPS-301 <- FND-002`: HARD
- `OPS-301 <- CS-230`: ENRICHMENT
- `DL-601 <- FND-004`: HARD
- `DL-601 <- MATH-204`: SOFT
- `DL-601 <- MATH-201`: ENRICHMENT
- `DL-610 <- DL-601`: HARD
- `DL-610 <- STAT-510`: ENRICHMENT
- `DL-610 <- ML-530`: ENRICHMENT
- `IR-901 <- DL-630`: JIT
- `RAG-920 <- IR-910`: HARD
- `RAG-920 <- DL-660`: SOFT
- `AG-950 <- RAG-920`: HARD
- `AG-950 <- EVAL-940`: HARD
- `AG-950 <- DL-660`: SOFT
- `AG-960 <- AG-950`: HARD
- `AISEC-1001 <- DL-660`: ENRICHMENT
- `AISEC-1020 <- RAG-920`: HARD
- `AISEC-1030 <- AG-960`: HARD
- `AISEC-1030 <- AISEC-1020`: HARD

## Governance

1. Only HARD edges block entry.
2. A learner may satisfy a HARD edge through the formal course or a documented diagnostic/mastery challenge.
3. SOFT/JIT/ENRICHMENT knowledge remains testable inside later course mastery gates when it becomes relevant.
4. Changes to edge type must state why the dependency is truly blocking or non-blocking.
5. The executable workbook is the source of truth for the complete typed-edge matrix.

The purpose is to reduce time-to-first-applied-result without lowering mastery standards. Deep mathematics and systems theory remain in the library and become mandatory where research depth actually requires them.
