# Round 081 · 🟦 Standard · Accept 后决策按钮锁定(per-supplier 持久)· 自主模式

- 时间:2026-06-26 · 档位:🟦 Standard · backlog 来源:续状态一致 —— accept 锁单后 Push/Accept 仍可点(可对已成交单再 push,逻辑矛盾)
- **审计**:negDecide('accept') 锁单(R054 sparkline 绿 + R078 列表 Locked + R080 worklog)但**决策按钮不变** —— 仍能点 Push(对已锁单 push,供应商"反报价"于已成交单)=状态矛盾。且 renderNegDecision 切供应商时重建按钮,简单 disable 不持久。
- **做了什么**:`negLockedSet`(Set)记录已锁供应商;`applyNegLockedUI()` 据 curNeg 是否锁 → Accept 变「✓ Deal locked」disabled、隐藏 Push/Adjust floor(未锁则复原)。negDecide accept 加入 Set + 调用;renderNegDecision 末尾调用(切换时按锁态正确渲染)。
- **验收**:console 零错(ERR=0)✓ · gz accept → acceptDisabled=true/「✓ Deal locked」/push+floor hidden ✓ · 切 XCMG(未锁)→ 按钮复原 ✓ · 切回 gz → 仍锁(Set 持久)✓ · 仅 negotiation · 无回归 ✓ · 3/3 KEEP。
- **★ 状态一致弧收尾**(R078-081):accept → 列表 Locked(78)+ 树 Approved(79,proc)+ worklog 实时(80)+ 决策按钮锁定持久(81)。
- **截图**:无(按钮态,title 验证;锁态可见于 R080 截图上下文)。
- **残留 → backlog**:决策卡抽组件;功能性国旗(低优先)。
- commit:见 git(cp index.html + push)
