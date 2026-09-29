# Memory Lineage / Product Narrative

## Purpose

Finding one memory answers:

**What happened?**

Lineage should also answer:

**How did this become the current state?**

## Nodes

A lineage graph may contain node types such as:

- REQUIREMENT
- DESIGN
- DECISION
- ARTIFACT
- TEST
- FAILURE
- CORRECTION
- MILESTONE
- RELEASE
- ROLLBACK

A deployment may add domain-specific node types, but the public core does not require them.

## Edges

The minimal public edge vocabulary is:

- previous
- next
- caused_by
- supersedes
- derived_from
- validated_by

Do not use caused_by when only chronological order is known.

## Example

~~~text
REQ-001
  -> DESIGN-002
  -> TEST-003
  -> FAILURE-004
  -> DECISION-005
  -> FIX-006
  -> TEST-007
  -> MS-008
~~~

A future agent can summarize this chain first, then open exact source pointers only where necessary.

## Narrative query types

The lineage layer should support questions such as:

- Why is the current design like this?
- What changed during the last six months?
- Did we try this before?
- Which failure caused this redesign?
- What replaced the previous approach?
- What remains unresolved?

## Boundary

Lineage is evidence-linked history, not free-form storytelling.

If a causal relation is unsupported:

- store chronological relation only,
- mark uncertainty,
- or omit the edge.

The goal is reconstructable history, not a plausible invented narrative.
