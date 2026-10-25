---
name: paper-pipeline
description: 实证经济学论文全流程辅助。当用户提出写新论文、重新想选题、论文卡在下一步、成稿要检查、准备投稿、收到审稿意见时使用。核心纪律：贡献句先行、占用检索过滤、门控推进（识别不过关不写作）、引用零凭记忆、诚实交付（不 p-hack，结果不理想时报告"诚实的零"）。默认目标期刊 SSCI 2–4 区瀑布，状态档案在 ~/Desktop/SSCI/。另附野心标尺（altitude/depth/range 落地版）：目标级指令、质疑交付物、阶段开工四问、可执行外部裁判、做空者内审、季度能力重探；aer-* 阶段 skill 与 humanizer 为硬依赖（§1）。 | An evidence-disciplined pipeline skill for empirical economics papers: routes each stage (topic selection → literature → identification → data → estimation → writing → journal selection) to the right specialized skill, enforces ten hard-won rules (fetch-before-cite, sample reconciliation, process-not-event treatment timing, randomization inference with few treated clusters, and more), carries an ambition ladder distilled from Rieseberg (2025): outcome-level instructions, question-the-deliverable, stage-kickoff four questions, executable outside judges, short-seller internal review, quarterly capability re-probe; the aer-* stage skills and humanizer are hard dependencies (§1).
---

# Paper Pipeline（实证论文全流程）

> A stage-routed, discipline-enforced pipeline for empirical economics papers — from topic selection to journal submission. Each phase auto-invokes the right specialized skill; ten hard-won rules guard the results.

给写实证经济学论文（政策评估 / staggered DID 为主）的用户做全流程辅助。
本 skill 的第一职责是**路由**：按阶段自动调对下一个 skill，不需要用户提醒。
第二职责是**拦错**：十条纪律来自真实踩坑，违反任何一条时主动叫停。
第三职责是**拔高**：模型能力每几周跳一档，别用去年的用法对今年的模型（§4 野心标尺）。

## 0. 开工第一步（每次必做）

1. 读 `~/Desktop/SSCI/05_论文_投稿追踪.md` 同步所有论文最新状态；
2. 读相关项目记忆（数据通道清单见记忆 `reference-data-access-inventory`）;
3. 需要期刊信息时读 `~/Desktop/SSCI/02`/`03`/`06`，**引用前先读 05 取最新状态**；
4. 阶段开工先答四问（§4.3）：顶尖专家此刻会怎么做 / 最原始素材在哪 / 用什么专业工具 / 外部裁判是谁——答案写进该阶段开工说明，再动手。

## 1. 阶段路由表

> **硬依赖声明（不可协商）**：路由表中的 `aer-*` 阶段 skill（topic-selection / literature / identification / paper-body / introduction / tables-figures / consistency / referee-sim / submission / rebuttal）与 `humanizer` 是本 pipeline 的**强制组件**，不是可选参考。**使用本 skill = 必须使用它们**：进入任一阶段前，先完整读入 `aer-skills/<阶段名>/SKILL.md`（本仓库内，单一维护源）再执行；发现定义缺失时**立即停下向用户报告**，禁止凭记忆即兴替代——保租房论文的调用史已证明这套技能是审计质量的来源，跳过即降级。

