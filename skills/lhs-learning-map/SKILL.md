---
name: lhs-learning-map
description: |
  Leila Hormozi learning-map workflow with default IMA knowledge-base retrieval. Use when the user asks where to start, what Leila Hormozi materials to study first, how to learn leadership, hiring, CEO operations, decision-making, mindset, or how to turn the LeilaHormozi 知识库 into a study plan, lesson map, or output-driven learning path.
---

# lhs-learning-map

Turn the Leila Hormozi knowledge base into a focused learning path tied to the user's goal.

## Default Source

Default IMA knowledge base:

```text
LeilaHormozi 知识库
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
