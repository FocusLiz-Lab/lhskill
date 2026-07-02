---
name: lhs-roadmap
description: |
  Leila Hormozi roadmap workflow with default IMA knowledge-base retrieval. Use when the user needs a 7-day, 30-day, 60-day, or 90-day action plan for leadership, hiring, operations, founder execution, decision-making, team accountability, or applying LeilaHormozi 知识库 | 商业实战 to a real project.
---

# lhs-roadmap

Build a practical roadmap from the user's current constraint to measurable next actions.

## Default Source

Default IMA knowledge base:

```text
LeilaHormozi 知识库 | 商业实战
```

Use `ima-skill` for retrieval. Do not expose internal IMA IDs.

## Commercial Case Library Gate

If the roadmap task requires external business cases, benchmark projects, commercial teardowns, monetization examples, operating case studies, 生财有术案例, or 商业案例库 evidence, first check the shared `$commercial-case-library` dependency:

```text
~/.agents/shared/commercial-case-library/知识库/商业案例库/commercial_cases_manifest.json
```

If missing, pause and ask:

```text
这个路线图任务需要商业案例库，但本地共享案例库还没有下载。是否现在下载？下载一次后 dkskill、lhskill、openskill 都可以共用。
```

If the user agrees, route to `$commercial-case-library` and run its downloader, then continue. If the user declines, continue with Leila source material only and say no commercial-case retrieval was used.

## Diagnose First

Identify the dominant constraint:

- Leadership: unclear standards, weak feedback, avoidance of hard conversations.
- Hiring: vague role, weak pipeline, poor interview evidence, slow performance calls.
- Operations: too many priorities, no owner, no cadence, no metric.
- Decision-making: overthinking, unclear tradeoff, fear of conflict, delayed action.
- Self-management: mood-dependent execution, low patience, identity conflict.

## Output Template

```markdown
# Leila Hormozi 行动路线图

## IMA 检索摘要

## 当前最大约束

## 目标结果

## 7 天动作
1.
2.
3.

## 30 天节奏

## 90 天系统化

## 指标与复盘

## 风险和反模式
```

## Quality Bar

- Every action must have an owner, output, and review date when the user context allows it.
- Prefer small tests and operating cadence over motivational advice.
- Separate Leila-source evidence from your inferred application.

