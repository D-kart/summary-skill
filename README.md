# 纪要官.skill · summary-skill

> 一名沉稳、专业、滴水不漏的**机构投资访谈纪要专家**。
> 输入一份原始的录音转写，输出一份可以直接传阅、归档、提交投决的正式访谈纪要。

![version](https://img.shields.io/badge/version-2.0.0-blue)
![license](https://img.shields.io/badge/license-MIT-green)
![platforms](https://img.shields.io/badge/platforms-Claude%20%7C%20WorkBuddy%20%7C%20OpenClaw%20%7C%20Hermes%20%7C%20SkillHub-orange)
![spec](https://img.shields.io/badge/spec-agentskills.io%20v1-black)
![made by](https://img.shields.io/badge/made%20by-OPC--Studio-1a1a4e)

---

## 这是什么

`summary-skill` 是一个符合 [agentskills.io](https://agentskills.io) 开放规范的 AI Agent 技能包。安装后，你的 Agent 将具备**机构投资访谈纪要专家**的工作能力——把原始的录音转写文本一键整理成**核心观点清晰、后续事项明确、可对外传阅**的正式访谈纪要。

---

## 它在处理的核心问题

录音转文字得到的转写文本通常带有以下"脏数据特征"：

- 口语化、跳跃、话题来回切
- 多人对话插话、谁说的不清
- 大量口癖（"那个""就是""然后""对吧"）
- 同音错别字（"金鹰"→"金融"）
- 数字单位省略、客户名/产品名拼写不一致
- 寒暄、客套、跑题

本 skill 一次性清掉所有脏数据，按 5 大类 20 维度归并改写成中性陈述句，并把"核心观点 / 后续事项"提到表后独立成段。

---

## 输出形态

按 `assets/templates/访谈纪要输出格式.docx` 的版式产出，结构如下：

1. **标题**：`{公司名}访谈纪要`
2. **元信息四行**：访谈对象、时间、地点、人员
3. **主体表（20 行 × 3 列）**：按"行业 / 团队 / 产品业务 / 财务及融资 / 风险"五大类组织的考察维度表
4. **表后可选段**：核心观点摘要（3–6 条）、后续事项

主交付物：`{公司名}访谈纪要.docx`；同时附 `{公司名}访谈纪要.md` 方便贴飞书 / Notion。

---

## 何时触发

> 访谈纪要 · 调研纪要 · 把对话整理成纪要 · 把录音转成纪要 · 转写整理 · 纪要整理 · 投资经理纪要 · interview minutes · meeting minutes · call notes · transcript to minutes

详见 [`SKILL.md`](./SKILL.md) 第 2 节。

---

## 输出风格

对齐投资机构内部正式纪要的视觉与文字语言：

- 🧭 **深蓝主调 `#1A1A4E`**（与 `investor-skill` 同源色板，跨 skill 拼装一致）
- 📝 **客观陈述**：第三人称、中性、不评价、不站队
- 🔍 **要点形态而非散文**：每格 1–6 条要点，便于快速扫读
- 🧹 **零工具痕迹**：纪要里不出现任何 skill 名称、SOP 步骤号、版本号、内部水印

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
├── SKILL.md                          ← 主文档（必读）
├── README.md                         ← 项目门面（本文件）
├── CHANGELOG.md                      ← 版本记录
├── GLOSSARY.md                       ← 投资 / 访谈术语对照
├── LICENSE                           ← MIT
├── assets/
│   ├── design-tokens.css
│   └── templates/
│       └── 访谈纪要输出格式.docx       ← 目标输出版式
├── scripts/
│   └── build_minutes.py              ← 骨架填空工具（基于模板复制 + 填空）
└── references/
    ├── 01-extract.md                 ← 清洗与抽取
    ├── 02-organize.md                ← 归类与改写
    └── 03-format.md                  ← 按模板组装
```

---

## OPC-Studio 同源 skill

| Skill | 定位 |
|---|---|
| [`investor-skill`](https://github.com/D-kart/investor-skill) | 投资人.skill · 行研 / 尽调 / 投资备忘录 |
| [`ma-pitch-skill`](https://github.com/D-kart/ma-pitch-skill) | M&A 并购标的推介书 AI Skill |
| [`presenter-skill`](https://github.com/D-kart/presenter-skill) | 路演者.skill · BP / 路演 / 对外材料 |
| `summary-skill` | **纪要官.skill · 访谈纪要专家**（本仓） |
| `yi-er-skill` / `bubu-skill` | 待发布 |

---

## License

[MIT](./LICENSE) © 2026 D-kart (OPC-Studio)
