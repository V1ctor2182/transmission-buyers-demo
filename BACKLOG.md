# BACKLOG — 买方端体验优化

> 每轮按 **影响 × 把握 ÷ 风险** 排序取顶。档:🟥 大件(做完暂停 review)· 🟦 Standard · ⬜ Utility。
> R002 完成逐视图深度审计(5 视图截图 + 动态行为登记 + 操作步数),下方已据实校准优先级。

## 进行中 / 已完成
- [x] ⬜ **真实 logo 接入**(R001)— `.brand-icon` 假「T」→ 白 chip + logo-mark.png + favicon。
- [x] 🟥 **逐视图深度审计**(R002)— 见 `reports/round-002-audit.md` 动态行为登记 + 各视图操作步数。

## 新方向:首页减字 + 可视化 + 科技感(用户 2026-06-25,参考 reference/factorygate)
> 选定路线:**亮色 + 加科技感与可视化(低风险)**,不转深色。逐步迭代 dashboard。
- [x] **KPI 行可视化 + 减字(R028)** — 4 卡加 mini-viz(储蓄上升 sparkline / 4 项目 bar / 24 vetted tick 条 / deadline 倒计时条)+ topline delta + 左侧语义色 rail;greeting 砍长句;dashboard 加克制点阵网格背景(科技感)。
- [x] **Sourcing pipeline 漏斗可视化**(R029) — 新增 24→9→4→2 funnel(In dialogue/Shortlisted/Negotiating/Ready to award,锥形 + chevron + green-win),at-a-glance 替代读数字。注:项目进度区已有进度条+stage dots,够视觉。
- [ ] **继续 dashboard 可视化**(下步):① 总览趋势图(采购额/省钱随时间);② 右栏「Replies Layla is handling」仍偏文字 → 状态可视化/精简;③ 视情况克制科技点缀(hairline/微光/glass)。谨慎勿 slop。

## 新方向(用户 2026-06-25)
- [x] 🟦 **logo 改用矢量 SVG(R025)** — 用户提供的 SVG 源(`transmission-tm-icon.source.svg` / `-full-lockup.source.svg`)尾部有 base64 垃圾导致 XML 解析报错;已截断生成干净 `logo/transmission-tm-icon.svg`(monogram,真矢量 4 path + 1 小高光节点)+ `logo/transmission-full-lockup.svg`。HTML 侧栏 brand chip `<img>` 与 favicon(`image/svg+xml`)改指 tm-icon.svg。原 `logo-mark.png` 不再引用(保留未删)。任意缩放清晰。

## 新方向(用户 2026-06-25 重启 loop)
- [x] 🟥 **买家引导式 tutorial / 点点看(R022)** — 用户:demo 给买家看,买家可能"笨笨的",要能点点快速理解全项目。已建 coachmark 引导:7 步 spotlight(Layla 在场→决策卡→安心感 KPI→Worklog→4 阶段侧栏→谈判代谈→收尾),跨视图切换展示全流程;首次进会话自动启动(sessionStorage)+ agent-bar「Take a tour」可重播;Skip/Back/Next + n/7。零 AI 味、品牌蓝 spotlight。17/17 自检通过。
- [x] ⬜ **tutorial 后续 polish**:[x] 回访脉冲提示(R023);[x] tour 扩到 10 步覆盖全 5 视图(R024:加 Sourcing/Projects/Diligence 步,带「1·2·3·4 阶段」编号,一遍点完即懂全项目)。可选残留(低价值):各视图首进 hint / 移动端定位。

## 已修缺陷
- [x] 🟥 **selectNegSupplier 崩溃 + 谈判 per-supplier 决策面板**(R017)— R013 移除 neg-chips 后 selectNegSupplier 仍引用它 → 切供应商必崩(已修)。新增 `NEG_DEC`(8 供应商让步轨迹/建议/价)+ `renderNegDecision`,切供应商时决策面板(轨迹/建议/按钮价/agent-bar 状态)随之更新;negDecide 改数据驱动。补修 R013 漏掉的 `· Ahmed Al-Rashid`(JS 转义中点 9 处)→ Layla。现仅 sidebar 用户块保留 Ahmed。

