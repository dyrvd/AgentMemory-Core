# Synthetic Demo Product

This example is intentionally fictional.

No IDs, names, timelines, source references, or project details in this folder correspond to a private production system.

## Scenario

PRODUCT_ALPHA develops a search component.

~~~text
REQ-001  Faster bounded retrieval is requested.
DESIGN-002  A broad full-storage search is proposed.
TEST-003  The broad search returns noisy cross-product matches.
FAILURE-004  Retrieval precision is judged insufficient.
DECISION-005  Route-first retrieval is adopted.
FIX-006  Two-level routing is implemented.
TEST-007  Product-scoped retrieval returns the intended memory set.
MS-008  Route-first retrieval becomes the current approach.
~~~

## Example Level 1 route

~~~json
{
  "collection_id": "COLLECTION_DEMO",
  "product_id": "PRODUCT_ALPHA",
  "workstream_id": "RETRIEVAL",
  "era": "R2",
  "topic": "SEARCH_PRECISION"
}
~~~

## Example Level 2 memory

~~~json
{
  "memory_id": "MEM-0042",
  "collection_id": "COLLECTION_DEMO",
  "product_id": "PRODUCT_ALPHA",
  "workstream_id": "RETRIEVAL",
  "domain": "MEMORY",
  "era": "R2",
  "topic": "SEARCH_PRECISION",
  "actor_id": null,
  "summary": "Route-first retrieval replaced broad full-storage search after noisy cross-product matches.",
  "status": "CURRENT",
  "source_pointer": "SOURCE-DEMO-0091",
  "source_location": "section:decision-005",
  "milestone_ids": ["MS-0008"],
  "lineage_node_ids": ["DECISION-005", "FIX-006", "MS-008"],
  "tags": ["route-first", "two-level-index"],
  "created_at": "2026-01-10T10:00:00Z",
  "updated_at": "2026-01-12T10:00:00Z"
}
~~~

## Example milestone

~~~json
{
  "milestone_id": "MS-0008",
  "product_id": "PRODUCT_ALPHA",
  "time": "2026-01-12T10:00:00Z",
  "type": "ADOPTION",
  "status": "ACTIVE",
  "summary": "Route-first two-level retrieval adopted as the current search path.",
  "source_pointers": ["SOURCE-DEMO-0091"],
  "previous_milestone_id": null,
  "next_milestone_id": null,
  "related_memory_ids": ["MEM-0042"],
  "unresolved": []
}
~~~

## Expected recovery behavior

A new agent should not read every synthetic source.

It should:

1. route to PRODUCT_ALPHA,
2. inspect the retrieval branch,
3. resolve MEM-0042,
4. read MS-0008,
5. trace the nearby lineage if the user asks why,
6. open SOURCE-DEMO-0091 only if exact evidence is required.
