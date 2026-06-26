# Round 106 · ⬜ Polish · 地图高亮路由「货流向 Alexandria」流动动画(游戏感)

- 时间:2026-06-26 · 档位:⬜ Polish(地图交互细节,additive)· backlog 来源:用户「地图游戏感/交互感」(地图是用户重点),procurement 审计无缺口
- **审计**:procurement(My Projects)视图已很完整(项目树+match 分数、KPI、风险分、Layla 推荐 Approve PO 横幅、阶段追踪器、Quote Terms、Export Destinations 条),无真实缺口 → 不强改。转做地图小游戏感。
- **做了什么**:hover/点项目(egHL 高亮某条送货路由)时,该路由的虚线**向 Alexandria 进口枢纽方向流动**(`.eg-route-flow` 给高亮路由的 Leaflet path 加 `egRouteFlow` stroke-dashoffset 动画),呼应「Layla 正在替你把货运到港」。仅高亮的那一条流动,其余静止;`prefers-reduced-motion` 下关闭。
- **验收**:
  - console 零错 ✓
  - headless 自检 ✓:`egHL(2)` → `{r2flow:true, r0flow:false, r2flowCleared:true(egHL(-1)后)}` —— 仅高亮路由获得流动 class、可清除,零抛错
  - 跨视图抽查 ✓:仅地图 egHL,additive
  - 3 critic:产品 KEEP(高亮路由可见货流方向,游戏感,真实方向非假进度)· 视觉 KEEP(仅单条流动,on-brand,reduced-motion 关)· 回归 KEEP(console0,自检对)· **3/3 KEEP**
- **截图**:动态动画,以自检为闸门;地图静态见 `shots/r101-realmap-after.png`。
- **残留 → backlog**:**进入细 polish 阶段** —— 五视图 + 地图 viz/交互/决策点均充分。后续仅边际项(科技感微调 / factorygate 个别件)。用户要求持续 1min,不强推收敛;继续只做诚实低风险真改进,价值走低会如实告知。
- commit:见 git(cp index.html + push)
