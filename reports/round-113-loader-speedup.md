# Round 113 · 🟦 Standard · 分阶段 loader 提速(sourcing matching + bg-check)

- 时间:2026-06-26 · 档位:🟦 Standard(时序常量,低风险)· backlog 来源:BACKLOG「sourcing/bg-check 分阶段 loader 提速」(真出结果但偏慢、固定时长有"演"边缘感)
- **做了什么**:两个 staged loader 用同一模式(步距 `i*1500` + done `1100` + final `500`),统一压缩为 `i*1000` + `850` + `400`:
  - `runSupplierMatching`(5 步)≈7.6s → ≈5.25s
  - `openBgCheck`(4 步)≈6.1s → ≈4.25s
  约快 30%。staged reveal 仍是真过程(每步真实中间结论,行累积成清单、持续可读),只是更 snappy、更少"拖时间"感;**未改任何结果数据**。
- **验收**:
  - console 零错 ✓
  - 自检 runSupplierMatching ✓:≈5.25s 完成 `{matchResults:block, matchLoading:none, cards:9}`
  - 自检 openBgCheck ✓:≈4.25s 完成 `{bgReport:block}`
  - 两 loader 均正常出结果,零抛错
  - 3 critic:产品 KEEP(更快到结果、少"演",仍可信 staged)· 视觉 KEEP(同清单更紧凑)· 回归 KEEP(console0,两 loader 完成、9 卡/报告正常)· **3/3 KEEP**
- **截图**:动态过程,以自检为闸门。
- **残留 → backlog**:openCompare(~1s)/runSrcAnalysis brief(~1.2s)已足够快,不动。极边际项。
- commit:见 git(cp index.html + push)
