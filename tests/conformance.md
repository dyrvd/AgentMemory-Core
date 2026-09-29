# Conformance Tests

These tests define behavioral expectations for an implementation of the public core.

They are specification tests, not claims about any private system.

## T01 — Route before global search

Given:

- PRODUCT_ALPHA and PRODUCT_BETA both contain a memory tagged SEARCH,
- the request explicitly names PRODUCT_ALPHA.

Expected:

- search PRODUCT_ALPHA first,
- do not begin with all-storage search.

## T02 — Same-name isolation

Given two memories with the same title in different products.

Expected:

- do not merge them,
- preserve product identity,
- return ambiguity if product identity is missing.

## T03 — Current vs historical

Given:

- MEM-OLD = HISTORICAL,
- MEM-NEW = CURRENT.

Expected:

- a present-state query returns MEM-NEW,
- a historical query may return both,
- timestamp alone does not decide current state.

## T04 — Broken pointer

Given a resolved memory whose source pointer cannot be opened.

Expected:

- return BROKEN_POINTER,
- do not silently substitute a similar source.

## T05 — Summary is not evidence

Given a memory summary and an exact source.

Expected:

- use the summary for navigation,
- use the source when exact wording or proof is requested.

## T06 — Milestone compression

Given hundreds of source events but five major milestones.

Expected:

- cold start reads the milestones first,
- source events remain available but are not all loaded.

## T07 — Lineage without invented causality

Given A occurred before B but no causal evidence exists.

Expected:

- previous/next may be recorded,
- caused_by must not be invented.

## T08 — Explicit cross-product search

Given a request asking whether other products experienced a similar failure.

Expected:

- cross-product retrieval is allowed for this request,
- each result preserves its product identity.

## T09 — Unknown classification

Given a memory with unknown actor or era.

Expected:

- UNKNOWN remains valid,
- the implementation does not invent a value merely to complete an index.

## T10 — Bounded working set

Given a large archive.

Expected:

- retrieval loads only the route, fine-index candidates, relevant milestones/lineage, and exact sources needed for the question.

## Suggested health metrics

A deployment may track:

- Unindexed Ratio
- Broken Pointer Rate
- Stale Verification Rate
- Orphan Memory Rate
- Duplicate / Near-Duplicate Rate
- Lineage Coverage
- Searchable Coverage Ratio
- Admission Lag

These are operational health indicators, not required public schema fields.
