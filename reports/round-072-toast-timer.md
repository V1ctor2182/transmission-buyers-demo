# Round 072 · 🟦 Standard · 全按钮 onclick 核验(0 死) + showToast 连发计时修复 · 自主模式

- 时间:2026-06-26 · 档位:🟦 Standard · backlog 来源:续 behavior 审计
- **审计**:① 全量扫 `<button>`(含嵌套 SVG/span 的)无 onclick = **0**(R070/R071 后全按钮有动作)。② `showToast` 单 toast 元素,每次调用各设一个 2500ms 隐藏 timer —— **连发时早先 toast 的 timer 会提前隐藏后来的 toast**(如一次批准 3 张决策卡 → 3 连 toast,第 1 个的 timer 会在第 3 个还该显示时把它藏掉)。
- **做了什么**:`showToast` 加 `clearTimeout(toastTimer)` —— 每次只保留最新 timer,连发 toast 各得完整 2.5s 显示。
- **验收**:console 零错 ✓ · 连发 A→B(B 在 1.5s)实测:B+1300ms inline opacity=1(旧 bug 会在 B+1000 被 A timer 藏掉)、B+2800ms=0(B 正确在 B+2500 隐藏)✓ · 单行改、无回归 ✓ · 3/3 KEEP(产品:连发 toast 各显完整不被截断;视觉:无变;回归:console 零错验证)。
- **截图**:无(timer 行为)。
- **残留 → backlog**:决策卡抽组件;功能性国旗(低优先)。
- commit:见 git(cp index.html + push)