| 用户信号 / 阶段 | 调用 | 过门条件（不过不推进） |
|---|---|---|
| "写新论文 / 重新想选题 / 我有个想法" | `aer-topic-selection`（先读 SSCI/05 与禁区清单） | 每题贡献句六格填满（X 造成 Y，用 Z 识别，数据 D，量级 M，改变文献对 Q 的认识）；**英文占用检索**（WebSearch + NBER/SSRN/Dataverse）；收敛菜单 ≤4 题带推荐序；每题标"数据是否在手" |
| 选题已定 | `aer-literature` | antecedents map 3–6 篇（含"它没做什么"中性表述）；**fetch-before-cite：每条引用经 Crossref 核验后才进正文** |
| 设计 | `aer-identification` | 识别假设一句话；staggered DID 用现代估计量（did2s/CS/SA），TWFE 只进对照；诊断清单（先行期/安慰剂/RI）列出 |
| 数据 | 免费通道清单（见记忆 reference-data-access-inventory）+ 下载器骨架 | 报三段样本口径：原始面板 / 窗口内非缺失 / 回归样本，全文沿用 |
| 实证 | pyfixest（**API 先用合成数据验证，再上真数据**） | 先行期（用对来源）+ 安慰剂组 + 量级合理性（均值占比）三关齐过 |
| 写作 | `aer-paper-body` → `aer-introduction` → `humanizer`（两轮） | 图表过 `aer-tables-figures` 规范（图注下置、灰度可读、图内禁自带标题） |
| 成稿 | `aer-consistency` + PDF 编译 + 机械体检脚本 | 引用双向匹配 / 双盲匿名（含源文件注释）/ PDF 0 error 且读完全部 warning |
| 内审 | `aer-referee-sim`（先过做空研究员，§4.5） | verdict ≥ major R&R 且逐条挂可复算检验（§4.4）；报告不软化；修改清单分"必改/建议/扩写/等 R&R"四级给用户勾选 |
| 选刊投稿 | SSCI/06 期刊池 + `aer-submission` | 三套瀑布方案（学术口/冲高/速度）带推荐序给用户拍板；投稿动作当天回写 05 |
| 收到审稿意见 | `aer-rebuttal` | **先改稿、后写信**；逐条独立复算意见里的事实性指控（外部审计方也会出错） |

## 2. 十条纪律（真实事故抽象；详细案例见指针）

1. **fetch-before-cite**。记忆里的 DOI、期刊名、年份默认是错的，直到 Crossref 证明它对。做法：引用表程序化生成，零手打。
2. **数字可溯源**。论文每个数字由当前代码+数据版本生成；跨版本继承前先查 schema 漂移——旧结果文件里出现已删除的变量，就是过期铁证。
3. **样本对账**。子样本分析必报 N 且与主管线对得上；有对照组的设计，对照组必须在每个展示环节出现（事件研究丢对照 = 整节作废）。
4. **处理是过程不是事件**。制度化时点（官宣/挂牌/批复）滞后于真实过程；时点平移敏感性是标配，先行期漂移是信息不是失败——改叙事，不改结果。
5. **推断与设计匹配**。处理组 <20 个 cluster 用随机化推断 RI 为主判据；wild bootstrap 等异常或失败的推断，记录后弃用，不静默保留。
6. **安慰剂分级表述**。干净（精确零）/ 无信息（检验力不足）/ 被污染（回识别阶段修）——措辞必须与证据等级一致，机制重量只压在"干净"的上面。
7. **先验证后真跑**。库调用先过合成数据；环境限制（内存杀、进程池、命令缺失、API 配额）用降规模策略（float32 裁列、月度聚合、手写 FE、双数据源），不硬扛。
8. **交付双轨双全**。投稿 LaTeX 与阅读 DOCX 都过程序化体检：图全嵌入、表为原生表格、公式可见、References 节、双盲连源文件注释都查。编译 0 error ≠ 正确，warning 也要读。
9. **外部审计逐条复核**。欢迎第三方审读，但其结论须独立复算后才能采信——审计方也会出错，认账要认得明明白白，更正也要有凭据。
10. **样本纪律**。处理名单与子样本由来源质量决定，永不由结果 p 值决定；结果变差时先查测量误差方向，不缩样本。

## 3. 用户偏好卡

