# HTML 纪要外壳 · minutes-shell

> 当用户明确要求"输出 HTML 版纪要"或"在浏览器里看"时，按此外壳生成。
> 默认情况下，纪要只产出 Markdown + docx 排版规范，**不主动**生成 HTML。

## 文件骨架

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{公司名}访谈纪要</title>
  <link rel="stylesheet" href="../assets/design-tokens.css">
</head>
<body>
  <div class="opc-page">

    <!-- 1. Letterhead -->
    <div class="opc-header-bar">
      <div class="opc-firm-name">OPC · INTERVIEW MINUTES</div>
      <div class="opc-doc-meta">
        Document No. / 文档编号<br>
        Drafted by / 撰写人
      </div>
    </div>
    <div class="opc-confidential">CONFIDENTIAL · 内部参考 · 严禁外传</div>

    <!-- 2. Title -->
    <div class="opc-title-block">
      <div class="opc-report-type">Interview Minutes · 项目公司访谈纪要</div>
      <div class="opc-report-title">{公司名}访谈纪要</div>
    </div>

    <!-- 3. Meta Bar -->
    <div class="opc-meta-bar">
      <div class="opc-meta-item">
        <div class="opc-meta-label">访谈对象</div>
        <div class="opc-meta-value">{访谈对象，含职位}</div>
      </div>
      <div class="opc-meta-item">
        <div class="opc-meta-label">时间</div>
        <div class="opc-meta-value">{YYYY-MM-DD HH:MM－HH:MM}</div>
      </div>
      <div class="opc-meta-item">
        <div class="opc-meta-label">地点</div>
        <div class="opc-meta-value">{线下/腾讯会议/Zoom}</div>
      </div>
      <div class="opc-meta-item">
        <div class="opc-meta-label">参会人员</div>
        <div class="opc-meta-value">我方：xxx · 对方：xxx</div>
      </div>
    </div>

    <!-- 4. Topics Section -->
    <div class="opc-section">
      <div class="opc-section-title">I · 访谈内容（按时间顺序）</div>

      <div class="opc-topic">
        <div class="opc-topic-title">
          主题：{主题名}
          <span class="opc-timestamp">首次出现 00:00:19</span>
        </div>
        <div class="opc-topic-body">
          <p>{主题内容自然段}</p>
          <p>
            <span class="opc-supplement">后文补充 00:08:00</span>
            {补充内容}
          </p>
          <p>
            <span class="opc-speaker">A总补充：</span>{xxx}
          </p>
          <div class="opc-quote">"{对方原话引用，必要时使用}"</div>
        </div>
      </div>

      <!-- 重复 .opc-topic 块至覆盖全部主题 -->

    </div>

    <!-- 5. Coverage Check -->
    <div class="opc-section">
      <div class="opc-section-title">II · 5 大类 20 小项覆盖度核查</div>
      <table class="opc-coverage-table">
        <thead>
          <tr><th>类别</th><th>考察维度</th><th>覆盖状态</th><th>纪要位置 / 备注</th></tr>
        </thead>
        <tbody>
          <tr>
            <td class="opc-cat">1. 行业</td>
            <td class="opc-dim">主营业务</td>
            <td><span class="opc-status-ok">✓ 已访到</span></td>
            <td>主题：{xxx}</td>
          </tr>
          <!-- ... 20 行 ... -->
          <tr>
            <td class="opc-cat">5. 风险</td>
            <td class="opc-dim">主要风险</td>
            <td><span class="opc-status-missing">✗ 未访到</span></td>
            <td>建议下轮追问</td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- 6. Follow-up Questions -->
    <div class="opc-section">
      <div class="opc-section-title">III · 待确认问题清单</div>
      <div class="opc-followup-box">
        <div class="opc-followup-label">Follow-up Backlog · 下一轮访谈追问</div>
        <ul class="opc-followup-list">
          <li>【行业 · 竞争格局】具体提名 CR3 / CR5 厂商，并说明各自份额。</li>
          <li>【团队 · 股权结构】实控人持股比例、是否存在代持或一致行动安排。</li>
          <li>【财务 · 上市规划】是否已签字中介机构，预计申报时间窗。</li>
        </ul>
      </div>
    </div>

    <!-- 7. Footer -->
    <div class="opc-footer">
      本纪要由 summary-skill v1.0.0 · OPC-Studio 整理 ·
      关键数字 / 客户名称 / 技术路线建议人工复核 ·
      仅供内部决策参考，未经授权严禁外传。
    </div>

  </div>
</body>
</html>
```

## 使用规则

1. **默认不输出 HTML**——除非用户明确要求。Markdown + docx 规范是默认两件套。
2. 若输出 HTML：CSS 引用 `../assets/design-tokens.css`，不内联色值。
3. **时间戳必须使用 `<span class="opc-timestamp">` 包裹**，"时间待核查"加 `.tbd` 修饰类。
4. **覆盖度状态**严格三档：`.opc-status-ok` / `.opc-status-partial` / `.opc-status-missing`。
5. **footer 必须保留**"建议人工复核"字样——这是合规底线。
