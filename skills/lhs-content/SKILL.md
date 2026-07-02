---
name: lhs-content
description: |
  Leila Hormozi content workflow with default IMA knowledge-base retrieval. Use when the user wants content ideas, hooks, scripts, posts, titles, newsletters, short videos, topic clusters, or to turn LeilaHormozi 知识库 | 商业实战 material into leadership, hiring, operations, mindset, or business execution content assets.
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

If the content task requires external business cases, benchmark posts/products, teardown angles, monetization examples, 生财有术案例, or 商业案例库 evidence, first check the shared `$commercial-case-library` dependency:

```text
~/.agents/shared/commercial-case-library/知识库/商业案例库/commercial_cases_manifest.json
```

If missing, pause and ask:

```text
这个内容任务需要商业案例库，但本地共享案例库还没有下载。是否现在下载？下载一次后 dkskill、lhskill、openskill 都可以共用。
```

If the user agrees, route to `$commercial-case-library` and run its downloader, then continue. If the user declines, continue with Leila source material only and say no commercial-case retrieval was used.

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

