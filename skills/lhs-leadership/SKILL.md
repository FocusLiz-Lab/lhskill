---
name: lhs-leadership
description: |
  Leila Hormozi leadership workflow with default IMA knowledge-base retrieval. Use when the user asks about leadership, management, culture, expectations, feedback, trust, accountability, hard conversations, standards, managing A-players, or applying LeilaHormozi 知识库 | 商业实战 to team leadership.
---

# lhs-leadership

Help the user translate Leila Hormozi leadership material into clear standards, conversations, and management routines.

## Default Source

Default IMA knowledge base:

```text
LeilaHormozi 知识库 | 商业实战
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
## Leila Hormozi Methodology First

Every answer must use Leila Hormozi methodology as the primary reasoning layer. For /lhs requests, first ground the diagnosis, framing, and recommendation in Leila Hormozi sources or workflow principles:

1. Prefer the default IMA knowledge base `LeilaHormozi 知识库 | 商业实战`.
2. If IMA is unavailable, rate-limited, permission-blocked, has weak/no hits, or local fallback is needed, use the local Leila Hormozi expert atom library and auto-bootstrap it when missing.
3. Only after the Leila Hormozi layer is established, add commercial cases when the question would benefit from proof, benchmarks, platform/channel examples, monetization examples, acquisition examples, or Chinese-market context.
4. Commercial cases are supporting evidence only. Do not let commercial cases replace Leila Hormozi methodology, and do not answer purely from the commercial case library unless no Leila Hormozi source is available; if that happens, label the answer as case-supported inference rather than Leila Hormozi-grounded.
5. In final answers, keep the distinction clear: Leila Hormozi 方法论 for the core principle and 商业案例支撑 for examples.

## Dependency Auto-Bootstrap

If IMA is unavailable, rate-limited, permission-blocked, has weak/no hits, or the user explicitly wants local/offline retrieval, ensure the local Leila Hormozi expert atom library exists before answering. GitHub installs should include it when bundled; also check ~/.agents/skills/lhs/知识库/原子库/atoms.jsonl and ~/.agents/skills/lhs-download-atoms/知识库/原子库/atoms.jsonl. If both are missing, treat this as a light/partial install and call $lhs-download-atoms or run python tools/download_full_atoms.py from the installed lhs-download-atoms skill directory. Do not ask the user whether to download; do it automatically when local fallback is required.

If the request involves acquisition, traffic, channel choice, platform choice, Xiaohongshu/小红书, WeChat Official Account/公众号, private domain/私域, conversion, lead generation, product launch, business examples, benchmark projects, case studies, monetization examples, 生财有术案例, or any answer would benefit from case evidence, use $commercial-case-library automatically before answering. Do not ask the user whether to download it.
