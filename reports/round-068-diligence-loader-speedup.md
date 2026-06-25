# Round 068 · 🟦 Standard · runDueDiligence loader 提速(R059 漏网,最慢)· 自主模式

- 时间:2026-06-26 · 档位:🟦 Standard · backlog 来源:审计 dd-bar 填充逻辑时发现 `runDueDiligence` 仍是 `i*3400` × 6 步 ≈ **~20.3s**(R059 只压了 matching/bg-check,漏了这个最慢的核心流程)
- **审计副产**:核实 dd-bar(`width:0%` + data-w)由 `showDDReport()` 填充(200ms 后 set width=data-w + risk needle),正常流程 runDueDiligence 末步调 showDDReport,**bars 正常填充非 bug**。
- **做了什么**:`runDueDiligence` 节奏减半(步间隔 3400→1500ms、active 2600→1100ms、收尾 700→500ms)。6 步实质产出(注册/海关/财务/制裁/网站/评分)保留,仅去拖沓。
- **验收**:console 零错 ✓ · 实测 **DD 20.3s→9100ms**,报告正常显示 + `FIRST_BAR_W=80%`(showDDReport 跑、bars 动画填充)✓ · 仅时间常量、diligence-only、无回归 ✓ · 3/3 KEEP(产品:核心流程更快不拖;视觉:同 6 步揭示+bar 动画更快;回归:console 零错 bars 填充验证)。
- **截图**:无(纯时长,视觉同)。
- **★ loader 提速全收齐**:matching 7.6s(R059)/ bg-check 6.1s(R059)/ **diligence 9.1s(R068)**。
- **残留 → backlog**:决策卡抽组件;功能性国旗(低优先)。
- commit:见 git(cp index.html + push)
