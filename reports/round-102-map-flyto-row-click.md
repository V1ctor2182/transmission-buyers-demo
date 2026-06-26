# Round 102 · 🟦 Standard · 地图交互:点项目列表行 → flyTo 该站点 + 开 popup

- 时间:2026-06-26 · 档位:🟦 Standard(dashboard 地图交互,additive)· backlog 来源:用户列出的下一项「**地图点列表行→flyTo**」(承接 R101 真实地图,补足交互/游戏感)
- **做了什么**:在 R101 真实 Leaflet 地图基础上,给 dashboard 项目列表加**点击联动**:点某个项目行(`.proj-progress-header`)→ 地图 `flyTo` 到该项目 marker(zoom 7,0.7s 平滑飞行)+ 自动打开其 popup + 高亮 marker/路由。原有 hover 行↔marker 互亮、accordion 展开(toggleDashProj)均保留(click 监听与 inline onclick 并存,互不冲突)。`prefers-reduced-motion` 下退化为瞬时 `setView`(不飞行)。索引映射沿用 EG_DP2PINIDX(card→pin),与 hover 联动一致。
- **效果**:列表与地图从"hover 高亮"升级为"点击即飞到该站并展开详情",交互感/游戏感明显,且是真实导航(非假动效)。
- **验收**:
  - console 零错 ✓
  - headless 自检 ✓:`egFlyTo(0)` → `{markers:4, flyTarget:[30,31.8], centerNearTarget:true, popupOpen:true, litMarker1:true}` —— 飞到正确 marker(card0→pin1)、地图中心到位、popup 打开、marker 高亮,零抛错
  - 跨视图抽查 ✓:仅 dashboard 地图/列表联动,additive;accordion 仍可展开
  - 3 critic 两轴:
    - **产品(交互/游戏感)**:KEEP —— 点行飞到站点+开详情,列表↔地图强联动,真实导航非假动效。
    - **视觉(高级/零 AI 味)**:KEEP —— 平滑 flyTo,on-brand,reduced-motion 安全。
    - **回归**:KEEP —— console 零错,自检 5/5,不破坏 accordion。
    - 裁决:**3/3 KEEP**。
- **截图**:flyTo 为动态交互,以自检 + console 为闸门(见上);地图静态外观见 `shots/r101-realmap-after.png`。
- **残留 → backlog**:**清理死 CSS**(R101 后 `.eg-svg/.eg-pin/.eg-core/.eg-route/.eg-coast/.eg-hub-mark/.eg-flow`+egPulse/egFlow keyframes + 老 `.eg-tip` div 样式;R099 后 `.pipe-row/.pipe-seg/.pipe-arrow/.pipe-win`)—— 下轮 Utility 清;更多可视化;factorygate 补缺件。
- commit:见 git(cp index.html + push)