## 红线违规(最高优先 — 假进度 / 逼买方劳作)
- [x] 🟦 **[RED] 修 openCompare 假进度条**(R003)— 删 `setInterval` 0→100% 空跑;改为"助理已对比完成"+ 4 个真实对比维度的 <1s 快速 reveal → 报告;去掉 📊 / `🤖 AI Recommendation` emoji(→ "Specialist recommendation:")。
- [x] 🟥 **谈判 negotiation 反转为「助理代谈」(§3-D)**(R013,**已做完,暂停 review**)— 线程「out」气泡全部归 Layla(12 头像 +3 时间戳:`Layla · for you`);移除买方打字输入框,换成**决策面板**:让步轨迹 `$42→$39.50→$38.50 −8.3%` + Layla 有立场建议 + Accept/Push for $37/Adjust floor。`negDecide` 真交互(accept→Layla 发确认+toast+状态「Deal locked」;push→Layla 加码+供应商真回 counter $38.00)。**顺带修 R010 高度回归**:agent-bar 占 57px,3 个全高布局 calc 补偿 + chat-col/chat-msgs min-height:0,negotiation/procurement/sourcing 底部不再被裁。
- [x] 🟦 **寻源 sourcing 长表单 → 助理预填(§4)**(R014)— 重构 framing:「Layla drafted this from your New Cairo Smart City project」chip + 「Review your sourcing brief」+「Requirement · drafted by Layla」+ CTA「Confirm brief & have Layla match suppliers →」。字段本就预填,改为「助理已起草,你确认/微调」。
- [x] 🟦 **尽调 diligence 表单 → 助理主动(§4)**(R014)— 「Layla auto-vets every supplier she shortlists」chip +「Layla already queued XCMG…」+ CTA「Open Layla's intelligence report →」+ 右栏 placeholder「Layla's report is ready… nothing for you to fill in」。从「填表」变「开助理已跑好的报告」。

