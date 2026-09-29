# memory-search

## Goal

Find the smallest relevant memory scope before reading detailed sources.

## Input

- user request
- optional collection or product hint
- available Level 1 route index

## Output

- bounded candidate route or routes
- search terms for Level 2
- confidence or ambiguity note

## Procedure

1. Extract the requested subject, product, workstream, era, and event type when available.
2. If collection or product is already known, stay inside it.
3. Query Level 1 before broad storage search.
4. Prefer explicit route matches over generic semantic similarity.
5. If several routes remain plausible, return several candidates instead of guessing.
6. If no route matches, widen only within the authorized parent scope.
7. Do not automatically search all storage unless the request explicitly requires cross-product discovery.

## Stop conditions

Stop and return ambiguity when:

- two products have the same name or topic,
- the current route cannot be distinguished from historical routes,
- or the required collection is unknown.

## Principle

**Route first. Search second.**
