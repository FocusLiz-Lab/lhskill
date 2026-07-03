---
name: lhs-content
description: |
  Leila Hormozi content workflow with local atom-library retrieval; IMA retrieval only when explicitly requested. Use when the user wants content ideas, hooks, scripts, posts, titles, newsletters, short videos, topic clusters, or to turn LeilaHormozi 知识库 | 商业实战 material into leadership, hiring, operations, mindset, or business execution content assets.
---

# lhs-content

Turn Leila Hormozi source material into content assets while preserving source boundaries.

## Default Source

Default IMA knowledge base:

```text
LeilaHormozi 知识库 | 商业实战
```

Use `ima-skill` for retrieval. Search terms should match the user's platform and topic plus leadership, hiring, CEO, operations, standards, decision, mindset, content, hook, script, 标题, 短视频.

## Commercial Case Library Gate

If the content task requires external business cases, benchmark posts/products, teardown angles, monetization examples, 生财有术案例, or 商业案例库 evidence, use the shared `$commercial-case-library` dependency before answering. Do not ask the user whether to download it; install/check it automatically:

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

## Content Jobs

Each piece should do one job:

```text
Name the hidden problem -> Raise standards -> Show the behavior change -> Give one practical next step
```

## Output Template

```markdown
# Leila-Style Content Map

## IMA 检索摘要

## Audience

## Core Belief Shift

## 5 Content Pillars

## 30 Topic Ideas

## 10 Hooks

## 3 Short Scripts

## CTA
```

## Quality Bar

- Do not copy long source passages.
- Do not claim a line is a direct quote unless it was retrieved and verified.
- Make content practical, direct, and tied to leadership, hiring, operations, or self-management behavior.
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
