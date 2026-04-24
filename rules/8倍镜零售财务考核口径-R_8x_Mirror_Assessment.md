---
title: "8倍镜零售财务考核口径｜R_8x_Mirror_Assessment"
aliases: ["8倍镜零售财务考核口径", "R_8x_Mirror_Assessment", "data_project:R_8x_Mirror_Assessment", "8x Mirror Retail Financial Assessment"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/财务, 业务动作/考核, 业务动作/校验, 治理状态/生效]
keywords: ["8倍镜零售财务考核口径", "R_8x_Mirror_Assessment", "8x Mirror Retail Financial Assessment", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 8倍镜零售财务考核口径｜R_8x_Mirror_Assessment

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_8x_Mirror_Assessment`
- 英文锚点：`8x Mirror Retail Financial Assessment`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:R_8x_Mirror_Assessment
- canonical_key: R_8x_Mirror_Assessment
- rule_id: R_8x_Mirror_Assessment
- rule_name: 8倍镜零售财务考核口径 (8x Mirror Retail Financial Assessment)
- status: project-only
- change_type: unchanged
- content_hash: `6b0f02111c2dc5b4`
- source_refs:
  - `context/rules.md#L317`
  - `context/rules.md#L317`

#### 结构化事实

- business_definition: 反映零售线的财务考核口径数据，包含存量、申购、赎回、定投等多个维度的统计。
- use_cases: 零售线业绩考核、规模统计。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: 无显式命中
- related_dictionary: 无显式命中

#### 原始事实摘录

* **业务定义**: 反映零售线的财务考核口径数据，包含存量、申购、赎回、定投等多个维度的统计。
* **适用场景**: 零售线业绩考核、规模统计。
* **计算口径**: 
  * **存量 (Stock)**: 统计时点的持有份额/金额。
  * **申购 (Buy)**: 统计周期内的确认申购数据。
  * **赎回 (Sell)**: 统计周期内的确认赎回数据。
  * **定投 (Auto)**: 统计周期内的定投确认数据。
* **注意**: 该口径由 `CJHX_VIEW.V_8_*` 系列视图提供，直接查询视图即可获取已加工好的考核数据。

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
