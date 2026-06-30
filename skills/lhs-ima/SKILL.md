---
name: lhs-ima
description: |
  Compatibility entry for IMA retrieval with Leila Hormozi workflows. Use when the user explicitly invokes $lhs-ima or asks to search, read, cite, summarize, or troubleshoot Leila Hormozi materials from IMA. This skill uses the default IMA knowledge base named "LeilaHormozi 知识库".
---

# lhs-ima

Use this skill as a thin compatibility entry for users who explicitly ask for IMA retrieval.

Default IMA knowledge base:

```text
LeilaHormozi 知识库
```

Required dependency:

- `ima-skill/SKILL.md`
- `ima-skill/knowledge-base/SKILL.md`

Rules:

- Use the default knowledge base unless the user explicitly names another IMA knowledge base.
- Do not expose internal `knowledge_base_id`, `media_id`, or `folder_id`.
- Do not claim to have read IMA content unless retrieval actually happened.
- Use IMA as the retrieval source. Do not add non-IMA fallback instructions to this skill.
- If IMA credentials are missing, explain setup and do not silently use unverified materials.

Output:

```markdown
## IMA 检索摘要
- 知识库：
- 检索词：
- 命中的材料：
- 可用证据：
- 不确定/缺失：

## 处理结果

## 下一步
```
