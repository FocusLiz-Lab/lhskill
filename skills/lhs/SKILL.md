---
name: lhs
description: |
  Leila Hormozi 领导力与商业执行 Skill 工具箱主入口。用于 CEO 领导力、招聘、团队标准、运营、决策、创始人心态、个人成长、商业执行、内容选题、资料检索、学习路径和 Leila 风格诊断。默认使用 IMA 知识库「LeilaHormozi 知识库 | 商业实战」，并可在 IMA 不可用时读取本地原子库。触发词包括 $lhs、/lhs、Leila Hormozi、领导力、管理、招聘、团队、CEO、运营、决策、创业心态、学习地图和 IMA 检索。
---

# lhs Leila Hormozi 商业执行工具箱

这是 Leila Hormozi 领导力与商业执行工具箱的主入口。先判断用户意图，再路由到最相关的 workflow skill；如果上下文足够，直接在同一回答中完成对应工作流。

## 默认 IMA 知识库

所有 workflow skills 默认读取：

```text
LeilaHormozi 知识库 | 商业实战
```

用户不需要每次输入这个知识库名称。如果用户明确指定其他 IMA 知识库，则优先使用用户指定的知识库。

## 必要依赖

所有需要资料依据的 workflow 都使用 `ima-skill` 做检索。不要臆造 IMA API。不要向用户暴露内部 `knowledge_base_id`、`media_id` 或 `folder_id`。

如果没有安装 `ima-skill` 或凭证缺失，先提示用户安装并配置 IMA：

```text
请安装 ima 技能
下载地址：https://app-dl.ima.qq.com/skills/ima-skills-1.1.7.zip
API Key 获取：https://ima.qq.com/agent-interface
```

## 路由表

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

## Commercial Case Library Gate

If the user asks for external commercial cases, benchmark examples, business teardowns, monetization examples, operating case studies, 生财有术案例, or asks to "找案例/拆案例/参考案例/对标/商业案例库", use the shared `$commercial-case-library` dependency before answering.

Check for:

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


