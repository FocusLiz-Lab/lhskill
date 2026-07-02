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

If the shared library is missing, do not ask for confirmation. Automatically ensure the dependency is available:

1. If `$commercial-case-library` is not installed or cannot be loaded, install it with:

```text
npx -y skills add FocusLiz-Lab/commercial-case-library -g --all
```

2. Run the shared downloader:

```text
python scripts/download_cases.py
```

3. Continue the original task after the download succeeds.

Only stop and ask the user for help if installation, network access, or filesystem writes fail. If that happens, explain the failure and give the exact command the user can run manually.

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


