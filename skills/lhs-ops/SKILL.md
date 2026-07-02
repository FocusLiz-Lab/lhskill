---
name: lhs-ops
description: |
  Leila Hormozi operations workflow with default IMA knowledge-base retrieval. Use when the user asks about CEO execution, operating cadence, meetings, accountability, priorities, decision-making, systems, delegation, metrics, bottlenecks, or applying LeilaHormozi 知识库 | 商业实战 to business operations.
---

# lhs-ops

Turn Leila Hormozi operating principles into a repeatable execution system.

## Default Source

Default IMA knowledge base:

```text
LeilaHormozi 知识库 | 商业实战
```

Use `ima-skill` for retrieval. Do not expose internal IMA IDs.

## Commercial Case Library Gate

If the operations task requires external operating cases, benchmark companies, business teardowns, monetization examples, 生财有术案例, or 商业案例库 evidence, first check the shared `$commercial-case-library` dependency:

```text
~/.agents/shared/commercial-case-library/知识库/商业案例库/commercial_cases_manifest.json
```

If missing, pause and ask:

```text
这个运营任务需要商业案例库，但本地共享案例库还没有下载。是否现在下载？下载一次后 dkskill、lhskill、openskill 都可以共用。
```

If the user agrees, route to `$commercial-case-library` and run its downloader, then continue. If the user declines, continue with Leila source material only and say no commercial-case retrieval was used.

## Operating Diagnosis

Check these failure modes:

- Too many priorities.
- No single owner.
- Meetings do not produce decisions.
- Metrics are lagging or decorative.
- Delegation lacks output definition.
- Hard decisions are delayed.
- The founder is substituting effort for system design.

## Output Template

```markdown
# CEO Operating System

## IMA 检索摘要

## Current Bottleneck

## Decision Rule

## Weekly Cadence

## Metrics

## Delegation Map

## Next 10 Business Days
```

## Quality Bar

- Prefer operating rhythm, metrics, and owner clarity over generic productivity advice.
- State assumptions when user context is thin.
- Separate evidence retrieved from IMA and inferred operating design.

