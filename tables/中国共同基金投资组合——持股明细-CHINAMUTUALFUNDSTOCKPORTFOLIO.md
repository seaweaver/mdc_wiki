---
title: "中国共同基金投资组合——持股明细｜CHINAMUTUALFUNDSTOCKPORTFOLIO"
aliases: ["中国共同基金投资组合——持股明细", "CHINAMUTUALFUNDSTOCKPORTFOLIO", "data_project:CHINAMUTUALFUNDSTOCKPORTFOLIO", "中国共同基金投资组合——持股明细表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 业务域/投研, 资产类型/基金, 资产类型/股票, 资产类型/组合, 数据技术/表, 治理状态/生效]
keywords: ["中国共同基金投资组合——持股明细", "CHINAMUTUALFUNDSTOCKPORTFOLIO", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 中国共同基金投资组合——持股明细｜CHINAMUTUALFUNDSTOCKPORTFOLIO

## 概览

- 来源项目：`data_project`
- 物理表名：`CHINAMUTUALFUNDSTOCKPORTFOLIO`
- 业务名称：中国共同基金投资组合——持股明细
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:CHINAMUTUALFUNDSTOCKPORTFOLIO
- canonical_key: CHINAMUTUALFUNDSTOCKPORTFOLIO
- table_name: CHINAMUTUALFUNDSTOCKPORTFOLIO
- object_name: 中国共同基金投资组合——持股明细
- domain: 十一、外部数据域 (Wind)
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `b0a660b55c0d02e4`
- source_refs: `context/tables.md#L864`

#### 结构化事实

- business_role: 记录基金定期公布的底层持有股票的明细数据。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名 (Oracle库)**: `WIND.CHINAMUTUALFUNDSTOCKPORTFOLIO`
* **业务用途**: 记录基金定期公布的底层持有股票的明细数据。
* **业务主键**: `S_INFO_WINDCODE` (Wind代码), `F_PRT_ENDDATE` (截止日期), `S_INFO_STOCKWINDCODE` (股票Wind代码)
* **核心字段**:
  * `S_INFO_WINDCODE`: Wind代码
  * `F_PRT_ENDDATE`: 截止日期 (格式: YYYYMMDD)
  * `S_INFO_STOCKWINDCODE`: 股票Wind代码（港股带有 '.HK' 后缀）
  * `F_PRT_STKVALUE`: 持股市值
  * `F_PRT_STKTONAV`: 持股市值占基金资产净值比例(%)

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
