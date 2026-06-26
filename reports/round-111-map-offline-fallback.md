# Round 111 · ⬜ Polish · 地图离线优雅降级(无网时不再空白暗框)

- 时间:2026-06-26 · 档位:⬜ Polish(健壮性,低风险)· backlog 来源:R101 真实地图依赖网络(LOOP-STATE 注:离线 file:// 无瓦片)—— 此前 initEgMap 在 `!window.L` 时直接 return,留一个空白暗框
- **做了什么**:initEgMap 增加优雅降级 —— 若 `window.L` 未加载(CDN 不可达/离线),在 `#eg-leaflet` 居中显示克制提示「Interactive map loads when online」(`.eg-offline`),而非空白暗框;`window.L` 存在时先 `el.innerHTML=''` 清掉任何提示再交给 Leaflet。线上 Pages 有网,行为不变。
- **验收**:
  - console 零错(两路径)✓
  - 自检 A(在线,含 Leaflet):`{egMap:true, markers:4, offlineNote:false}` —— 地图正常初始化、提示已清 ✓
  - 自检 B(离线,剥离 Leaflet):`{egMap:false, markers:0, offlineNote:true}` —— 显示降级提示、零抛错 ✓
  - 3 critic:产品 KEEP(离线优雅降级,线上无损)· 视觉 KEEP(在线不变,离线克制提示替空白)· 回归 KEEP(两路径 console0,在线正常初始化)· **3/3 KEEP**
- **截图**:在线无变化;离线为一行克制提示(自检为闸门)。
- **残留 → backlog**:极边际项;continue 诚实低风险或如实告知无高价值。
- commit:见 git(cp index.html + push)
