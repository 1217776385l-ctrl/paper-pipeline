# Paper Pipeline

> A stage-routed, discipline-enforced pipeline skill for empirical economics papers — from topic selection to journal submission.
> 实证经济学论文全流程辅助 skill：阶段自动路由 + 十条实战纪律 + 野心标尺（Ambition Ladder）。
> Plus an ambition ladder distilled from Felix Rieseberg's *How to Be More Ambitious* (2025): outcome-level instructions, question-the-deliverable, stage-kickoff four questions, executable outside judges, short-seller internal review, quarterly capability re-probe.

## What it does / 它做什么

This skill makes an AI coding agent run the full lifecycle of an empirical paper **without the user having to say which step comes next**. It was distilled from a complete real-world run — topic selection, staggered-DID identification, 1.4M-row panel construction, full drafting, adversarial internal review, an external audit that caught two critical bugs, and journal selection — compressed into a routing table, ten general rules, and an ambition ladder.

这个 skill 让 AI 编程代理自动跑通实证论文的全生命周期，用户无需逐步指挥。它提炼自一次完整的实战：选题 → staggered DID 识别 → 139 万行面板构建 → 全文写作 → 对抗式内审 → 外部审计（揪出两个致命错误）→ 选刊尽调，最终压缩为一张路由表、十条一般性纪律，外加一节野心标尺。

## The routing table / 路由表

| Signal 阶段信号 | Auto-invokes 自动调用 | Gate 过门条件 |
|---|---|---|
| New paper / topic idea 立项与选题 | topic-selection | Contribution sentence (6 blanks) + English occupancy search + ≤4 candidates |
| Topic fixed 选题已定 | literature | Antecedents map 3–6 papers + fetch-before-cite citations |
| Design 设计 | identification | One-sentence identifying assumption + modern staggered-DID estimators |
| Data 数据 | data-channel playbook | Three-tier sample counts reported and kept consistent |
| Estimation 实证 | pyfixest (API pre-validated on synthetic data) | Pre-trends + placebo battery + magnitude sanity |
| Writing 写作 | paper-body → introduction → humanizer | AER-style exhibits (notes: method/CI/sample/N) |
| Assembled 成稿 | consistency + compile + mechanical audit | Citation two-way match / dual-blind anonymity / PDF 0 errors |
| Internal review 内审 | referee-sim | Verdict ≥ major R&R |
| Journal selection 选刊 | journal knowledge base + submission | Three waterfall options with recommendation |
| Reviewer comments 审稿意见 | rebuttal | Revise manuscript first, letter second |

## The ten rules / 十条纪律（真实事故抽象）

1. **Fetch-before-cite** — every DOI, journal, year from memory is wrong until Crossref proves it right.
2. **Traceable numbers** — every figure in the paper traces to artifacts from the current code+data version; check schema drift before inheriting across versions.
3. **Sample reconciliation** — every subsample reports N and reconciles with the master pipeline; a design with a control group must show it in every exhibit.
4. **Treatment is a process, not an event** — institutional milestones lag reality; timing-shift sensitivity is standard, and pre-trend drift is information, not failure.
5. **Inference matched to design** — few treated clusters → randomization inference primary; inference methods that fail or misbehave are documented and dropped, never silently kept.
6. **Grade your placebos** — clean / uninformative / contaminated; the language must match the evidence, and mechanism weight rests only on clean ones.
7. **Validate before real data** — library calls proven on synthetic data first; environment limits (memory kills, process pools, missing commands, API quotas) answered with down-scaling, not brute force.
8. **Dual-track, fully checked deliverables** — submission LaTeX and reading DOCX both pass programmatic audits; compile with 0 errors ≠ correct, read the warnings.
9. **Audit auditors** — welcome third-party review, but independently re-compute every claim before accepting it; auditors err too.
10. **Samples follow source quality, never results** — treatment lists are never grown or shrunk to move a p-value; versioned folders, append-only.

## The ambition ladder / 野心标尺（防"用得太平庸"）

The ten rules guard against errors; the ladder guards against under-using the model. 十条纪律防错，野心标尺防平庸：模型能力每几周跳一档，去年判定的"不可能"今年可能就是一条命令。

1. **Outcome-level instructions (altitude)** — instruct by the gate to pass ("clean pre-trends, placebo battery passing"), not the steps to run ("run this regression"). If you'd call a group meeting about it, delegate it at high altitude.
2. **Question the deliverable** — before filling in the event-study plot, ask what exhibit best answers the identification question; run a better warning/presentation design in parallel before switching.
3. **Stage-kickoff four questions** — what would a leading expert do now / where is the rawest material (feed the raw panel, let the model say what happened in it) / which professional instruments (pyfixest, RI, databases — not markdown tables) / who is the outside judge. Set unreasonably high goals and assert they are solvable.
4. **Executable outside judges** — a second model reviewing the first is not an independent judge (errors correlate). Judges must be executable: synthetic data with known ground truth, held-out samples, re-computable scripts, pre-registered checklists. Referee-sim verdicts must attach to re-computable checks.
5. **Short seller in the crew** — besides a friendly simulated referee, run an adversarial reviewer whose mission is to refute the result: have it *do what* a referee does (design the killing robustness check, hunt counterexamples), not *write like* one. Mechanism claims: reproduce from raw data first, then try to break them; ablate "new findings" to tell recall of known results from genuine derivation.
6. **Quarterly capability re-probe** — keep a list of steps previously judged infeasible / not worth automating, and retry it at the start of each quarter. Capability expiry is faster than code expiry; the bottleneck is often disbelief, not impossibility.

## Install / 安装

Copy the folder into your agent's skills directory (for ZCode: `~/.zcode/skills/paper-pipeline/`), or point the agent at this repository. The skill references a personal journal knowledge base (`~/Desktop/SSCI/`) — see SKILL.md §0 and §5; replace the pointers with your own or remove them.

将文件夹复制到代理的技能目录即可。skill 引用了个人投稿知识库（路径见 SKILL.md），可替换为自有路径或删除相关指针。

## Files / 文件

```
SKILL.md        the skill (routing table, ten rules, ambition ladder, user preference card, pointers)
aer-skills/     hard-dependency stage skills (aer-* × 11 + humanizer) — a stage must load its skill definition before running
```

## Hard dependency / 硬依赖

The routed stage skills (`aer-*` × 11) and `humanizer` are **mandatory components**, not optional references: using this pipeline means loading each stage's skill definition from `aer-skills/` before executing it. If a definition is missing, stop and tell the user — never improvise from memory.

路由到的各阶段 skill（aer-* × 11）与 humanizer 是强制组件：使用本 pipeline 就必须先读入 `aer-skills/` 里对应阶段的定义再执行；定义缺失时停下报告，禁止凭记忆即兴替代。

## Signature / 署名

Made by LYU Minglei © 2026
