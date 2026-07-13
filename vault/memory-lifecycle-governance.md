---
type: Synthesis
title: Memory Lifecycle Governance
description: Treating agent memory as governed records with provenance, scope, validity, supersession, redaction, deletion, and auditability rather than an append-only store.
tags: [synthesis, agent-memory, governance, privacy, provenance, temporal-data]
timestamp: 2026-07-13T02:43:17Z
---

# Memory Lifecycle Governance

Agent memory should be managed as a lifecycle of governed records, not as a permanent transcript or vector collection. A useful record carries not only content but also its provenance, scope, temporal validity, and state.

## The Lifecycle

1. **Write selectively** — extract only information that is durable and useful enough to affect later work.
2. **Validate and classify** — reject or redact sensitive content; attach tenant, user, agent, project, and permission scope before indexing.
3. **Version over time** — when a fact changes, mark the old record superseded with a valid-until boundary and activate the replacement at its valid-from boundary.
4. **Retrieve under policy** — enforce scope, permission, temporal validity, and provenance constraints before relevance ranking can influence the prompt.
5. **Forget completely** — deletion must propagate to vector indexes, caches, summaries, and other derived forms while retaining an appropriate deletion audit event.

## Why It Matters

Naively appending turns preserves contradictory facts and can retain PII. Naively overwriting loses the historical context needed to answer time-bound questions. Lifecycle governance permits both: “where does the user live now?” and “where did they live before moving?”

It also makes multi-agent sharing safer. Private memory can remain private by default, while a write to project or organization scope is deliberate, attributable, and filtered on subsequent reads.

## Practical Use

Use explicit record metadata such as source, writer, created time, effective time range, state (`active`, `superseded`, `redacted`, `deleted`), scope, and access policy. Keep raw events separate from mutable derived memories so corrections and deletion requests have a traceable lineage.

## Limitations

Metadata and propagation add operational work, especially for summaries that combine records from different scopes. Policies must also distinguish genuine updates from ambiguity: conflicting facts should not automatically overwrite each other.

## Sources

- [How AI Agent Memory Works dossier](/dossiers/how-ai-agent-memory-works.md) — presents write, age, supersede, redact, forget, and audit as the memory lifecycle, with temporal updates, PII filtering, scoped sharing, and deletion propagation.
