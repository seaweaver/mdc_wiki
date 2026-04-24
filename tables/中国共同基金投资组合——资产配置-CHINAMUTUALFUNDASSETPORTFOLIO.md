---
title: "中国共同基金投资组合——资产配置｜CHINAMUTUALFUNDASSETPORTFOLIO"
aliases: ["中国共同基金投资组合——资产配置", "CHINAMUTUALFUNDASSETPORTFOLIO", "data_project:CHINAMUTUALFUNDASSETPORTFOLIO", "中国共同基金投资组合——资产配置表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 业务域/投研, 资产类型/基金, 资产类型/组合, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["中国共同基金投资组合——资产配置", "CHINAMUTUALFUNDASSETPORTFOLIO", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 中国共同基金投资组合——资产配置｜CHINAMUTUALFUNDASSETPORTFOLIO

## 概览

- 来源项目：`data_project`
- 物理表名：`CHINAMUTUALFUNDASSETPORTFOLIO`
- 业务名称：中国共同基金投资组合——资产配置
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:CHINAMUTUALFUNDASSETPORTFOLIO
- canonical_key: CHINAMUTUALFUNDASSETPORTFOLIO
- table_name: CHINAMUTUALFUNDASSETPORTFOLIO
- object_name: 中国共同基金投资组合——资产配置
- domain: 十一、外部数据域 (Wind)
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `d07e6ad088545af3`
- source_refs: `context/tables.md#L851`

#### 结构化事实

- business_role: 记录基金定期（季度）公布的投资于各种类型证券资产的组合情况，包含港股投资市值。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名 (Oracle库)**: `WIND.CHINAMUTUALFUNDASSETPORTFOLIO`
* **业务用途**: 记录基金定期（季度）公布的投资于各种类型证券资产的组合情况，包含港股投资市值。
* **业务主键**: `S_INFO_WINDCODE` (Wind代码), `F_PRT_ENDDATE` (截止日期)
* **核心字段**:
  * `S_INFO_WINDCODE`: Wind代码
  * `F_PRT_ENDDATE`: 截止日期 (格式: YYYYMMDD)
  * `F_PRT_HKSTOCKVALUE`: 港股通投资港股市值
  * `F_PRT_HKSTOCKTONAV`: 港股通投资港股市值占资产净值比
  * `F_PRT_NETASSET`: 资产净值(元)

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
