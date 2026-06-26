# Round 110 · ⬜ Polish · Leaflet 脚本改 defer(开场首屏不被阻塞,性能)

- 时间:2026-06-26 · 档位:⬜ Polish(性能,低风险)· backlog 来源:R101 引入 Leaflet 时 `<script>` 放 `<head>` 无 defer = 渲染阻塞
- **问题**:Leaflet JS(~150KB)在 `<head>` 同步加载 → 阻塞首屏(splash)渲染,直到脚本 fetch+parse 完。
- **做了什么**:给 Leaflet `<script>` 加 `defer`。`initEgMap()` 只在 `load` 与 `showView('dashboard')` 时调用(均晚于 defer 执行时机),`window.L` 届时已就绪;body 内联脚本解析期不引用 L → defer 安全。splash/首屏不再等 Leaflet,opening 更快(呼应用户「开场」诉求)。
- **验收**:
  - console 零错 ✓
  - headless 自检 ✓:`{L:true, egMap:true, markers:4, tiles:12}` —— defer 后地图仍正常初始化、瓦片加载,零抛错
  - 无视觉变化(纯加载时序)
  - 3 critic:产品 KEEP(开场首屏更快,地图无损)· 视觉 KEEP(无变化)· 回归 KEEP(console0,自检全过,defer 安全)· **3/3 KEEP**
- **截图**:无视觉变化(性能轮,自检为闸门)。
- **残留 → backlog**:极边际项;continue 诚实低风险或如实告知无高价值。
- commit:见 git(cp index.html + push)
