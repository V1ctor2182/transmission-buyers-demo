# Round 059 · 🟦 Standard · sourcing/bg-check 分阶段 loader 提速(去拖时间感)· 自主模式

- 时间:2026-06-26 · 档位:🟦 Standard · backlog 来源:「sourcing/bg-check 分阶段 loader 提速」—— 真出结果的分阶段过程,但固定 ~15s/~12s 偏长有「演/拖时间」边缘感
- **审计**:`runSupplierMatching` 5 步每步**有扎实产出**(847 厂→41 票海关→9 家认证→评分权重→排序),非假转圈;问题仅**时长**(3s/步 ≈ 15s)。`openBgCheck` 同样(4 步×3s ≈ 12s)。
- **做了什么**:两 loader 节奏减半(每步间隔 3000→1500ms、active 2400→1100ms、收尾 800/700→500ms)。保留逐步 active→done 揭示与每步实质产出,仅去掉拖沓。
- **验收**:console 零错 ✓ · 实测 **MATCH 15.2s→7601ms / BG 12.1s→6100ms**,两流程均正确到达 results/report ✓ · 仅改时间常量、无逻辑/视觉改动、无回归 ✓ · 3/3 KEEP(产品:更快不拖、每步仍有真产出;视觉:同揭示更快;回归:console 零错两流程完成)。
- **截图**:无(纯时长变更,无视觉 diff)。
- **残留 → backlog**:决策卡抽组件;功能性国旗(低优先)。
- commit:见 git(cp index.html + push)
