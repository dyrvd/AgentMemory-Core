# memory-trace

## Goal

Reconstruct the smallest useful history around a memory, milestone, or product state.

## Input

- one or more resolved memory IDs or lineage node IDs
- optional time range
- optional relation types

## Output

- ordered lineage segment
- related milestone IDs
- unresolved or uncertain links
- source pointers for nodes that require verification

## Procedure

1. Start from the resolved node, not from the whole archive.
2. Follow only relevant relations:
   - previous
   - next
   - caused_by
   - supersedes
   - derived_from
   - validated_by
3. Stop when the user's question is answered or when the requested time boundary is reached.
4. Preserve uncertainty. Chronology is not causality.
5. Do not invent missing intermediate events.
6. Return a compact chain before opening exact sources.

## Principle

**Trace only the lineage needed to explain the present question.**