## 大件(🟥 做完暂停 review)
- [x] 🟥 **助理常驻骨架(§3-A)**(R010,**已做完,暂停 review**)— topbar 下新增全局共享 `.agent-bar`:助理身份(Layla Hassan · Your Procurement Agent + 在线绿点)+ **随视图变化的实时工作状态**(AGENT_STATUS,在 showView 更新,映射各视图真实工作)+ Worklog 按钮(→ toggleRobot 打开「Layla's Worklog」面板)。robot FAB/panel 🤖 去 emoji 并并入助理主题。**待 review 放行后**继续:活动流真实时间戳(§3-B)/ dashboard 三段 / 谈判代谈。
- [x] 🟥 **Dashboard 重构为三段(§3-F,§4)**(R012,**已做完,暂停 review**)— 顶部新增「Needs your decision · 3」决策卡 hero(每卡:tag + saves/deadline + 标题 + 「Layla:」建议 + Approve/次按钮),Approve → 卡片翻成「✓ Approved · Layla 接手」+ 计数递减 + toast(真状态变更非假);KPIs 改「Layla is keeping watch」、项目「In progress · Layla is managing」、供应商「Replies Layla is handling」。被动信息墙 → 看→决策。**决策卡组件雏形已建(§3-F)。**

## Standard(🟦)
- [x] 🟦 **活动流 / Worklog(§3-B)**(R011,用户点名优先)— Layla's Worklog 面板重做为**带时间戳的助理动作时间线**(Today/Yesterday 分组 · mono 时间 · 连接线 · 语义点 blue=需你/green=done · 决策 pill),内容映射真实流程(XCMG/SANY 谈判省 $20K、Guangzhou 报价、尽调清单、寻源匹配 9 家、发 RFQ)。**待深化**:点击 worklog 条目跳到对应上下文 / 真实可累积。
- [x] 🟦 **「Click to reply →」违背零负担(§4)**(R016)— dashboard「Replies Layla is handling」3 处「Click to reply →」→「Layla drafted a reply — review →」,与「她替你起草、你只审」叙事一致。
- [ ] 🟦 **采购 procurement 助理盯单(§3-G)**:订单推进 / 异常由助理监控,买方看进度 + 仅需决策项。(procurement 视图基础不错:已有 matched 理由 + 进度 + quote terms;补"助理在盯 + 需决策项"。)
- [ ] 🟦 **sourcing/bg-check 分阶段 loader 提速 / 真实化**(影响中·把握中·风险低):`runSupplierMatching`(~15s)、`openBgCheck`(~12s)是**真出结果**的分阶段过程(非纯转圈,北极星允许),但偏慢且固定时长有"演"的边缘感。可压缩时长 / 让每段产出更扎实,避免滑向"拖时间假过程"。
- [ ] 🟦 **决策卡组件统一(§3-F)**:散落的「需买方拍板」统一为一致 Decision Card。
- [x] 🟦 **进展 / 安心感汇总(§3-G)**(R020)— dashboard「Layla is keeping watch」KPI 行从被动计数重做为安心感:**Saved for you $843K**(谈判省下,3 deals)· **Advancing for you 4**(3 需你决策)· **Suppliers vetted 24**(全清无红旗)· **Next deadline 12d**(on track)。$843K = compare 三项节省($468K+$24.8K+$350K)真实加总。

## Utility(⬜ 去 AI 味)
- [x] ⬜ **nav emoji 图标**(R004)— 侧栏 🏠🔍📋💬🔎 → inline SVG 线性图标(grid/search/layers/chat/shield-check),`stroke:currentColor` 随 active/hover 变色。
- [~] ⬜ **flag / 装饰 emoji**(R005 部分):已去 `👋`、`🤖 YOUR PROCUREMENT SPECIALIST SUGGESTS`、`🤖 AI Procurement Recommendation`。**残留**:robot FAB `🤖`(L2171)+ robot-panel-title `🤖`(归助理常驻大件一起做)、diligence 标题 `🔧`、org-badge / 各处 flag emoji(🇪🇬🇨🇳…)、`📊` 等。
- [x] ⬜ **供应商卡 emoji「logo」**(R006)— `renderSupplierCards` 的 `.smc-logo` 从 emoji(💡🔆☀️…)改为 `${s.name.charAt(0)}` 首字母,chip 重做成 slate `#475569` + 白 JetBrains Mono(与 supplier=slate 一致)。`logo:` 数据字段保留(已不渲染)。
- [ ] ⬜ **sourcing 右栏 placeholder ✦ sparkle 图标**:`src-right-empty` 的装饰 sparkle 略 AI 味 → 收成更克制或去掉。
- [x] ⬜ **彩色字母 avatar 撞色**(R005)— 25+ 处头像渐变从 amber/green/red/purple/cyan 彩虹撞色统一为**两档**:self(user/chat-buyer/robot FAB)= 品牌蓝 `#1B5EFF,#0EA5E9`;supplier/contact = 中性 slate `#475569,#64748B`(66 处)。
- [x] ⬜ **negotiation/diligence export 条撞色**(R007)— export/destination 条 blue/green/purple/amber/grey → 统一品牌蓝 `var(--accent),var(--accent2)`;改 3 处渲染(negotiation 静态 markup L1781/87/93、diligence dd-bar L1974/78/82/86、JS `selectNegSupplier` exBars L2847)。语义 `.prog-green`/`.prog-amber` + Low-risk 绿框完好未动。
- [x] ⬜ **proj-ph-icon emoji + deadline dots**(R008)— dashboard 项目图标 🏗💡⛏☀️ → slate SVG 线性图标(building/bulb/mountain/sun)+ 统一中性 chip(去 pastel 撞色底);Upcoming Deadlines 🔴🟡🟢 → `currentColor` CSS 圆点(语义色保留)。
- [x] ⬜ **去逐屏 AI 味 emoji**(R009 完成全量)— sourcing(pcb-icon/rec-chip/sr-cluster/sr-callout/✦/📄/📊/src-empty)+ procurement(proj-row-icon/⚡Compare/👆/💬Chat/🔎BgCheck)+ diligence(🔎🔍/✅)+ 模态(🤝/✅/📦)全部 → slate SVG 线性图标 / CSS / 纯文本。**全应用仅剩功能性国旗 + ✓/✕ + 助理 🤖(归大件)。**
- [ ] ⬜ **flag emoji 决策**(org-badge 🇪🇬 / Cairo 🇪🇬 / 供应商/export 各处国旗):贸易语境下国旗偏功能性(原产国),非纯装饰;待定是否全替为文字国名/国家码,或仅去顶栏装饰性两处。低优先。

## 已观察的设计优点(勿推倒)
- 亮色 + 信号蓝方向正确;KPI / 卡片网格对齐良好;JetBrains Mono 金额已用。**不换色相。**
