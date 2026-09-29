# Architecture

## Goal

AgentMemory-Core is an external memory architecture for long-running AI work.

The system is designed around a simple separation:

**Storage may grow continuously. Working context should stay bounded.**

A project can keep years of source material while a new agent loads only a small set of relevant indexes, milestones, and source excerpts.

## Four components

### A. Two-Level Memory Index

Level 1 is a routing layer.

It narrows the search by dimensions such as:

- collection,
- product or project,
- workstream,
- domain,
- era or phase,
- topic,
- actor or seat when relevant,
- status.

Level 2 is a precision layer.

It points to a specific memory entry and its source.

### B. Milestone System

Milestones summarize important changes in project history.

They are not replacements for sources. They are high-value navigation points.

### C. Retrieval Skills

Retrieval is procedural.

The agent should not simply search everything and trust the first semantic match.

It should route, narrow, resolve, trace, and only then read source evidence.

### D. Memory Lineage

Lineage links events into a project narrative.

It records relationships such as:

- previous,
- next,
- caused_by,
- supersedes,
- derived_from,
- validated_by.

## Storage layers

A practical deployment can use three temperature levels.

### Hot
Loaded at cold start.

Keep this small:

- memory entry point,
- current product or collection pointer,
- retrieval rules,
- current milestone pointer.

### Warm
Loaded on demand:

- Level 1 index,
- Level 2 index,
- relevant milestones,
- relevant lineage segment,
- memory summaries.

### Cold
Read only when needed:

- raw conversations,
- complete research,
- historical versions,
- large attachments,
- exact evidence.

The raw archive can be very large without forcing a large model context.

## Core invariants

1. Route before broad search when scope is known.
2. A source may be referenced by many indexes but should not be duplicated merely for classification.
3. A summary never replaces the exact source.
4. Historical records remain historical after a successor exists.
5. A milestone is a compression layer, not another copy of the source.
6. Lineage edges must not invent causality when the relation is unknown.
7. Unknown is a valid result.
8. Cross-product search is explicit, not the default.
9. Retrieval should load the smallest sufficient working set.
10. Long-term storage growth is acceptable if indexes and pointers remain healthy.

## Cold-start procedure

A new agent should normally:

1. identify the collection or product,
2. read the current memory entry point,
3. read the latest relevant milestones,
4. read unresolved items if present,
5. use Level 1 to choose the correct branch,
6. use Level 2 to select candidate memories,
7. trace lineage only when historical explanation is needed,
8. read exact sources only for details or evidence.

## What this architecture does not claim

It does not claim:

- internal model memory,
- perfect recall,
- automatic truth,
- automatic access to private sources,
- automatic importance detection,
- universal token savings,
- or autonomous background synchronization.

It is a structured recovery method, not a guarantee that every stored fact is correct or retrievable forever.
