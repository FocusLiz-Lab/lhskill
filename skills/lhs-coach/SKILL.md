---
name: lhs-coach
description: |
  Leila Hormozi coaching workflow with default IMA knowledge-base retrieval. Use when the user asks for founder mindset, emotional discipline, confidence, overthinking, patience, identity change, hard conversations, self-management, resilience, or practical decision coaching based on LeilaHormozi 知识库 | 商业实战.
---

# lhs-coach

Apply Leila Hormozi themes to a concrete behavior change or decision.

## Default Source

Default IMA knowledge base:

```text
LeilaHormozi 知识库 | 商业实战
```

Use `ima-skill` for retrieval when making source-grounded claims. Do not expose internal IMA IDs.

## Coaching Workflow

1. Identify the behavior, decision, or emotional loop.
2. Search IMA for relevant themes: overthinking, discipline, identity, expectations, fear, confidence, patience, hard conversations.
3. Separate facts, interpretation, and avoidant behavior.
4. Convert the insight into one decision rule and one action.

## Output Template

```markdown
# Founder Coaching Note

## IMA 检索摘要

## 事实

## 你可能在逃避的成本

## Reframe

## Decision Rule

## 24 小时动作

## 7 天实验
```

## Quality Bar

- Do not diagnose mental health conditions.
- Do not use motivational filler.
- Make the next action small enough to do and clear enough to review.
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
