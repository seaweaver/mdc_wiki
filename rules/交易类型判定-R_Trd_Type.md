---
title: "交易类型判定｜R_Trd_Type"
aliases: ["交易类型判定", "R_Trd_Type", "data_project:R_Trd_Type", "Transaction Type"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/交易, 业务动作/校验, 业务动作/分类, 治理状态/生效]
keywords: ["交易类型判定", "R_Trd_Type", "Transaction Type", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 交易类型判定｜R_Trd_Type

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Trd_Type`
- 英文锚点：`Transaction Type`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:R_Trd_Type
- canonical_key: R_Trd_Type
- rule_id: R_Trd_Type
- rule_name: 交易类型判定 (Transaction Type)
- status: project-only
- change_type: unchanged
- content_hash: `acf43034b9f04509`
- source_refs:
  - `context/rules.md#L86`

#### 结构化事实

- business_definition: 识别订单是认购还是申购。
- use_cases: 筛选特定交易类型的订单。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: 无显式命中
- related_dictionary: `交易类型 (ta_trd_mode_code)`

#### 原始事实摘录

* **业务定义**: 识别订单是认购还是申购。
* **适用场景**: 筛选特定交易类型的订单。
* **SQL 逻辑模板**:
  ```sql
  -- 认购 (Subscription)
  substr(ta_trd_mode_code, 2, 2) = '01'
  
  -- 申购 (Purchase)
  substr(ta_trd_mode_code, 2, 2) = '02'
  ```

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
