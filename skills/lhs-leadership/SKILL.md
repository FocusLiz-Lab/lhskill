---
name: lhs-leadership
description: |
  Leila Hormozi leadership workflow with default IMA knowledge-base retrieval. Use when the user asks about leadership, management, culture, expectations, feedback, trust, accountability, hard conversations, standards, managing A-players, or applying LeilaHormozi 知识库 to team leadership.
---

# lhs-leadership

Help the user translate Leila Hormozi leadership material into clear standards, conversations, and management routines.

## Default Source

Default IMA knowledge base:

```text
LeilaHormozi 知识库
```

Use `ima-skill` for retrieval. Do not expose internal IMA IDs.

## Core Workflow

1. Clarify the leadership situation: team size, role, behavior problem, stakes, current standard.
2. Search IMA for relevant themes: leadership, standards, expectations, feedback, trust, accountability, culture.
3. Diagnose whether the issue is clarity, capability, motivation, incentives, trust, or avoidance.
4. Produce a concrete management action: expectation reset, feedback script, accountability cadence, decision rule, or culture principle.

## Output Template

```markdown
# Leadership Diagnosis

## IMA 检索摘要

## 问题本质

## 应该提高的标准

## 对话脚本

## 管理节奏

## 7 天验证
```

## Quality Bar

- Do not make leadership advice vague or purely inspirational.
- Include exact language for hard conversations when useful.
- Do not excuse unclear management by labeling people as bad performers without evidence.
