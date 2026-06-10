# 纪要官.skill · summary-skill

> 一名沉稳、专业、滴水不漏的**机构投资经理访谈纪要官**。
> 一句"帮我把这份访谈整理成纪要"——从此告别在转写软件 / 文档编辑器 / 维度对账表之间反复切换。

![version](https://img.shields.io/badge/version-1.0.0-blue)
![license](https://img.shields.io/badge/license-MIT-green)
![platforms](https://img.shields.io/badge/platforms-Claude%20%7C%20WorkBuddy%20%7C%20OpenClaw%20%7C%20Hermes%20%7C%20SkillHub-orange)
![spec](https://img.shields.io/badge/spec-agentskills.io%20v1-black)
![made by](https://img.shields.io/badge/made%20by-OPC--Studio-1a1a4e)

---

## 这是什么

`summary-skill` 是一个符合 [agentskills.io](https://agentskills.io) 开放规范的 AI Agent 技能包。
安装后，你的 Agent 将具备**机构投资经理访谈纪要官**的完整工作能力——
把**原始转写文本**一键整理成**结构化、带时间戳、可归档**的专业访谈纪要，并附一张**信息缺口诊断表**。

---

## 它能做什么（6 大能力）

| # | 能力 | 产出 |
|---|---|---|
| 1 | **关键事实抽取** | 从原始转写中抠出数字 / 客户名 / 产品名 / 技术路线 / 融资数据 / 风险点，原话保留 |
| 2 | **主题归并与组织** | 按时间顺序排列主题；同主题不同时段补充统一回归首次出现位置 |
| 3 | **时间戳分级标注** | 首次出现 / 后文补充 / 时间待核查 三档分级，格式统一 |
| 4 | **5 大类 20 小项核查** | 行业 / 团队 / 产品业务 / 财务及融资 / 主要风险 覆盖度对账 |
| 5 | **信息缺口诊断** | 末尾产出"待确认问题清单"，直接喂给下一轮访谈 |
| 6 | **双格式产出** | Markdown 纪要（线上协作） + docx 排版规范（直接进档案室） |

---

## 何时触发

> 访谈纪要 · 调研纪要 · 把对话整理成纪要 · 把录音转成纪要 · 转写整理 · 纪要整理 · 投资经理纪要 · interview minutes · meeting minutes · call notes · transcript to minutes

详见 [`SKILL.md`](./SKILL.md) 第 2 节。

---

## 核心交付物

```
{公司名}访谈纪要.md          ← Markdown 版，线上协作 / 投决系统首选
{公司名}访谈纪要.docx 规范   ← docx 输出指令文档，对齐机构内部归档模板
待确认问题清单.md            ← 5 大类 20 小项缺口诊断 + 追问脚手架
```

**三件套同时产出。** 哪怕用户只问纪要，缺口表也默默生成放在末尾——这是本 skill 的差异化所在。

---

## 输出风格

输出对齐**投资机构内部纪要**的视觉语言：

- 🧭 **深蓝主调 `#1A1A4E`**（与 `investor-skill` 同源色板，跨 skill 拼装一致）
- 📝 **客观陈述**：用陈述句、第三人称视角，不写"我们认为"
- ⏱ **时间戳显性化**：每个主题块旁注明首次出现时间，便于回溯录音
- 🔍 **缺口可见**：访到 / 部分访到 / 未访到 三档标记，转化为下轮追问

---

## 安装

### Claude Code

```bash
git clone https://github.com/D-kart/summary-skill.git ~/.claude/skills/summary-skill
```

### WorkBuddy

```bash
git clone https://github.com/D-kart/summary-skill.git ~/.workbuddy/skills/summary-skill
```

### OpenClaw / Hermes

按各平台 skill 目录约定 clone 到对应位置。

### SkillHub

下载 Release zip，在 SkillHub 控制台「导入 Skill」上传即可。

---

## 兼容性声明

本 skill 同时声明兼容：

- **Claude Skills**（Anthropic Code）
- **WorkBuddy**（agentskills.io 规范）
- **OpenClaw**
- **Hermes**
- **SkillHub**

规范基准：**[agentskills.io](https://agentskills.io)** 开放规范 v1。

---

## 三层架构

```
summary-skill/
├── SKILL.md                      ← 主文档（必读）
├── README.md                     ← 项目门面（本文件）
├── CHANGELOG.md                  ← 版本记录
├── GLOSSARY.md                   ← 投资 / 访谈术语对照
├── LICENSE                       ← MIT
├── assets/                       ← 模板与设计语言
│   ├── design-tokens.css
│   ├── page-shells/minutes-shell.md
│   └── templates/
│       ├── minutes-md-template.md
│       ├── minutes-docx-spec.md
│       └── question-checklist-template.md
├── references/                   ← 4 个 SOP，按 step 加载
│   ├── 01-extract.md
│   ├── 02-organize.md
│   ├── 03-timestamp.md
│   ├── 04-quality-check.md
│   └── case-studies/case-template.md
└── 访谈纪要模板.docx              ← 原版 docx 模板（归档保留）
```

---

## OPC-Studio 同源 skill

| Skill | 定位 |
|---|---|
| [`investor-skill`](https://github.com/D-kart/investor-skill) | 投资人.skill · 行研 / 尽调 / 投资备忘录 |
| [`presenter-skill`](https://github.com/D-kart/presenter-skill) | 路演者.skill · BP / 路演 / 对外材料 |
| `summary-skill` | **纪要官.skill · 访谈纪要官**（本仓） |
| `yi-er-skill` / `bubu-skill` | 待发布 |

---

## License

[MIT](./LICENSE) © 2026 D-kart (OPC-Studio)
