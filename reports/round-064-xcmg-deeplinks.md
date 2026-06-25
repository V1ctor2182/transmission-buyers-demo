# Round 064 · 🟦 Standard · XCMG 专属动作深链一致(View thread / Proceed)· 自主模式

- 时间:2026-06-26 · 档位:🟦 Standard · backlog 来源:R063 续 —— 全量扫 `showView('negotiation')` 找 supplier 错配
- **审计**:14 处 `showView('negotiation')`。其中两处明确属 XCMG 却泛跳落默认 gz:① dashboard XCMG 决策卡「View thread」(L802)② diligence(XCMG 报告)verdict「Proceed to negotiation →」(L2401)。其余:nav 项(泛对)/「Chat →」项目行(供应商多非 neg 列表成员、id 不映射,留泛跳)/ procurement briefing「Chat」(d.id 与 neg id 不 1:1,留泛跳)。
- **做了什么**:两处 XCMG 专属动作 → `goNeg('xcmg')`(R063 的 helper,xcmg 在 neg 列表)。点 XCMG 决策卡查看线程 / 尽调后转谈判,均落 XCMG 线程。
- **诚实/稳健**:`goNeg` 无匹配时仅 showView(不调 selectNegSupplier),故对任意 id 安全;此处 xcmg 必匹配。
- **验收**:console 零错 ✓ · 真点击验证:`viewthread→curNeg=xcmg | proceed→curNeg=xcmg` ✓ · 仅改 2 onclick、无其它路径影响、无回归 ✓ · 3/3 KEEP(产品:XCMG 动作落 XCMG 线程 §4;视觉:行为修复;回归:console 零错真点击验证)。
- **截图**:无(行为修复,XCMG 线程视觉同 R063 shots/r063-reply-deeplink-xcmg.png)。
- **残留 → backlog**:「Chat →」项目行 / procurement Chat 需 procurement→neg id 映射表才能深链(中低价值);决策卡抽组件。
- commit:见 git(cp index.html + push)
