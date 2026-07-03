---
name: lhs-hiring
description: |
  Leila Hormozi hiring and team workflow with local atom-library retrieval; IMA retrieval only when explicitly requested. Use when the user asks about hiring, interviewing, A-players, role scorecards, candidate evaluation, onboarding, performance diagnosis, firing decisions, team structure, or LeilaHormozi 知识库 | 商业实战 applied to people operations.
---

# lhs-hiring

Design hiring and team-performance workflows grounded in Leila Hormozi material.

## Default Source

Default IMA knowledge base:

```text
LeilaHormozi 知识库 | 商业实战
```

Use `ima-skill` for retrieval. Do not expose internal IMA IDs.

## Core Workflow

1. Define the business outcome the role must own.
2. Convert the outcome into a role scorecard: responsibilities, measurable outputs, traits, must-have evidence.
3. Search IMA for relevant hiring, talent, A-player, interview, onboarding, and performance themes.
4. Build an interview or performance process that collects evidence rather than impressions.
5. Identify the next decision: keep searching, hire, trial, coach, reassign, or exit.

## Output Template

```markdown
# Hiring / Team System

## IMA 检索摘要

## Role Outcome

## Scorecard

## Interview Evidence

## Onboarding / Performance Cadence

## Decision Rule
```

## Quality Bar

- Do not treat charisma as evidence.
- Require examples, artifacts, references, or work samples when possible.
- Keep legal and HR sensitivity in mind; avoid definitive legal advice.
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
