# Public Scope and Private Boundary

## Public scope

This repository intentionally publishes only four generic memory components:

1. Two-Level Memory Index
2. Milestone System
3. Memory Retrieval Skills
4. Memory Lineage / Product Narrative

The repository may also include synthetic examples and conformance tests required to explain those four components.

## Out of scope

The following are intentionally not part of this repository:

- other private skills,
- broader governance systems,
- domain-specific creative or research methods,
- private product or project data,
- private research corpora,
- private datasets,
- original conversations,
- real actor histories,
- real milestone histories,
- private cloud identifiers,
- private local paths,
- private hashes or artifact identities,
- unpublished project structures,
- or any other private system not explicitly included here.

## No implied publication

The existence of a concept in this public repository does not imply that any private implementation, dataset, workflow, skill, project, or historical record has been published.

This repository is a clean public reference model. Examples must use synthetic names, IDs, events, and sources.

## Clean-room publication rule

Public examples should be created from scratch.

Do not publish a private database by merely replacing names or IDs.

Preferred process:

~~~text
private implementation
  -> extract generic principle
  -> rewrite public specification
  -> create synthetic schema
  -> create synthetic fixture
  -> test the public fixture independently
~~~

## Scope sentence

**Public: how the memory system works.  
Private: what a private memory system remembers, plus all unrelated private skills and methods.**
