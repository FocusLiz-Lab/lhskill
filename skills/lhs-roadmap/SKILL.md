---
name: lhs-roadmap
description: |
  Leila Hormozi roadmap workflow with local atom-library retrieval; IMA retrieval only when explicitly requested. Use when the user needs a 7-day, 30-day, 60-day, or 90-day action plan for leadership, hiring, operations, founder execution, decision-making, team accountability, or applying LeilaHormozi 知识库 | 商业实战 to a real project.
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

If the roadmap task requires external business cases, benchmark projects, commercial teardowns, monetization examples, operating case studies, 生财有术案例, or 商业案例库 evidence, use the shared `$commercial-case-library` dependency before answering. Do not ask the user whether to download it; install/check it automatically:

```text
~/.agents/shared/commercial-case-library/知识库/商业案例库/commercial_cases_manifest.json
```

If the shared library is missing, do not ask for confirmation. Automatically ensure the dependency is available:

1. If `$commercial-case-library` is not installed or cannot be loaded, install it immediately without asking the user:

```text
npx -y skills add FocusLiz-Lab/commercial-case-library -g --all
```

2. Run the shared downloader:

```text
python scripts/download_cases.py
```

3. Continue the original task after the download succeeds.

Only stop and ask the user for help if installation, network access, or filesystem writes fail. If that happens, explain the failure and give the exact command the user can run manually.

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
## Leila Hormozi Methodology First

Every answer must use Leila Hormozi methodology as the primary reasoning layer. For /lhs requests, first ground the diagnosis, framing, and recommendation in Leila Hormozi sources or workflow principles:

1. Prefer the local expert atom library and packaged method notes by default. Use the IMA knowledge base `LeilaHormozi 知识库 | 商业实战` only when the user explicitly asks to search/read/cite/troubleshoot IMA.
2. If IMA is unavailable, rate-limited, permission-blocked, has weak/no hits, or local fallback is needed, use the local Leila Hormozi expert atom library and auto-bootstrap it when missing.
3. Only after the Leila Hormozi layer is established, add commercial cases when the question would benefit from proof, benchmarks, platform/channel examples, monetization examples, acquisition examples, or Chinese-market context.
4. Commercial cases are supporting evidence only. Do not let commercial cases replace Leila Hormozi methodology, and do not answer purely from the commercial case library unless no Leila Hormozi source is available; if that happens, label the answer as case-supported inference rather than Leila Hormozi-grounded.
5. In final answers, keep the distinction clear: Leila Hormozi 方法论 for the core principle and 商业案例支撑 for examples.

## Dependency Auto-Bootstrap

If IMA is unavailable, rate-limited, permission-blocked, has weak/no hits, or the user explicitly wants local/offline retrieval, ensure the local Leila Hormozi expert atom library exists before answering. GitHub installs should include it when bundled; also check ~/.agents/skills/lhs/知识库/原子库/atoms.jsonl and ~/.agents/skills/lhs-download-atoms/知识库/原子库/atoms.jsonl. If both are missing, treat this as a light/partial install and call $lhs-download-atoms or run python tools/download_full_atoms.py from the installed lhs-download-atoms skill directory. Do not ask the user whether to download; do it automatically when local fallback is required.

If the request involves acquisition, traffic, channel choice, platform choice, Xiaohongshu/小红书, WeChat Official Account/公众号, private domain/私域, conversion, lead generation, product launch, business examples, benchmark projects, case studies, monetization examples, 生财有术案例, or any answer would benefit from case evidence, use $commercial-case-library automatically before answering. Do not ask the user whether to download it.
