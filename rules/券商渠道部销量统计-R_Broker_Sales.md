---
title: "券商渠道部销量统计｜R_Broker_Sales"
aliases: ["券商渠道部销量统计", "R_Broker_Sales", "data_project:R_Broker_Sales", "Broker Channel Sales Statistics"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/渠道, 业务域/销售, 业务动作/校验, 业务动作/统计, 治理状态/生效]
keywords: ["券商渠道部销量统计", "R_Broker_Sales", "Broker Channel Sales Statistics", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 券商渠道部销量统计｜R_Broker_Sales

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Broker_Sales`
- 英文锚点：`Broker Channel Sales Statistics`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:R_Broker_Sales
- canonical_key: R_Broker_Sales
- rule_id: R_Broker_Sales
- rule_name: 券商渠道部销量统计 (Broker Channel Sales Statistics)
- status: project-only
- change_type: unchanged
- content_hash: `dd86d29c30e311b3`
- source_refs:
  - `context/rules.md#L413`
  - `context/rules.md#L413`

#### 结构化事实

- business_definition: 券商渠道部的销量统计口径。销量 = 认购 + 申购 + 转换入。
- use_cases: 见原始事实摘录
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: `DWD_CUST_PR_DTL_DI`
- related_dictionary: `交易类型 (ta_trd_mode_code)`

#### 原始事实摘录

* **业务定义**: 券商渠道部的销量统计口径。销量 = 认购 + 申购 + 转换入。
* **数据来源**: `DCCDM.DWD_CUST_PR_DTL_DI`（客户交易订单表）
* **交易类型判定**:
  * 认购: `substr(code,2,2) = '01'`
  * 申购: `substr(code,2,2) = '02'`
  * 转换入: `substr(code,2,2) = '16'`

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
