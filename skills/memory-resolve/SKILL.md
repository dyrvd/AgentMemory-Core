# memory-resolve

## Goal

Select the correct Level 2 memory entry from a bounded candidate set.

## Input

- candidate route
- Level 2 fine-index results
- current / historical state
- user request

## Output

- resolved memory_id list
- unresolved ambiguity if any
- exact source pointers, not source content

## Procedure

1. Filter candidates by collection and product identity.
2. Prefer explicit current state when the user asks about the present.
3. Keep historical entries when the user asks why, when, before, or previously.
4. Compare era, workstream, status, milestone links, and source identity.
5. Do not treat newest timestamp as equivalent to current.
6. Do not merge same-title memories from different products.
7. Return UNKNOWN or AMBIGUOUS when identity cannot be resolved.
8. Pass resolved memory IDs to memory-trace or memory-read-source only when required.

## Principle

**Resolve identity before reading content.**
