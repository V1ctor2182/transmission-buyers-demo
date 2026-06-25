# Round 091 · 🟦 Standard · decRemaining 单一真值:KPI delta + agent-bar 随决策同步(状态一致收尾)· 自主模式

- 时间:2026-06-26 · 档位:🟦 Standard · backlog 来源:续 R090 —— 另两处「3 need you」陈旧
- **审计**:① KPI「Advancing for you」delta「3 need you」静态;② agent-bar dashboard 状态「3 items need your decision」(AGENT_STATUS 模板,showView 每次重置回它)—— 清决策后均陈旧。
- **做了什么**:`decRemaining`(初 3)作**单一真值**:
  - `dashAgentStatus()` 据 decRemaining 返回状态;showView 对 dashboard 用它(导航返回也反映已清)。
  - decApprove 设 decRemaining=remaining,并更新 KPI delta(N need you / all clear,色 accent→green)+ agent-bar(dashAgentStatus,含中间态)。
  - 配 R090 greeting + count 徽章 + all-caught-up 横幅。
- **验收**:console 零错(ERR=0)✓ · 批 1→KPI「2 need you」/agent「2 items」、批 3→KPI「all clear」、**导航走返 agent 仍「All decisions cleared」**(decRemaining 持久)✓ · 仅 dashboard · 无回归 ✓ · 3/3 KEEP。
- **★ dashboard 决策清空一致全收尾**:greeting(R90)+ KPI delta + agent-bar + count 徽章 + all-caught-up 横幅(R53)全由 decRemaining 派生。
- **截图**:无(文本同步,title 验证)。
- **残留 → backlog**:决策卡抽组件;功能性国旗(低优先)。
- commit:见 git(cp index.html + push)
