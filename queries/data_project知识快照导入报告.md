---
title: "data_project知识快照导入报告"
aliases: ["data_project导入报告", "知识快照导入复核", "context snapshot import report"]
created: 2026-04-24
updated: 2026-04-24
type: query
tags: [知识类型/问答, 业务动作/校验, 业务动作/过滤, 数据技术/血缘, 治理状态/内部, 治理状态/生效]
keywords: ["导入报告", "复核", "知识快照", "data_project"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# data_project知识快照导入报告

## 导入结论

本次导入已将 `data_project` 的自包含知识快照归档到 raw，并将稳定、可复用的知识单元提升为 wiki 页面。

## 输入与边界

- 输入快照：`D:\Dropbox\Project\data_project\context\exports\data_project-知识快照-2026-04-24-bc37852.md`
- raw 归档：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 事实源边界：仅 `context/tables.md`、`context/rules.md`、`context/dictionary.md`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 源提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 与上一快照：`data_project-知识快照-2026-04-23-ca1431d.md`

## 导入规模

- 数据对象页：`36`
- 业务规则页：`21`
- 字典概念页：`1`，包含 `17` 个字典条目
- 项目入口页：`1`
- 全局规范页：`1`
- 导入报告页：`1`

## 抽取策略

- `Tables｜数据对象` 按物理表拆成 `tables/` 页面，保留每个条目的结构化事实与原始事实摘录。
- `Rules｜业务规则` 按规则 ID 拆成 `rules/` 页面，保留规则逻辑、来源、补充摘录和重复合并痕迹。
- `Dictionary｜字典与术语` 暂不拆成 17 个页面，统一进入 `concepts/营销域语义字典`，避免过度原子化。
- 项目级全局说明进入 `standards/data_project上下文全局规范`，提升 SQL 与平台约束的可检索性。
- 关系索引、知识结构导览和版本差异进入 `scenarios/data_project知识快照导入`，便于 agent 从项目入口定位。

## 复核项

- raw 快照是否存在：通过，已归档到 `raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 页面数量是否匹配快照：通过，快照中的 `36` 个数据对象、`21` 条唯一规则、`17` 个字典条目均已进入对应页面或汇总页
- 新增页面是否登记到 index：通过，`index.md` 已登记 data_project 数据对象、业务规则、项目入口、全局规范、语义字典和导入报告
- 主要 wikilink 是否可解析：通过，扫描 `107` 个 markdown 文件、`749` 个 wikilink，未发现断链

## 后续建议

- 下一次导入同项目新快照时，应优先依据快照 diff 更新已有页面，而不是重复新建。
- 如果后续多个 data_project 出现同名规则或口径冲突，应在 wiki 层建立跨项目 comparison 或 canonical rule 页面。
