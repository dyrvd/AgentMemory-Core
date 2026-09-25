# AgentMemory-Core

> A Lightweight, Deterministic Long-Term Memory & Governance Architecture for AI Multi-Agent Systems.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📌 Overview
`AgentMemory-Core` is a zero-dependency, structured memory management framework designed to solve Context Window inflation, hallucination, and state drift in multi-agent workflows.

By employing **Three-Layer Separation**, **Event Anchor Referencing**, and **Active Status Caching**, it allows long-term project sessions (500+ sessions / 90k+ messages) to be indexed and maintained within a **<100MB plain-text footprint**, cutting API Token consumption by **80%+**.

---

## 🔑 Core Features

### 1. Three-Layer Boundary Separation (Audit Safety)
Strict physical and semantic isolation between three types of memory states:
* **Raw Human Directives**: Single Source of Truth (never overwritten by AI).
* **AI Proposals**: Exploratory outputs and intermediate reasoning.
* **Approved Specifications**: User-validated active states.

### 2. Event Anchor Threading
Instead of storing full-text conversation dumps in context, tasks are tracked via **Event Anchors**. New AI agents can load specific narrative/logic threads without reading irrelevant historic chats.

### 3. Active Status Caching (Task Cache)
New sessions onboard via a dynamic `CURRENT_TASK_HANDOFF.md` and `Active Status` index, getting up to speed in <10 seconds without raw history re-feeding.

### 4. ISO 8601 Time-Deterministic Replay
Supports strict temporal truncation to replay AI memory state at any exact historical timestamp, preventing hindsight bias.

---

## 📊 Benchmark & Footprint
* **Scale Test**: 568 Sessions / 91,648 Messages.
* **Storage Footprint**: < 100 MB (Plain-text UTF-8 + Structured JSON Index).
* **Token Cost Efficiency**: ~80%+ reduction in direct context dumping for long-term task continuation.

---

## 🛠 Repository Structure

```text
AgentMemory-Core/
├── schemas/
│   ├── event_anchor_schema.json     # Schema for tracking storyline event chains
│   └── active_status_schema.json    # Schema for active valid specs & task caches
├── tools/
│   ├── reconcile.py                 # Hash verification & strict ordinal check script
│   └── query_memory.py              # Lightweight indexing & retrieval CLI tool
└── templates/
    └── CURRENT_TASK_HANDOFF.md      # Template for seamless session handoffs
