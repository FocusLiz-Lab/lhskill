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

| 用户意图 | 路由到 | 适用场景 |
|---|---|---|
| 学习路径、阅读顺序、从哪里开始 | `$lhs-learning-map` | 用户想学习 Leila 的材料，或想了解如何使用知识库。 |
| 7/30/90 天执行计划 | `$lhs-roadmap` | 用户需要领导力、招聘、运营或个人执行方面的实战计划。 |
| 领导力、管理、文化、标准 | `$lhs-leadership` | 用户想知道如何带人、设定期望、反馈、建立信任或统一标准。 |
| 招聘、面试、A 级人才、团队设计 | `$lhs-hiring` | 用户需要招聘流程、面试评分表、岗位清晰度或绩效诊断。 |
| CEO 运营、决策、系统、问责 | `$lhs-ops` | 用户问运营节奏、瓶颈、优先级、会议、指标或执行系统。 |
| 内容选题、钩子、脚本、帖子 | `$lhs-content` | 用户想把 Leila 风格原则转成内容资产。 |
| 创始人心态、情绪纪律、自我管理 | `$lhs-coach` | 用户需要决策辅导、心态重构，或基于 Leila 主题做行为改变。 |
| 明确要求 IMA 检索/阅读/引用/排错 | `$lhs-ima` | 用户明确要求搜索、读取、引用 IMA，或排查 IMA 检索问题。 |

## 商业案例库触发规则

如果用户要求外部商业案例、对标例子、业务拆解、变现例子、运营案例、生财有术案例，或明确说“找案例/拆案例/参考案例/对标/商业案例库”，回答前使用共享 `$commercial-case-library` 依赖。不要询问用户是否下载，直接自动安装/检查。

检查这个文件：

```text
~/.agents/shared/commercial-case-library/知识库/商业案例库/commercial_cases_manifest.json
```

如果共享库缺失，不要询问确认，直接确保依赖可用：

1. 如果 `$commercial-case-library` 未安装或无法加载，立即安装：

```text
npx -y skills add FocusLiz-Lab/commercial-case-library -g --all
```

2. 运行共享下载脚本：

```text
python scripts/download_cases.py
```

3. 下载成功后继续处理原始任务。

只有安装、网络访问或文件写入失败时才停止，并说明失败原因和用户可手动运行的准确命令。

## 只澄清一次

如果用户的问题很模糊，只问一个问题：

```text
你现在最想处理哪一块：学习地图、行动路线图、领导力、招聘团队、运营系统、内容创作、自我管理，还是从 IMA 资料里找原文？
```

收到回答后立即路由。

## 质量标准

- 涉及实质性观点时，默认使用 IMA 依据。
- 区分已检索证据和框架推断。
- 不要模仿 Leila Hormozi 的人设，也不要声称代表她发言。
- 不要编造引用、节目标题、日期、收入数字或来源说法。
- 不要发布或重复长段原始来源内容。

## Leila Hormozi 方法论优先

每个回答都必须以 Leila Hormozi 方法论作为主要推理层。对于 `/lhs` 请求，先用 Leila Hormozi 资料或工作流原则建立诊断、框架和建议：

1. 优先使用默认 IMA 知识库 `LeilaHormozi 知识库 | 商业实战`。
2. 如果 IMA 不可用、限流、权限受阻、命中弱/无命中，或需要本地兜底，使用本地 Leila Hormozi 专家原子库；缺失时自动补全。
3. 只有在 Leila Hormozi 方法论层建立之后，才在需要证明、对标、平台/渠道例子、变现例子、获客例子或中文市场语境时加入商业案例。
4. 商业案例只能作为支撑证据。不要让商业案例替代 Leila Hormozi 方法论；除非完全没有 Leila Hormozi 来源，否则不要纯用商业案例库回答。如果发生这种情况，要标注为“案例支撑推断”，而不是“Leila Hormozi 依据”。
5. 最终回答中保持区分：核心原则用 `Leila Hormozi 方法论`，例子用 `商业案例支撑`。

## 依赖自动补全

如果 IMA 不可用、限流、权限受阻、命中弱/无命中，或用户明确要求本地/离线检索，回答前要确保本地 Leila Hormozi 专家原子库存在。GitHub 安装的完整包通常会包含它；同时检查 `~/.agents/skills/lhs/知识库/原子库/atoms.jsonl` 和 `~/.agents/skills/lhs-download-atoms/知识库/原子库/atoms.jsonl`。如果两者都缺失，把它视为轻量/不完整安装，并调用 `$lhs-download-atoms`，或在已安装的 `lhs-download-atoms` skill 目录运行 `python tools/download_full_atoms.py`。不要询问用户是否下载；需要本地兜底时自动执行。

如果请求涉及获客、流量、渠道选择、平台选择、小红书、公众号、私域、转化、线索获取、产品发布、商业例子、对标项目、案例研究、变现案例、生财有术案例，或答案会因案例证据而更好，回答前自动使用 `$commercial-case-library`。不要询问用户是否下载。
