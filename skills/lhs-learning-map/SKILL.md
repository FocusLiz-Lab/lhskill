---
name: lhs-learning-map
description: |
  Leila Hormozi learning-map workflow with default IMA knowledge-base retrieval. Use when the user asks where to start, what Leila Hormozi materials to study first, how to learn leadership, hiring, CEO operations, decision-making, mindset, or how to turn the LeilaHormozi 知识库 | 商业实战 into a study plan, lesson map, or output-driven learning path.
---

# lhs-learning-map

Turn the Leila Hormozi knowledge base into a focused learning path tied to the user's goal.

## Default Source

Default IMA knowledge base:

```text
LeilaHormozi 知识库 | 商业实战
```

Use `ima-skill` for retrieval before recommending specific materials. Do not expose internal IMA IDs.

## Intake

Ask only for missing information:

```text
1. 你的目标是什么：领导力、招聘、运营、CEO 决策、个人成长、内容创作，还是整体学习？
2. 你现在处于哪一阶段：刚开始、带小团队、管理多层团队、正在扩张、遇到瓶颈？
3. 你想要什么输出：学习路径、材料顺序、练习任务、团队诊断、行动计划？
```

## Learning Routes

- Leadership path: standards -> expectation setting -> feedback -> trust -> accountability.
- Hiring path: role clarity -> A-player criteria -> interview evidence -> onboarding -> performance management.
- Operations path: decision rules -> priorities -> meeting cadence -> metrics -> execution review.
- Founder mindset path: emotional discipline -> patience -> hard conversations -> identity -> consistency.
- Content path: principle extraction -> audience pain -> hooks -> scripts -> reuse plan.

## Output Template

```markdown
# Leila Hormozi 学习地图

## 你的目标

## IMA 检索摘要
- 知识库：
- 检索词：
- 命中的材料：
- 可用证据：
- 不确定/缺失：

## 先看这 5 个
1.
2.
3.
4.
5.

## 7 天启动计划

## 30 天学习顺序

## 每次学习必须产出的东西

## 下一步 Skill
```

## Quality Bar

- Do not recommend "全部从头看".
- Learning must produce an output: leadership checklist, hiring scorecard, operating cadence, decision rule, content map, or behavior experiment.
- If IMA retrieval is unavailable, state the limitation clearly.
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
