# Paper Pipeline

> A stage-routed, discipline-enforced pipeline skill for empirical economics papers — from topic selection to journal submission.
> 实证经济学论文全流程辅助 skill：阶段自动路由 + 十条实战纪律。

## What it does / 它做什么

This skill makes an AI coding agent run the full lifecycle of an empirical paper **without the user having to say which step comes next**. It was distilled from a complete real-world run — topic selection, staggered-DID identification, 1.4M-row panel construction, full drafting, adversarial internal review, an external audit that caught two critical bugs, and journal selection — compressed into a routing table and ten general rules.

这个 skill 让 AI 编程代理自动跑通实证论文的全生命周期，用户无需逐步指挥。它提炼自一次完整的实战：选题 → staggered DID 识别 → 139 万行面板构建 → 全文写作 → 对抗式内审 → 外部审计（揪出两个致命错误）→ 选刊尽调，最终压缩为一张路由表和十条一般性纪律。

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

## Install / 安装

Copy the folder into your agent's skills directory (for ZCode: `~/.zcode/skills/paper-pipeline/`), or point the agent at this repository. The skill references a personal journal knowledge base (`~/Desktop/SSCI/`) — see SKILL.md §0 and §4; replace the pointers with your own or remove them.

将文件夹复制到代理的技能目录即可。skill 引用了个人投稿知识库（路径见 SKILL.md），可替换为自有路径或删除相关指针。

## Files / 文件

```
SKILL.md   the skill (routing table, ten rules, user preference card, pointers)
```

## Signature / 署名

Made by LYU Minglei © 2026
