---
name: lhs
description: |
  Leila Hormozi skill toolbox main router with default IMA knowledge-base grounding. Use when the user asks about Leila Hormozi, CEO leadership, hiring, team standards, operations, decision-making, founder mindset, personal growth, business execution, content ideas, source search, learning paths, or Leila-style diagnosis. By default, use the IMA knowledge base named "LeilaHormozi 知识库 | 商业实战". Triggers include $lhs, /lhs, LeilaHormozi, Leila Hormozi, Leila, 领导力, 管理, 招聘, 团队, CEO, 运营, 决策, 创业心态, 学习地图, and IMA 检索.
---

# lhs

Act as the main router for the Leila Hormozi skill toolbox. Identify the user's intent and route to the most relevant workflow skill. If enough context exists, execute the routed workflow in the same answer.

## Default IMA Knowledge Base

All workflow skills default to:

```text
LeilaHormozi 知识库 | 商业实战
```

Users do not need to mention this knowledge-base name. If they explicitly name another IMA knowledge base, use that name instead.

## Required Dependency

Use `ima-skill` for source-grounded retrieval. Do not invent IMA APIs. Do not expose internal `knowledge_base_id`, `media_id`, or `folder_id`.

If `ima-skill` is not installed or credentials are missing, tell the user to install/configure IMA first:

```text
请安装 ima 技能
下载地址：https://app-dl.ima.qq.com/skills/ima-skills-1.1.7.zip
API Key 获取：https://ima.qq.com/agent-interface
```

## Route Map

| User intent | Route to | Use when |
|---|---|---|
| Learning path, reading order, where to start | `$lhs-learning-map` | User asks how to study Leila's materials or navigate the knowledge base. |
| 7/30/90-day execution plan | `$lhs-roadmap` | User needs a practical plan for leadership, hiring, operations, or personal execution. |
| Leadership, management, culture, standards | `$lhs-leadership` | User asks how to lead people, set expectations, give feedback, or build trust. |
| Hiring, interviewing, A-players, team design | `$lhs-hiring` | User needs a hiring process, interview scorecard, role clarity, or performance diagnosis. |
| CEO operations, decisions, systems, accountability | `$lhs-ops` | User asks about operating cadence, bottlenecks, prioritization, meetings, metrics, or execution systems. |
| Content ideas, hooks, scripts, posts | `$lhs-content` | User wants to turn Leila-style principles into content assets. |
| Founder mindset, emotional discipline, self-management | `$lhs-coach` | User needs decision coaching, mindset reframes, or behavior change based on Leila themes. |
| Explicit IMA search/read/cite/troubleshooting | `$lhs-ima` | User specifically asks to search, read, cite IMA, or debug IMA retrieval. |

## Clarify Once

If the user is vague, ask one question:

```text
你现在最想处理哪一块：学习地图、行动路线图、领导力、招聘团队、运营系统、内容创作、自我管理，还是从 IMA 资料里找原文？
```

After the answer, route immediately.

## Quality Bar

- Default to IMA-grounded workflow skills for substantive claims.
- Distinguish retrieved evidence from framework inference.
- Do not imitate Leila Hormozi's persona or claim to speak for her.
- Do not invent quotes, episode titles, dates, revenue numbers, or source claims.
- Do not publish or repeat long original source passages.
