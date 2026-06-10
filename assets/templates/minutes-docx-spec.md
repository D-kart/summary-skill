# docx 排版规范 · minutes-docx-spec

> 当用户要求"输出 Word 版纪要 / docx 版纪要"时，Agent 按本规范产出 docx 文件，**字号 / 字体 / 编号 / 缩进必须严格对齐**。
> 此规范对齐用户提供的原版 `访谈纪要模板.docx`。

## 1. 全局样式

| 项 | 值 |
|---|---|
| 页边距 | 上下 2.54cm，左右 3.18cm（Word 默认普通模板） |
| 行距 | 1.5 倍 |
| 中文字体 | 宋体（Songti SC / SimSun） |
| 英文 / 数字字体 | Times New Roman |
| 正文字号 | 小四（12pt） |
| 段落间距 | 段前 0pt，段后 6pt |

## 2. 标题层级

| 层级 | 用途 | 样式 |
|---|---|---|
| 标题 1 | 文档主标题 `XX公司访谈纪要` | 黑体二号（22pt），加粗，居中，段前 12pt 段后 12pt |
| 元信息行 | 访谈对象 / 时间 / 地点 / 人员 | 宋体小四（12pt），左对齐，行距 1.5 |
| 标题 2 | `一、访谈内容` / `二、覆盖度核查` / `三、待确认问题清单` | 黑体三号（16pt），加粗，左对齐，段前 18pt 段后 6pt |
| 标题 3 | `主题：XXX（首次出现 HH:MM:SS）` | 黑体小三（15pt），加粗，深蓝 #1A1A4E，段前 12pt 段后 6pt |
| 加粗子段 | `内容：` | 宋体小四加粗 |

## 3. 段落与列表

- **主题块正文**：宋体小四，行距 1.5，首行缩进 2 字符。
- **要点列表**：使用项目符号 `·` 或 `-`，悬挂缩进 2 字符。
- **后文补充标记**：`（后文补充 HH:MM:SS）` 用 **Times New Roman 五号（10.5pt）灰色 #595959**，紧贴正文行内插入。
- **讲话人归属**：`A总补充：` / `B总另认为：` 用宋体小四加粗黑色，冒号后正文不加粗。
- **时间戳**：所有时间戳（首次出现 / 后文补充 / 时间待核查）用 **Times New Roman**，与中文区分开。

## 4. 覆盖度核查表（必须为 Word 表格，不是文字）

| 列 | 宽度 | 对齐 |
|---|---|---|
| 类别 | 14% | 居中 |
| 考察维度 | 26% | 左对齐 |
| 覆盖状态 | 16% | 居中 |
| 纪要位置 / 备注 | 44% | 左对齐 |

- **表头**：黑体五号（10.5pt），加粗，**深蓝底 #1A1A4E + 白字**。
- **正文**：宋体五号（10.5pt），行高 1.3 倍。
- **斑马纹**：偶数行底色 #FAF9F6（米白）。
- **覆盖状态颜色**：
  - ✓ 已访到 → 深绿 #0A6E2A
  - ◐ 部分访到 → 暗黄 #7A4F00
  - ✗ 未访到 → 暗红 #C00000

## 5. 待确认问题清单（按 5 大类分组）

- 每个分类（行业 / 团队 / 产品业务 / 财务及融资 / 风险）作为 **标题 4**（黑体四号 14pt 加粗）。
- 问题用项目符号 `?` 或 `-` 列出，宋体小四。
- 整体放在 **细边框框（1pt 深蓝）** 内，背景米白 #F5F5FA。

## 6. 页眉 / 页脚

- **页眉**：左侧 `{公司名}访谈纪要` 宋体五号；右侧 `CONFIDENTIAL · 内部参考` 黑体五号深蓝。下方一条 0.75pt 深蓝细线。
- **页脚**：居中页码 `- X -` 宋体五号灰色。

## 7. 末尾复核说明

- 标题 2 `四、纪要复核说明`。
- 正文用项目符号列出（同 Markdown 版）。
- 整段用 **9pt 灰色 #595959 斜体**，区分于主体内容。

## 8. Agent 产出 docx 的两种方式

### 方式 A：Python + python-docx（推荐）

```python
from docx import Document
from docx.shared import Pt, Cm, RGBColor
from docx.enum.text import WD_ALIGN_PARAGRAPH

doc = Document()
# 1. 标题
title = doc.add_heading('{公司名}访谈纪要', level=1)
title.alignment = WD_ALIGN_PARAGRAPH.CENTER

# 2. 元信息
for line in ['访谈对象：xxx', '时间：xxx', '地点：xxx', '人员：xxx']:
    doc.add_paragraph(line)

# 3. 主题块
doc.add_heading('一、访谈内容', level=2)
h = doc.add_heading('主题：xxx（首次出现 00:00:19）', level=3)
# 设置 H3 深蓝色
for run in h.runs:
    run.font.color.rgb = RGBColor(0x1A, 0x1A, 0x4E)

doc.add_paragraph('内容：').runs[0].bold = True
doc.add_paragraph('要点 1', style='List Bullet')
...

# 4. 覆盖度核查表
table = doc.add_table(rows=21, cols=4)
table.style = 'Light Grid Accent 1'
# ... 填充内容

doc.save('{公司名}访谈纪要.docx')
```

### 方式 B：交付排版规范文档让用户手动复制

若 Agent 运行环境无 python-docx，则产出 `{公司名}访谈纪要-Word排版指引.md`，附本规范全文，让用户手动在 Word 里按规范排版。

## 9. 硬性要求

1. **不修改用户原版模板字号字体**——本规范全部对齐 `访谈纪要模板.docx` 原版。
2. **覆盖度核查表必须是 Word 真表格**，不能是文字伪表格。
3. **时间戳全部 Times New Roman**，禁止用中文字体显示数字时间。
4. **页眉 CONFIDENTIAL 字样不可省略**——合规底线。
