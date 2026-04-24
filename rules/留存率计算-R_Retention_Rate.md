---
title: "留存率计算｜R_Retention_Rate"
aliases: ["留存率计算", "R_Retention_Rate", "data_project:R_Retention_Rate", "Retention Rate"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务动作/校验, 业务动作/计算, 治理状态/生效]
keywords: ["留存率计算", "R_Retention_Rate", "Retention Rate", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 留存率计算｜R_Retention_Rate

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Retention_Rate`
- 英文锚点：`Retention Rate`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:R_Retention_Rate
- canonical_key: R_Retention_Rate
- rule_id: R_Retention_Rate
- rule_name: 留存率计算 (Retention Rate)
- status: project-only
- change_type: unchanged
- content_hash: `1cf0bc4ea0a90ffb`
- source_refs:
  - `context/rules.md#L258`

#### 结构化事实

- business_definition: 用订单在指定时间区间内的确认金额作为“区间申购金额”，用指定快照日的订单余额金额作为“剩余金额”，计算订单层面的留存率。
- use_cases: 渠道/产品/省市维度的订单留存分析。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: 无显式命中
- related_dictionary: 无显式命中

#### 原始事实摘录

* **业务定义**: 用订单在指定时间区间内的确认金额作为“区间申购金额”，用指定快照日的订单余额金额作为“剩余金额”，计算订单层面的留存率。
* **适用场景**: 渠道/产品/省市维度的订单留存分析。
* **SQL 逻辑模板**:
  ```sql
  -- 订单留存率计算
  -- 区间申购金额: SUM(cnfm_amt)
  -- 指定快照日剩余金额: SUM(orde_bal_amt)
  -- 留存率: 剩余金额 / 区间申购金额
  retention_rate = CASE 
                       WHEN SUM(base.cnfm_amt) = 0 THEN 0
                       ELSE SUM(bal.orde_bal_amt) / SUM(base.cnfm_amt)
                   END
  ```

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
