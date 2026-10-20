# arkinvest-research

一个供 AI 代理（Claude Skills 等）使用的研究报告技能：按固定流程完成**公司、行业、市场规模、技术与成本曲线**研究，并按结构化格式成稿。

规范依据对 153 篇 ARK Invest 公开 Analyst Research 文章的审阅提炼：
- 保留其中反复使用、行之有效的结构，例如结论先行、单位经济拆解、估值模型模板和关键输入区间表；
- 针对审阅中反复发现的缺陷补上规则，例如标题口径不一、管理层说法被当作验证、熊市情景依赖尚不存在的业务、缺少证伪条件。

## 结构

```
arkinvest-research/
├── SKILL.md                     # 技能主文件（自包含的完整规则）
├── references/
│   └── full-spec.md             # 完整版《Research 报告写作与调查规范》
└── templates/
    ├── report-skeleton.md       # 报告输出骨架
    ├── ledger.csv               # 数据台账模板
    ├── conflict-log.csv         # 来源冲突记录模板
    ├── validation-table.md      # 验证指标与证伪条件表
    └── checklist.md             # 发布前检查清单
```

## 使用

- **Claude Code / Claude Agent SDK**：把整个文件夹放进 `~/.claude/skills/arkinvest-research/`，或放进项目的 `.claude/skills/`。
- **Claude.ai / Cowork**：在设置中上传技能，或把仓库打包成 zip 后上传。
- **其他 AI**：把 `SKILL.md` 作为系统提示或任务说明提供给模型；需要细节时，再附上 `references/full-spec.md`。

触发示例：“按 arkinvest-research 规范，研究某公司 2030 年的收入前景。”

## 工作流程

问题界定 → 数据台账 → 一手来源（L1–L6）→ 交叉核验 → 冲突处理 → 证据标签（事实 / 管理层说法 / 第三方估算 / 本报告推断 / 假设 / 未知）→ 反方证据与偏差检查 → 验证指标与证伪条件 → 成稿 → 检查清单

## 声明

- 本项目与 ARK Investment Management LLC 没有任何关联，也未获其认可或授权。“ARK Invest”仅用于说明本规范所依据的公开材料。
- 本项目不包含、也不复制原文章的句子、段落或图表，只提炼宏观结构和研究方法。
- 本项目不构成投资建议。
