# Changelog · summary-skill

本 skill 遵循 [Semantic Versioning](https://semver.org/lang/zh-CN/) 与 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/) 规范。

---

## [1.0.0] - 2026-06-10

### Added
- 首个公开版本。
- **META 层**：`SKILL.md` · `README.md` · `CHANGELOG.md` · `GLOSSARY.md` · `LICENSE`。
- **ASSETS 层**：
  - `design-tokens.css`（与 investor-skill 同源色板，深蓝 #1A1A4E）
  - `page-shells/minutes-shell.md`（HTML 纪要外壳）
  - `templates/minutes-md-template.md`（Markdown 纪要骨架）
  - `templates/minutes-docx-spec.md`（docx 排版规范，对齐 docx 原版模板）
  - `templates/question-checklist-template.md`（5 大类 20 小项追问骨架）
- **REFERENCES 层**：
  - `01-extract.md`（关键事实抽取 SOP）
  - `02-organize.md`（主题归并 SOP）
  - `03-timestamp.md`（时间戳三档分级 SOP）
  - `04-quality-check.md`（5 大类 20 小项覆盖度核查 + 缺口诊断 SOP）
  - `case-studies/case-template.md`（脱敏案例骨架）
- **原版模板**：`访谈纪要模板.docx`（用户提供的原版规范，作为档案保留）。

### Design Principles
- 遵循 [agentskills.io](https://agentskills.io) 开放规范 v1，frontmatter 覆盖关键触发词。
- 三层架构（META / ASSETS / REFERENCES），按需加载降低 token 成本。
- 工作流 4 步：抽取 → 归并 → 时间戳 → 覆盖核查。
- **核心差异化**：除了纪要本身，必产出"待确认问题清单"，把 5 大类 20 小项里"没访到""部分访到"的维度转化为下一轮访谈的脚手架。
- 兼容性声明：Claude Skills / WorkBuddy / OpenClaw / Hermes / SkillHub 全平台可用。

### Rationale
- 投资经理日常工作中"听录音 → 转写软件 → 文档编辑器 → 维度对账表"切换成本高，本 skill 把后三步整合到一个能力包里，原始转写文本进，纪要 + 缺口诊断出。
- 严格按用户提供的 docx 模板里的 Prompt 实现，不擅自扩展能力边界。

---

## [Unreleased]

### Planned
- 增加 2-3 份脱敏的完整纪要案例（消费 / 硬科技 / 医疗各一份）。
- 支持多语言对话（中英混合 / 粤语口语）的归并规则。
- 提供"批量纪要归档"工作流（多场访谈合并出一份调研合集）。
- 与 `investor-skill` 的接驳点：自动把"待确认问题清单"导出为投资备忘录的"信息缺口"章节。
