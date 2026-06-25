# Round 071 · 🟦 Standard · 3 个死 Export 按钮 → 有反馈(§4 去死路)· 自主模式

- 时间:2026-06-26 · 档位:🟦 Standard · backlog 来源:续 behavior 审计 —— 扫 Export/Download 按钮
- **审计**:3 个 Export 按钮**无 onclick(点击全无反应=死路)**:① diligence 报告头「↓ Export PDF」(L2418)② bg-check 模态「↓ Export Report」(L2617)③ compare 模态「↓ Export PDF Report」(L2639)。
- **做了什么**:三按钮各加 contextual toast:`showToast('Exporting <X> — Layla is compiling the PDF…')`(diligence/background check/comparison)。demo 不真生成 PDF,但点击有确认反馈(同 decApprove/procApprove 风格),去掉死按钮观感。
- **扫描**:简单文本按钮无 onclick 残留 = **0**(无其它死按钮)。
- **验收**:console 零错 ✓ · 真点击 diligence Export → toast「Exporting due-diligence report…」VIS=1 ✓ · 纯加 onclick、无回归 ✓ · 3/3 KEEP(产品:死按钮→有反馈 §4;视觉:复用 toast;回归:console 零错验证 + 无其它死按钮)。
- **截图**:无(toast 瞬态)。
- **残留 → backlog**:决策卡抽组件;功能性国旗(低优先)。
- commit:见 git(cp index.html + push)
