---
title: "订单余额快照过滤｜R_Order_Balance_Snapshot"
aliases: ["订单余额快照过滤", "R_Order_Balance_Snapshot", "data_project:R_Order_Balance_Snapshot", "Order Balance Snapshot Filter"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/订单, 业务动作/校验, 业务动作/过滤, 治理状态/生效]
keywords: ["订单余额快照过滤", "R_Order_Balance_Snapshot", "Order Balance Snapshot Filter", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 订单余额快照过滤｜R_Order_Balance_Snapshot

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Order_Balance_Snapshot`
- 英文锚点：`Order Balance Snapshot Filter`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:R_Order_Balance_Snapshot
- canonical_key: R_Order_Balance_Snapshot
- rule_id: R_Order_Balance_Snapshot
- rule_name: 订单余额快照过滤 (Order Balance Snapshot Filter)
- status: project-only
- change_type: unchanged
- content_hash: `e6036dad1ec9a233`
- source_refs:
  - `context/rules.md#L249`

#### 结构化事实

- business_definition: 在订单余额模型表中，按指定数据日期获取订单余额快照。
- use_cases: 统计某一时点的订单剩余金额、订单留存情况等。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: 无显式命中
- related_dictionary: 无显式命中

#### 原始事实摘录

* **业务定义**: 在订单余额模型表中，按指定数据日期获取订单余额快照。
* **适用场景**: 统计某一时点的订单剩余金额、订单留存情况等。
* **SQL 逻辑模板**:
  ```sql
  -- 订单余额快照过滤
  WHERE bal.data_date = '{snapshot_date}'  -- 例如: '20251206'
  ```

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
