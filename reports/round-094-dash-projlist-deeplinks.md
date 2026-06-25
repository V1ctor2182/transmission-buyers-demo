# Round 094 · 🟦 Standard · Dashboard 项目列表「Chat →」深链到对应供应商线程 · 自主模式

- 时间:2026-06-26 · 档位:🟦 Standard · backlog 来源:审计 dashboard「In progress · Layla is managing」项目列表
- **审计**:`#dash-proj-list` 各供应商行的「Chat →」按钮(dp1-dp4 共 ~11 个)全部 `onclick="showView('negotiation')"` —— 泛跳,落默认线程(gz),**点 Ezz/Suez/XCMG… 都到错的供应商**。同 R063/R064/R074/R085 已修的深链错配类(回复卡/决策卡/死卡/proc Chat 均已 goNeg),唯独 dashboard 项目列表漏网。
- **做了什么**:6 个在 NEG_DATA 内的供应商按钮改 `goNeg('<id>')`:Ezz Steel→ezz、Suez Cement→suez、Guangzhou Lumens→gz、Egyptian Electrical→eei、XCMG→xcmg、Caterpillar→caterpillar。不在 NEG_DATA 的(Baosteel/Huawei/Sandvik/Benban 系)保留泛跳 `showView('negotiation')`(优雅回退,无错配)。name-anchored 定位逐个替换(scope 限 dash-proj-list)。
- **效果**:dashboard 直接点某供应商「Chat →」即落**它自己的**谈判线程(决策面板/agent-bar 随之)—— 深链一致性延伸到 dashboard 项目列表,§4 无错配收口。
- **验收**:console 零错(ERR=0)✓ · 6/6 深链 active 列表项 onclick 含对应 id(ezz/suez/gz/eei/xcmg/caterpillar 全 OK)✓ · view=view-negotiation ✓ · 非 NEG_DATA 5 个保留泛跳无回归 ✓ · 3/3 KEEP。
- **截图**:无(导航深链,active 列表项 + title 验证)。
- **残留 → backlog**:决策卡抽组件;功能性国旗(低优先)。
- commit:见 git(cp index.html + push)
