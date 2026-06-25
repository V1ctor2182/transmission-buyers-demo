# loop-prompt — 直接复制下面整段,粘进对话发送即可启动买方端体验优化 loop

> 权威流程在 `demo/loop-procedure.md`。这段 prompt 只是入口,loop 每轮会去读那个文件闭环。
> 第一轮先做一次**全量审计**(逐视图截图 + 登记每个动态行为 + 数清每屏买方操作步数),把视觉 / 产品问题写满 BACKLOG;**助理常驻骨架**这类大件做完**截图暂停等你定调**,不自动铺开。

---

/loop 1min 持续优化买方端 demo `demo/transmission_v5 (1).html`(单文件 HTML,5 视图:dashboard / sourcing / procurement / negotiation / diligence)的体验。**每轮严格按 `demo/loop-procedure.md` 执行**(它是本次权威流程;`../loop-procedure.md`、`../loop-prompt.md` 是卖方端,只作写法参照,产品方向相反,别照搬其北极星)。流程:读 `demo/loop-procedure.md` + LOOP-STATE.md + BACKLOG.md(首轮无则创建)→ 审计 → 按 backlog 影响×把握÷风险 排序取顶。

/loop 1min 持续优化买方端 demo `demo/transmission_v5 (1).html`(单文件 HTML,5 视图:dashboard / sourcing / procurement / negotiation / diligence)的体验。**每轮严格按 `demo/loop-procedure.md` 执行**(它是本次权威流程;`../loop-procedure.md`、`../loop-prompt.md` 是卖方端,只作写法参照,产品方向相反,别照搬其北极星)。流程:读 `demo/loop-procedure.md` + LOOP-STATE.md + BACKLOG.md(首轮无则创建)→ 审计 → 按 backlog 影响×把握÷风险 排序取顶。参考这个 /Users/victor/work/创拾觅深-买方/demo/reference/factorygate (1).html来加一下我现在没有的一些component，还有开场+有更多一些有科技感的东西+首页文字排的太多了 页面排布都是纯文字，信息密度太高，一登录进来就是信息过载+多一些可视化+地图就是要有一种交互感 甚至说有一点点游戏感

**两条北极星(高于一切,每轮都按这判,持续朝它走)**:① **视觉 = 零 AI 味 + 高级感**(高端克制有质感的企业级 B2B,像金融/采购终端、Linear、Stripe;敢进给大客户的预售方案)。② **产品(买方视角)= 「我几乎什么都不用做,只看与决策」+ 强烈的「真人采购助理在替我实时干活」的人感**。具体:**(a) 几乎零负担** —— 搜索/比价/填表/核验/来回沟通都由助理替买方干完,界面只端来"做好的综合结论 + 明确建议",买方主要动作是"审阅→批准/否决/选择/设底线"这类一眼能定的决策;看到逼买方劳作(长表单/手动比价/自己整理)就记进 backlog 改掉。**(b) 强人感** —— 助理是个常驻在场的"人"(名字/身份/当前在做什么的实时状态)、工作有过程有阶段产出(不是瞬间吐全量)、带时间戳的真实动作流(像看真人助理工作日志)、谈判看得见助理代你来回博弈的让步轨迹与战报、给的是有立场的判断而非参数堆。**(c) 安心有进展** —— 替你省了多少/谈下多少/挡掉多少风险,可见可累积。

⚠️ **人感与进展必须真实挣来(买方端最大红线)**:严禁假装在思考的**空转 spinner / 假进度条 / 凭空跳动的计数**(既欺骗又 AI 味,一票否决);助理的每个动作和产出都要对应界面上**真实、前后一致**的状态推进。拟人化靠**专业语气 + 真实工作流 + 时间戳**,不靠 emoji / 卖萌 / 彩色头像。审计时除视觉外,也把"买方被迫劳作 / 助理不在场 / 瞬间出结果没过程 / 空转假进度 / 死路做完没下一步 / 空仪表盘 / 看不懂的数字"写回 BACKLOG。

**推进顺序**:① 首轮 = **全量审计**(逐视图截图 + 登记内联 `<script>` 每个动态行为是真推进还是假转圈 + 数每屏买方操作步数),写满 BACKLOG。② **人感骨架优先**(助理常驻身份+实时状态 = 大件,做完暂停等 review;活动流/Worklog;Dashboard 重构为「助理已完成 / 正在做 / 需你决策」三段)。③ 再逐视图:寻源加可信的逐家核验过程 + 推荐(查 `src-stage-*`/`sup-prog-row` 是否假转圈)、谈判看得见博弈、采购助理盯单、尽调出结论+红旗。④ 逐屏去 AI 味 + 决策卡统一 + 进展汇总。⑤ **真实 logo 接入(用户点名,优先)**:把 HTML 里假 logo(`.brand-icon` 蓝渐变方块+字母「T」,`<style>` L26 / 侧栏 L492,以及任何蓝块代 logo 处)换成 `demo/logo/` 的真实透明 PNG(`logo-mark.png` 监 monogram / `logo-full.png` 全锁版)`<img object-fit:contain>`,去掉方块底;别再 CSS 复刻 TM;暗侧栏对比不足时把 monogram 放进小白色圆角 chip。favicon 顺手指 logo-mark.png。(供应商卡里的 emoji logo 是产品图标占位,归去 AI 味处理,别混。)

**设计基调(沿用,勿换色相)**:亮色 + 信号蓝已就位 —— `--accent:#1B5EFF` 主强调 · `--bg:#F8FAFC` 浅底 · `--bg2:#FFFFFF` 白卡 · `--sidebar:#0F172A` navy 侧栏 · `--text1/2/3` 三级文字 · Inter 正文 + JetBrains Mono(金额/数字/计数 tabular 成列)。单一强调色锁:蓝是唯一品牌色,绿/红/amber/purple 仅作语义不当装饰撞色;渐变/glow 克制。优化重心是**秩序 / 层级 / 人感 / 决策流**,不是改配色。

**每轮闸门(单 HTML,无构建)**:浏览器打开截 before(优先 crop 改动区域+留一张全屏)→ 改 → 刷新截 after → **console 零报错** + 改动的动态行为实点一遍跑通 + 跨视图抽查没改坏 + 3 critic 判两轴【买方零负担 + 真人感(且真实挣来,无假转圈/假进度)】【高级感/零 AI 味/对比度】≥2/3 KEEP 过;纯静图难判时以 console 零错+逻辑自检+北极星自检为闸门并注明。过 → commit +(配了远端则 push)+(非大件)ScheduleWakeup(600)。

**写报告**:截图拷 `reports/shots/r<NNN>-*.png`,写 `reports/round-<NNN>-*.md`,更新 `reports/INDEX.md` + `LOOP-STATE.md`,git commit。

**红线**:只动 `demo/transmission_v5 (1).html`(及本目录 loop 自己的 reports/文档);不碰 `../` 卖方端与 `LOGO矢量.*` 源(只读参考);不换色相;人感真实挣来、不许空转/假进度/假%;不用 emoji/撞色/渐变glow 把 AI slop 请回来;买方零负担优先;console 永远零报错,过闸门才落库。
