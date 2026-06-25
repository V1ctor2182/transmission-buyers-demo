# Round 088 · 🟦 Standard · Sourcing pipeline 漏斗各段可点导航(交互感)· 自主模式

- 时间:2026-06-26 · 档位:🟦 Standard · backlog 来源:审计 dashboard 漏斗 —— pipe-seg 静态(无 onclick/pointer),用户要「交互感」
- **做了什么**:dashboard「Sourcing pipeline」漏斗 4 段加 onclick 导航到对应工作流视图 + cursor:pointer + hover 抬升(translateY+shadow)+ title 提示:
  - In dialogue(24)/ Shortlisted(9)→ sourcing
  - Negotiating(4)→ negotiation
  - Ready to award(2)→ procurement
- **效果**:漏斗从静态 viz 变**可点导航**(看到「4 Negotiating」点击即进谈判),加交互感 + 实用钻取。
- **验收**:console 零错(ERR=0)✓ · In dialogue→sourcing / Negotiating→negotiation / Ready to award→procurement 全对 · 仅 dashboard · 无回归 ✓ · 3/3 KEEP(产品:静态 viz→导航交互;视觉:hover 抬升 pointer 克制;回归:console 零错四段验证)。
- **截图**:无(hover/导航行为)。
- **残留 → backlog**:决策卡抽组件;功能性国旗(低优先)。
- commit:见 git(cp index.html + push)
