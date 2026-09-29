# AgentMemory-Core

> Recoverable long-term memory for AI agents: two-level indexing, milestones, retrieval skills, and memory lineage.

AgentMemory-Core is a small public reference architecture for one problem:

**An AI agent may lose context, but a long-running project should still be able to recover what happened, what matters now, and where the supporting source lives.**

This repository does not try to make a model internally remember forever. It defines an external memory structure that can survive new chats, new agents, model changes, and long project timelines.

## The four public cores

### 1. Two-Level Memory Index
Use a broad route index first, then a precise memory index.

- Level 1 answers: Where should I search?
- Level 2 answers: Which exact memory or source should I read?
- Do not begin with a global full-storage search when a collection or product route is known.

### 2. Milestone System
Compress long histories into important checkpoints without deleting the underlying evidence.

A milestone records a major decision, failure, correction, handoff, release, rollback, or other event that a future agent should see before reading detailed history.

### 3. Memory Retrieval Skills
A small set of procedures tells an agent how to:

- search the right scope,
- resolve ambiguous candidates,
- trace related memories,
- and read the exact source only when needed.

### 4. Memory Lineage / Product Narrative
Link events so an agent can answer not only “what do we remember?” but also:

**How did this product or project become what it is now?**

Typical lineage:

~~~text
Requirement
  -> Design
  -> Test
  -> Failure
  -> Decision
  -> Repair
  -> Validation
  -> Current state
~~~

## Core retrieval flow

~~~text
User request
  -> choose collection / product
  -> Level 1 route index
  -> Level 2 fine index
  -> relevant memory summary
  -> milestone / lineage when needed
  -> exact source only when evidence is required
~~~

The design principle is:

**Store broadly. Retrieve narrowly.**

Large archives are acceptable. Large working contexts are not required.

## Long-term use

The architecture is intended for projects that may last months or years. Memory lifetime depends mainly on storage durability, index maintenance, and source-pointer integrity rather than one model session.

This does not guarantee perfect recall. It provides a structured way to recover memory after context loss.

## Repository structure

~~~text
AgentMemory-Core/
├── README.md
├── PUBLIC_SCOPE_AND_PRIVATE_BOUNDARY.md
├── docs/
│   ├── architecture.md
│   ├── two-level-index.md
│   ├── milestone-system.md
│   └── memory-lineage.md
├── skills/
│   ├── memory-search/SKILL.md
│   ├── memory-resolve/SKILL.md
│   ├── memory-trace/SKILL.md
│   └── memory-read-source/SKILL.md
├── schemas/
│   ├── memory-index.schema.json
│   ├── milestone.schema.json
│   └── lineage.schema.json
├── examples/
│   └── demo-product/README.md
└── tests/
    └── conformance.md
~~~

## Minimal deployment model

A deployment only needs:

- durable storage,
- stable IDs,
- a Level 1 route index,
- a Level 2 fine index,
- milestone records,
- lineage edges,
- and a host capable of search + read.

Storage can be files, Git, SQLite, a database, cloud documents, or another backend.

## 中文摘要

AgentMemory-Core 不是讓模型「永遠不忘記」，而是讓 AI 在忘記之後仍知道：

- 要去哪裡找；
- 哪一筆記憶才是目標；
- 哪些事件是重要里程碑；
- 事情為什麼一路演變成現在這樣；
- 需要證據時如何回到真正來源。

公開範圍只包含：**雙層記憶索引、里程碑、記憶檢索 Skills、記憶串聯／產品事件鏈**。

其他私人 Skills、治理模組、產品內容、研究方法、資料集、原始對話與其他私人系統不在本 repository 的公開範圍。詳見 PUBLIC_SCOPE_AND_PRIVATE_BOUNDARY.md。
