---
title: "券商渠道部保有规模统计｜R_Broker_Holdings"
aliases: ["券商渠道部保有规模统计", "R_Broker_Holdings", "data_project:R_Broker_Holdings", "Broker Channel Holdings Statistics"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/渠道, 业务域/销售, 业务动作/持仓, 业务动作/校验, 业务动作/计算, 治理状态/生效]
keywords: ["券商渠道部保有规模统计", "R_Broker_Holdings", "Broker Channel Holdings Statistics", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 券商渠道部保有规模统计｜R_Broker_Holdings

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Broker_Holdings`
- 英文锚点：`Broker Channel Holdings Statistics`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:R_Broker_Holdings
- canonical_key: R_Broker_Holdings
- rule_id: R_Broker_Holdings
- rule_name: 券商渠道部保有规模统计 (Broker Channel Holdings Statistics)
- status: project-only
- change_type: unchanged
- content_hash: `31a7eb066df88e45`
- source_refs:
  - `context/rules.md#L421`
  - `context/rules.md#L421`

#### 结构化事实

- business_definition: 券商渠道部的保有规模（存量规模/持仓规模）统计。涉及省份、城市、网点等地域信息时优先使用专用表。
- use_cases: 见原始事实摘录
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: 无显式命中
- related_dictionary: 无显式命中

#### 原始事实摘录

* **业务定义**: 券商渠道部的保有规模（存量规模/持仓规模）统计。涉及省份、城市、网点等地域信息时优先使用专用表。
* **数据来源**: `dccdm.cdm_dwd_ast_orde_bal_more_df`（订单余额模型_网点版）
* **表优势**: 该表蕴含每笔持仓的地理位置/网点信息，可快速统计地域维度的规模

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
