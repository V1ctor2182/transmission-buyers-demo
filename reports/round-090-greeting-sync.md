# Round 090 · 🟦 Standard · 问候语随决策清空同步(状态一致)· 自主模式

- 时间:2026-06-26 · 档位:🟦 Standard · backlog 来源:审计 decApprove 状态一致 —— 问候语「3 decisions waiting」静态
- **审计**:dashboard 问候副标「**3 decisions** waiting — Layla has handled everything else.」静态。批准决策后 nyd-count 递减、all-caught-up 横幅(R053)显示,但**问候语仍「3 decisions waiting」**=陈旧不一致。
- **做了什么**:`#greeting-sub` 加 id;decApprove 据 remaining 更新:>0 → 「N decision(s) waiting…」(复数正确)、=0 → 「**All caught up** — Layla has everything from here.」(绿)。与 count 徽章 + all-caught-up 横幅同步。
- **验收**:console 零错(ERR=0)✓ · 批 1 张→「2 decisions waiting…」、批 3 张→「All caught up…」✓ · 仅 dashboard · 无回归 ✓ · 3/3 KEEP。
- **截图**:无(文本同步,title 验证)。
- **残留 → backlog**:决策卡抽组件;功能性国旗(低优先)。
- commit:见 git(cp index.html + push)
