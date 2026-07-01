# lhskill

Leila Hormozi 风格领导力、招聘、运营与创始人执行 Skill 工具箱。

`lhskill` 是一组面向 Agent 的 workflow skills，用来基于 IMA 知识库学习 Leila Hormozi 风格资料，并完成领导力诊断、团队招聘、CEO 运营、个人成长、行动路线图和内容资产生成。

适用于 Codex、Claude Code、Cursor、Trae Solo 等支持 skill / system prompt 工作流的 Agent。

---

## 安装

发布后，可以用下面的命令安装整套 skills：

```bash
npx -y skills add FocusLiz-Lab/lhskill -g --all
```

安装后可以直接使用：

```text
$lhs 团队执行力差，帮我按 Leila Hormozi 的管理思路拆一下。
```

也可以手动复制或导入 `skills/` 目录下的 skill 文件夹。

## IMA 配置

整套 workflow skills 默认读取这个 IMA 知识库：

```text
LeilaHormozi 知识库 | 商业实战
```

用户不需要在每次提问时输入知识库名称。如果想使用其他 IMA 知识库，在问题里直接写知识库名称即可。

### 加入 / 访问知识库

扫描下面的二维码，加入或访问对应知识库：

![知识库二维码](docs/knowledge-base-qrcode.png)

### 安装 IMA Skill

```text
请安装 ima 技能
下载地址：https://app-dl.ima.qq.com/skills/ima-skills-1.1.7.zip
API Key 获取：https://ima.qq.com/agent-interface
```

使用前需要满足：

- 已安装官方 `ima-skill`
- 已配置 IMA `Client ID` 和 `API Key`
- 当前 IMA 账号有权限访问目标知识库

本仓库不包含、也不会保存任何 IMA API Key。

## 工具箱

| Skill | 用途 |
|---|---|
| `$lhs` | 主入口。根据用户问题自动路由到合适的 Leila workflow。 |
| `$lhs-learning-map` | 学习地图：先学什么、阅读顺序、学习产出。 |
| `$lhs-roadmap` | 行动路线图：7/30/90 天执行计划。 |
| `$lhs-leadership` | 领导力：标准、反馈、信任、问责和困难对话。 |
| `$lhs-hiring` | 招聘团队：岗位 scorecard、面试证据、A-player 判断、绩效节奏。 |
| `$lhs-ops` | CEO 运营：优先级、会议、指标、owner 和系统化执行。 |
| `$lhs-content` | 内容系统：选题、hook、短视频脚本、内容支柱。 |
| `$lhs-coach` | 创始人教练：情绪纪律、过度思考、决策规则、自我管理。 |
| `$lhs-ima` | 可选 IMA 检索入口：搜索、阅读、引用或排查 IMA。 |

## 常见路径

### 从学习到团队应用

```text
lhs-learning-map
    ↓
lhs-leadership
    ↓
lhs-roadmap
```

### 从招聘到绩效

```text
lhs-hiring
    ↓
lhs-leadership
    ↓
lhs-ops
```

### 从个人瓶颈到运营系统

```text
lhs-coach
    ↓
lhs-ops
    ↓
lhs-roadmap
```

## 使用示例

```text
$lhs-learning-map 系统学习这个知识库，先看哪些？
```

```text
$lhs-hiring 帮我设计一个运营负责人岗位的面试 scorecard。
```

```text
$lhs-leadership 团队成员总是错过 deadline，我应该怎么开这个反馈会？
```

```text
$lhs-ops 公司现在事情很多但推进很慢，帮我设计一套周运营节奏。
```

```text
$lhs-content 围绕领导力和招聘，生成 30 个短内容选题。
```

## SkillHub 轻量包与全量原子库

SkillHub 单个上传包限制小于 10MB，因此 SkillHub 压缩包是轻量包，不直接内置完整 `atoms.jsonl`。安装后如果需要本地离线兜底检索，调用：

```text
$lhs-download-atoms
```

或在 lhskill 安装目录中运行：

```powershell
python tools/download_full_atoms.py
```

它会自动从 GitHub 下载并安装完整原子库到：

```text
知识库/原子库/atoms.jsonl
知识库/原子库/atoms_*.jsonl
```

如果需要手动下载，也可以在 GitHub Release 中下载 `lhs-local.zip`，它包含完整本地原子库。

## 知识库 / 原子库

本仓库包含一个发布安全的抽象原子库：

```text
知识库/原子库/atoms.jsonl
```

它用于保存 Leila Hormozi 风格 workflow 的方法论单元，不包含视频文稿、X/Twitter 原文、书籍原文、课程材料或私有资料。

## 资料边界

本仓库只包含 skill instructions 和 workflow 抽象。

本仓库不包含 Leila Hormozi 的原始 YouTube 转录稿、X/Twitter 归档、书籍、PDF、付费材料、私有资料文件夹或任何受版权保护的原始资料库。

这些 skills 会在运行时从用户自己的 IMA 知识库检索资料。用户需要自行确保有权上传和使用自己的资料。

请不要提交：

- IMA API Key
- 私有资料文件
- 原始 PDF、转录稿、视频或归档
- 个人环境配置
- 任何未经授权的第三方内容

## 许可证

本项目默认采用 CC BY-NC 4.0 许可证，除非后续另行添加其他许可证。

许可证只覆盖本仓库原创的 skill instructions 和 workflow 抽象，不授权任何第三方原始资料。
