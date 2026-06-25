# Round 073 · 🟦 Standard · 模态 Escape + 遮罩点击关闭(标准 UX/可达性)· 自主模式

- 时间:2026-06-26 · 档位:🟦 Standard · backlog 来源:续 behavior 审计 —— 模态键盘/遮罩 UX
- **审计**:bg-check / compare / contact 三模态仅 ✕/Close 按钮可关 —— **无 Escape 关闭、无遮罩点击关闭**(标准模态预期 + 可达性)。map 键盘处理已守卫"模态打开则跳过"(R043),故加模态 Escape 无冲突。
- **做了什么**:① 三 `.modal-overlay` 各加 `onclick="if(event.target===this)this.classList.remove('show')"`(点遮罩背景关,点模态内不关)② 全局 keydown:Escape → 关闭当前打开的 `.modal-overlay.show`。
- **验收**:console 零错 ✓ · 实测:compare Escape→关 ✓ / bg 遮罩点击→关 ✓ / bg 模态**内**点击→**不关**(event.target===this 守卫)✓ · 无 Escape 冲突(map 守卫)· 无回归 ✓ · 3/3 KEEP(产品:标准模态关闭 UX/可达性;视觉:无变;回归:console 零错三态验证)。
- **截图**:无(行为)。
- **残留 → backlog**:决策卡抽组件;功能性国旗(低优先)。
- commit:见 git(cp index.html + push)
