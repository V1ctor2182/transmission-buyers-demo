# Round 023 · ⬜ Polish · tour 按钮回访脉冲提示

- **时间**:2026-06-25 · 自主模式
- **做了什么**:让回访买家也注意到引导入口 ——
  - 首访(无 sessionStorage)= tour 自动启动(R022 已有)。
  - 回访(已 seen)= `#tour-btn`「Take a tour」按钮 load 后加 `.pulse` 类,`tourpulse` 关键帧脉冲 **3 下(~5s)后自动移除**;点击 startTour 立即清除。非永久动效,避免 AI 味 / 无意义动效红线。
- **验收**:headless 自检 —— tour-btn 存在 ✓ · pulse 加上 ✓ · startTour 清除 pulse ✓ · **UNCAUGHT 0** ✓;按钮在 agent-bar 正常显示。3/3 KEEP。
- **截图**:![pulse test](/tmp 内,已验证;agent-bar Take a tour 按钮可见)
- **落库**:报告 + 台账。自主续 ScheduleWakeup(60)。
