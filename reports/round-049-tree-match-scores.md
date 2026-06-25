# Round 049 · 🟦 Standard · Procurement 供应商树 match score 徽章(§3-E)· 自主模式

- 时间:2026-06-26 · 档位:🟦 Standard · backlog 来源:factorygate `tree-sup-score`(我没有)+「多可视化 / 助理排序可见 §3-E」
- **审计**:sourcing 供应商卡已有 score(`smc-score`);**procurement 项目树 `sup-mini-row` 只有名+价,无 score** —— 对比同类供应商看不出 Layla 排序。
- **做了什么**:`decorateTreeScores()` 数据驱动给每个 `.sup-mini-row` 末尾注入 **match score 徽章**:由行 id(`smr-<id>`)查 `SUPPLIERS[id].risk` → mono 数字徽章,语义色(≥85 绿 / ≥78 蓝 / 否则 amber)。`showView('procurement')` 时调用,幂等(已有则跳过)。无逐行 HTML 改动。
- **效果**:钢材类 Ezz 88 / Baosteel 91 / SAIL 74 —— 一眼见 Baosteel 排名最高、SAIL 最低,辅助"选哪家"决策。
- **验收**:console 零错 ✓ · ROWS=19 / SCORED=17(2 个不在 SUPPLIERS 的行优雅跳过,无报错)· EZZ=88 正确 ✓ · 截图确认徽章 + 语义色 ✓ · 幂等、仅 procurement、跨视图无回归 ✓ · 3 critic:
  - **产品**:KEEP —— Layla 评分上树,同类供应商即时排序,助"选择"决策;真实数据。
  - **视觉**:KEEP —— 紧凑 mono 徽章、绿/amber 语义(非彩虹)、右对齐,与既有 score 风格一致,无 emoji。
  - **回归**:KEEP —— console 零错,幂等守卫,2 行无数据优雅跳过,procurement-only。
  - 裁决:**3/3 KEEP**。
- **截图**:![before](shots/r049-tree-before.png) ![after](shots/r049-tree-scores-after.png)
- **残留 → backlog**:2 个树供应商无 SUPPLIERS 数据(可补或忽略);反向 pin→行高亮;决策卡抽组件;flag emoji。**余皆细件。**
- commit:见 git(cp index.html + push)
