# Round 069 · ✅ 审计 · 入场体验(splash/login/loader)全核验 + 截图方法学修正 · 自主模式

- 时间:2026-06-26 · 档位:✅ 审计(无代码改动)· backlog 来源:延续 behavior 审计,核验入场流程("开场")
- **审计**:
  - **splash**:`sp.addEventListener('click', finish)` —— Click to skip **真生效**;auto-finish 2300ms + 650ms fade ≈ 3s(合理品牌 intro,可跳过);**logo 从 demo 目录截图渲染正常**(蓝光 TM monogram 清晰可见)。
  - **login**:R058 白 chip logo **从 demo 目录确认渲染真实 logo**(非破图);「Sign in →」/「Continue as demo user」/ 邮箱密码 Enter 键 **全部 → doLogin() → afterIntro()(app+tour)**,功能完整。
  - **loaders**:matching 7.6s / bg 6.1s / diligence 9.1s / src brief 1.2s / compare <1s —— 全部已合理提速(R059/R068)。
- **结论**:入场体验稳健,无需改动。
- **★ 方法学修正(重要)**:`/tmp/*.html` 测试副本无法解析相对 `logo/` 路径 → 过往 /tmp 截图中 logo 区域可能显示破图(测试假象,**非 demo bug**;真站点/demo 目录解析正常)。**今后含 logo 的 UI 一律从 demo 目录截图**(`file://$PWD/__tmp.html` 并随后删除),已用此法复核 splash+login 均 OK。
- **验收**:逐项肉眼核验通过 · 纯审计无改动 · 3/3 KEEP(入场稳健性确认 + 方法学修正)。
- **截图**:splash/login 从 demo 目录确认(临时文件已删,不入库)。
- **残留 → backlog**:决策卡抽组件;功能性国旗(低优先)。
- commit:仅 reports(无 HTML 改动)
