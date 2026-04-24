---
title: "累计指标计算｜R_Accumulate"
aliases: ["累计指标计算", "R_Accumulate", "data_project:R_Accumulate", "Accumulation"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务动作/校验, 业务动作/计算, 治理状态/生效]
keywords: ["累计指标计算", "R_Accumulate", "Accumulation", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 累计指标计算｜R_Accumulate

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Accumulate`
- 英文锚点：`Accumulation`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:R_Accumulate
- canonical_key: R_Accumulate
- rule_id: R_Accumulate
- rule_name: 累计指标计算 (Accumulation)
- status: project-only
- change_type: unchanged
- content_hash: `dfe7ec13a1327e4f`
- source_refs:
  - `context/rules.md#L98`

#### 结构化事实

- business_definition: 计算从募集开始至今的累计值。
- use_cases: 统计累计认购金额、累计认购户数。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: 无显式命中
- related_dictionary: 无显式命中

#### 原始事实摘录

* **业务定义**: 计算从募集开始至今的累计值。
* **适用场景**: 统计累计认购金额、累计认购户数。
* **SQL 逻辑模板**:
  ```sql
  -- 需要关联产品表获取 coll_strt_date
  data_date BETWEEN P.coll_strt_date AND '{target_date}'
  ```

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
