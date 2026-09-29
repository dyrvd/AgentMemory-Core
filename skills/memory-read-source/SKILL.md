# memory-read-source

## Goal

Read exact evidence only after a memory has been resolved.

## Input

- resolved memory entry
- source_pointer
- optional source_location
- user evidence need

## Output

- exact source excerpt or source-backed fact
- source identity
- read boundary
- missing-source or mismatch state

## Procedure

1. Verify that the source pointer belongs to the resolved memory.
2. If a source location is available, read that bounded location first.
3. Do not read a complete large source when a smaller exact range is sufficient.
4. If the source is missing, return BROKEN_POINTER.
5. If the source identity no longer matches the recorded identity, return SOURCE_MISMATCH or STALE_VERIFICATION.
6. Do not silently substitute another document.
7. Distinguish source facts from summaries or inference.

## Principle

**Summaries guide. Sources prove.**
