# Changelog · summary-skill

本 skill 遵循 [Semantic Versioning](https://semver.org/lang/zh-CN/) 与 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/) 规范。

---

## [2.0.2] - 2026-06-12

### Changed
- README 「OPC-Studio 同源 skill」表格新增 [`ma-pitch-skill`](https://github.com/D-kart/ma-pitch-skill)（M&A 并购标的推介书 AI Skill）。

---

## [2.0.1] - 2026-06-12

### Fixed
- `scripts/build_minutes.py` 填充表格单元格时统一应用 楷体 五号（10.5pt），与模板其余列字体一致；此前仅依赖样式继承导致中文字体偏离。

---

## [2.0.0] - 2026-06-10

### Changed (重大)
- **输出形态对齐新版"访谈纪要输出格式.docx"**：以"20 行 × 3 列"考察维度表为主体（大类 / 维度 / 内容），不再单独产出"覆盖度核查表 / 待确认问题清单"作为外发文件——需要追问的内容直接写在表格对应单元格里。
- **去除所有内部工具痕迹**：纪要正文不再出现 `summary-skill` / `OPC-Studio` / `按 SOP` / `时间待核查` / `复核说明` / `CONFIDENTIAL` 等内部黑话。
- **时间戳硬性 SOP 降级**：不再强制为每个主题块标注"首次出现 / 后文补充 / 时间待核查"三档；原文有时间戳就保留作为附注，没有就完全不出现时间戳。
- **核心目标重新聚焦**：从"按时间归并 + 缺口对账"调整为"清洗口语转写 + 提炼核心观点 + 明确后续事项"。
- **工作流简化**：从 4 步合并为 3 步（清洗与抽取 → 归类与改写 → 按模板组装）。

### Added
- `references/03-format.md`：按目标模板组装 docx + md 的细则与示例代码。
- 主体表后可选两段：**核心观点摘要**（3–6 条）与**后续事项**（含责任方/时点）。
- 单元格风格示例（好 vs 差对照）与"严禁出现的文字"最终核查清单。

### Removed
- `references/03-timestamp.md`、`references/04-quality-check.md`：被新流程涵盖，不再单独维护。
- `assets/templates/minutes-md-template.md`、`assets/templates/minutes-docx-spec.md`、`assets/templates/question-checklist-template.md`：旧模板，被 `访谈纪要输出格式.docx` 取代。
- `assets/page-shells/minutes-shell.md`、`references/case-studies/`：未使用，下线。
- `访谈纪要模板.docx`（旧版样张）：替换为 `assets/templates/访谈纪要输出格式.docx`。

---

## [1.0.0] - 2026-06-10

### Added
- 首个公开版本。三层架构（META / ASSETS / REFERENCES）。
- 工作流 4 步：抽取 → 归并 → 时间戳 → 覆盖核查。
- 产出：Markdown 纪要 + docx 排版规范 + 5 大类 20 小项追问清单"三件套"。
- 兼容性声明：Claude Skills / WorkBuddy / OpenClaw / Hermes / SkillHub。

---

## [Unreleased]

### Planned
- 增加 2–3 份脱敏的完整纪要案例（消费 / 硬科技 / 医疗各一份）。
- 支持多语言对话（中英混合 / 粤语口语）的归并规则。
- 提供"批量纪要归档"工作流（多场访谈合并出一份调研合集）。
- 与 `investor-skill` 的接驳点：自动把单元格内"未涉及，建议下轮补充"导出为投资备忘录的"信息缺口"章节。
