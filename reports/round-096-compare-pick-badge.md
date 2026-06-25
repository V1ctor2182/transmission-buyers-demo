# Round 096 · 🟦 Standard · Compare 推荐供应商 ★ glyph → 「Layla's pick」徽章(去 AI 味)· 自主模式

- 时间:2026-06-26 · 档位:🟦 Standard · backlog 来源:全文 emoji codepoint 扫描
- **审计**:全量 emoji 扫描(非国旗)发现:① `MATCH_SUPPLIERS` 的 `logo:` 字段残留 9 个 emoji(💡🔆☀💫📡⚡🌟💎🏆)—— **R006 起已不渲染**(`.smc-logo` 用 `name.charAt(0)`),死数据,不可见,留置;② **CMP_DATA 三个推荐供应商名字尾部嵌 `★`**(Baosteel ★ / Guangzhou Lumens ★ / XCMG International ★)—— **在 Compare 模态真渲染**(score-bar + 表头),裸 ★ glyph 塞进名字 = 装饰 AI 味(北极星-1 忌)。
- **做了什么**:三处 `name:'… ★'` → 去 ★ + 加 `pick:true` 数据位;`showCmpReport` 表头 winner 列在名字下渲染克制「Layla's pick」蓝徽章(单一 accent 色 + accent-light 底,无 emoji,同 R055 sourcing top-pick 语汇)。先试塞 score-bar-label 但其窄宽截断(名字本就 ellipsis)→ 移到表头列(宽、可见、与 winner-col 蓝高亮同列,语义吻合:pick 恒为最高分列)。
- **效果**:对比表「谁是 Layla 首推」由 emoji glyph 升级为高端 B2B 徽章 —— 去 AI 味同时**强化首推一眼可见**(§3-E),截图确认 Guangzhou Lumens 列下蓝 pill 干净不挤。
- **验收**:console 零错(ERR=0)✓ · 三项目 compare 输出无 ★(star=N×3)✓ · hasPick=true(1.5s 揭示后)+ 截图徽章渲染干净 ✓ · 纯数据+render 无回归 ✓ · 3/3 KEEP。
- **截图**:Compare(lighting)表头 Guangzhou Lumens 下「Layla's pick」蓝徽章。
- **残留 → backlog**:`logo:` 死 emoji 字段(不渲染,低价值,可后续清);决策卡抽组件;功能性国旗(低优先)。
- commit:见 git(cp index.html + push)
