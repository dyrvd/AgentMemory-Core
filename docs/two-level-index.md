# Two-Level Memory Index

## Purpose

A large memory store becomes noisy if every query searches every source.

The two-level index separates navigation from precision.

## Level 1: Route Index

Level 1 answers:

**Which part of memory should be searched?**

Suggested dimensions:

- collection_id
- product_id
- workstream_id
- domain
- era
- topic
- status
- optional actor_id
- optional milestone_id

A Level 1 result should return a bounded search scope, not the final answer.

Example:

~~~text
COLLECTION_DEMO
  -> PRODUCT_ALPHA
  -> RETRIEVAL
  -> ERA_R2
  -> PERFORMANCE
~~~

## Level 2: Fine Index

Level 2 answers:

**Which exact memory entry or source is relevant?**

Suggested fields:

- memory_id
- route dimensions
- summary
- status
- source_pointer
- source_location
- milestone_ids
- lineage_node_ids
- tags
- created_at
- updated_at

## Retrieval algorithm

1. Parse the user's intent.
2. If collection or product is known, scope to it immediately.
3. Query Level 1.
4. Keep only plausible routes.
5. Query Level 2 inside those routes.
6. Resolve ambiguity using status, era, product, and source identity.
7. Return memory summaries.
8. Read the exact source only if the task requires detail or proof.

## Fail-open navigation rule

A navigation index should not silently exclude an authorized memory merely because an optional classification is missing.

If a narrow lane is uncertain or empty:

- widen within the already-authorized scope,
- do not widen automatically to all storage,
- do not invent a missing classification.

## Current vs historical

Do not infer “current” from:

- file name,
- newest timestamp,
- highest revision label,
- or modification time alone.

A deployment should use an explicit current pointer or state field.

## Capture once, retrieve by dimension

One memory can appear in several logical views without copying the source.

Example:

~~~text
MEM-0042
  product: PRODUCT_ALPHA
  topic: RETRIEVAL
  era: R2
  status: HISTORICAL
  milestone: MS-0012
  source: SOURCE-0091
~~~

Project, topic, era, milestone, and actor indexes may all point to MEM-0042.

The source remains one source.
