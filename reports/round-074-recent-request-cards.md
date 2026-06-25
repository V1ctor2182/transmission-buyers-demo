# Round 074 · 🟦 Standard · Recent Requests 2 死卡 → 深链导航(§4)+ pills 核验 · 自主模式

- 时间:2026-06-26 · 档位:🟦 Standard · backlog 来源:续 behavior 审计 —— 扫 cursor:pointer 无 onclick 的死可点件
- **审计**:① sourcing 表单 pills(`.quick-chip` type/region)→ `toggleQChip`(toggle sel),**交互正常**非死。② sourcing「Recent Requests」3 卡:LED(→srcGoToReport ✓)、**Structural Steel / Hydraulic Excavators 两卡 cursor:pointer 但无 onclick(看着可点却无反应=死路)**。
- **做了什么**:Structural Steel 卡 → `showView('procurement')`(其项目在 My Projects);Hydraulic Excavators 卡 → `goNeg('xcmg')`(挖机在 XCMG 谈判,Quoting 态相符)。点最近请求即到其当前 workspace。
- **验收**:console 零错 ✓ · 真点击:steel→view-procurement / exc→view-negotiation(curNeg=xcmg)/ **sourcing 剩余死卡=0** ✓ · 仅 2 onclick、无回归 ✓ · 3/3 KEEP(产品:死卡→有意义导航 §4;视觉:行为修复;回归:console 零错三态验证)。
- **截图**:无(行为)。
- **残留 → backlog**:决策卡抽组件;功能性国旗(低优先)。
- commit:见 git(cp index.html + push)