- 诚信红线：不编造、不 p-hack；结果不理想 = 报告"诚实的零"或停下诊断，不硬写。
- 选题呈现：收敛菜单 ≤4 题、每题带贡献句与"今天能否跑通"标记、给推荐序让用户拍板。
- 执行代理：方向性决策给菜单，执行细节全权代理；用户说"自己跑"即进入全自动模式（后台链 + 看门狗盯完成标记与进度速率 + 完成自唤醒）。
- 修改分级：必改 / 建议 / 扩写 / 等 R&R 四级清单供勾选；深水区（需外部数据的稳健性）主动留到教授/审稿人意见后。
- 交付语言：中文交流、术语标英文；汇报先结论后细节；版本文件夹只增不删。

## 4. 野心标尺（Ambition Ladder）

> 提炼自 Rieseberg《How to Be More Ambitious》(2025)。与十条纪律互补：**纪律防错，野心防平庸**——模型能力每几周跳一档，去年判定的"不可能"今年可能就是一条命令。

1. **目标级指令（altitude）**。指令写给要过的门（"先行期干净、安慰剂齐过、量级说得通"），不写给步骤（"跑这个回归"）。判据：**你本来会为它开组会的事，就高高度交给模型自主推进**；不会开组会的（图注措辞、配色），低高度省 token。
2. **质疑交付物本身**。别急着填事件研究图——先让模型回答："回答这个识别问题，最好的展示物是什么？"更好的预警/呈现设计与旧做法**并行一段时间**、验证后再切换，不一把梭换。
3. **阶段开工四问（stage-kickoff four questions）**。①顶尖专家此刻会怎么做？②最原始素材在哪——直接给原始面板，让模型自己说"数据里发生了什么"，不喂中间产物；③用什么专业工具（pyfixest / RI / 数据库，不是 markdown 表格）？④外部裁判是谁？目标可以定得不可理喻地高，并明说"这可解"（如"原始数据到终稿图表零手工步骤"），让它放手攻。
4. **裁判锚定可执行物（outside judge）**。再叫一个模型来 review **不算独立裁判**——模型间错误相关，可能一起错。裁判只认：合成数据（ground truth 已知）、held-out 样本、可复算脚本、预注册清单。referee-sim 的 verdict 必须逐条挂到可复算的检验上，"感觉不稳"不构成意见。
5. **做空者进组（assemble the crew）**。内审除善意审稿人外，加一个以推翻结论为使命的"做空研究员"：让它**做审稿人做的事**（设计致命稳健性检验、搜反例、算效应上界），不是**写审稿人的话**。机制假设同样处理："我们相信效应来自 X——先用原始数据复现它，再尝试推翻它"；声称的新发现先消融，区分"背出了已知结果"与"真推演出了新结果"。
6. **季度能力重探（self-efficacy）**。上季度判定"做不到 / 不值得自动化"的环节（全自动占用检索、整篇论文复现、跨库清洗）列成清单，每季度初重试一遍，与分区表年度复核同节奏。瓶颈常是"不相信可能"，不是"不可能"。

## 5. 指针（细节只查不复制，保持单一维护源）

- aer-* 与 humanizer 的定义：`aer-skills/`（本仓库内，随 git 持久化；恢复状态见其 README）
- 论文状态与投稿瀑布：`~/Desktop/SSCI/05_论文_投稿追踪.md`（每次投稿动作当天回写）
- 期刊池：`~/Desktop/SSCI/02`（免费 C 档）、`03`（letters）、`06`（环境/交通口）；避雷 `04`
- 数据通道实测：记忆 `reference-data-access-inventory`（QuotSoft / ERA5+POWER / 东财批量 / Wind 事件库 / Crossref）
- 事故档案与代码骨架：`~/Desktop/论文_公交电动化空气质量/docs/WORKFLOW_REVIEW.md` 与 `code/`
- 分区表每年 12 月/3 月更新：提醒用户复核各刊分区与费用

## Handoff

每次阶段推进时按 aer-workflow 惯例输出：

```text
NEXT SKILL: <下一个 skill>
REASON: <一句话>
INPUTS NEEDED: <下一阶段所需工件>
GATE STATUS: <已过 / 未过的门>
```
