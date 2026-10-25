# aer-skills — pipeline 硬依赖技能的定义存放地

本目录是 paper-pipeline 路由表所引用的 `aer-*` 阶段 skill 与 `humanizer` 的**唯一规范存放地**（单一维护源，随 git 持久化到 GitHub）。

**硬依赖规则**（与 SKILL.md §1 声明一致）：使用 paper-pipeline = 必须使用本目录的技能。进入任一阶段前，先完整读入对应 `SKILL.md` 再执行；文件缺失时停下报告用户，禁止凭记忆即兴替代。

## 成员清单（12 个）

| 目录 | 阶段 | 一句话职责 |
|---|---|---|
| `aer-topic-selection/` | 选题 | 贡献句六格 + 英文占用检索 + 收敛菜单 |
| `aer-literature/` | 文献 | antecedents map + fetch-before-cite 引用核验 |
| `aer-identification/` | 识别 | 识别假设一句话 + 现代估计量 + 诊断清单 |
| `aer-paper-body/` | 写作 | 正文段落，图表规范对接 aer-tables-figures |
| `aer-introduction/` | 写作 | 引言（贡献句先行） |
| `aer-tables-figures/` | 图表 | 图注下置、灰度可读、图内禁自带标题 |
| `aer-consistency/` | 成稿 | 七项审计（headline numbers / 样本 N / 单位换算 / 星号与标准误 / 交叉引用 / 引用双向 / 主张-证据映射） |
| `aer-referee-sim/` | 内审 | 模拟审稿 + 做空研究员，verdict ≥ major R&R |
| `aer-submission/` | 选刊 | 三套瀑布方案带推荐序 |
| `aer-rebuttal/` | 返修 | 先改稿后写信，逐条独立复算事实性指控 |
| `aer-workflow/` | 惯例 | Handoff 格式（NEXT SKILL / REASON / INPUTS / GATE STATUS） |
| `humanizer/` | 写作 | 去 AI 痕迹，两轮（本机另有 WorkBuddy 安装副本） |

## 当前状态（2026-10-25 建档）

**定义文件待恢复。** 史实：保租房论文（2026-10 上旬）会话中这套技能被真实调用并产出完整审计记录（如 aer-consistency 七项审计全 PASS 的成稿记录），但当时定义只存在于会话上下文，未落盘到持久目录；ZCode 旧会话日志已被例行清理，WorkBuddy 侧 traces 仍留有调用与审计片段可作底稿。

**恢复底稿来源**：
1. `SKILL.md` §1 路由表各行"过门条件"（每个阶段的验收标准）；
2. `SKILL.md` §2 十条纪律（各阶段的具体禁令）；
3. `~/Desktop/SSCI/07_写作与返修工具箱.md`（写作与返修阶段的工具件）；
4. WorkBuddy traces / projects 日志中的审计文档与调用记录（`~/.workbuddy/traces/`、`~/.workbuddy/projects/Users-abagnale-lyu-WorkBuddy-2026-10-10-*/`）；
5. 住房论文项目 `~/Desktop/论文_保租房租赁市场/` 的 CHECK / REVIEW / 终检报告（aer-consistency、aer-referee-sim 的真实输出样例）。

**恢复约定**：每个子目录一个 `SKILL.md`，frontmatter `name: aer-<stage>`；定义须与 §1 门控和 §2 纪律一致；恢复完成后从本 README 删去"当前状态"节，只留成员清单。
