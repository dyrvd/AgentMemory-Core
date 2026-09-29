# Milestone System

## Purpose

A long project can contain thousands of messages and source records.

A new agent should not need to reread all of them to understand the major history.

Milestones are a compact navigation layer for important events.

## Good milestone candidates

Create a milestone when an event materially changes what a future agent should know, for example:

- major decision,
- architecture adoption,
- rejection,
- important test result,
- significant failure,
- correction,
- handoff,
- release,
- rollback,
- major scope change.

Do not create a milestone for every source or every message.

## Minimum fields

A milestone should contain:

- milestone_id
- product_id
- time
- type
- status
- summary
- source_pointers
- optional previous_milestone_id
- optional next_milestone_id
- optional unresolved
- optional related_memory_ids

## Compression rule

Milestones compress history but do not erase it.

Preferred structure:

~~~text
many sources
  -> memory entries
  -> important findings
  -> milestones
  -> major decisions / current state
~~~

## Correction rule

Corrections should append a new historical event rather than silently rewriting the fact that an older milestone existed.

A corrected milestone may be marked:

- SUPERSEDED,
- CORRECTED,
- WITHDRAWN,
- HISTORICAL.

The new milestone should point back to the old one when relevant.

## Cold-start use

For an existing product, a new agent should usually read:

1. current product pointer,
2. recent milestones,
3. unresolved milestones,
4. lineage around those milestones,
5. detailed memories only when needed.

This keeps onboarding small even when the archive is large.
