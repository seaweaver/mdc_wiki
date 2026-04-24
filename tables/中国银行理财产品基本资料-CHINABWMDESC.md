---
title: "中国银行理财产品基本资料｜CHINABWMDESC"
aliases: ["中国银行理财产品基本资料", "CHINABWMDESC", "data_project:CHINABWMDESC", "中国银行理财产品基本资料表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/银行理财, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["中国银行理财产品基本资料", "CHINABWMDESC", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 中国银行理财产品基本资料｜CHINABWMDESC

## 概览

- 来源项目：`data_project`
- 物理表名：`CHINABWMDESC`
- 业务名称：中国银行理财产品基本资料
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:CHINABWMDESC
- canonical_key: CHINABWMDESC
- table_name: CHINABWMDESC
- object_name: 中国银行理财产品基本资料
- domain: 十一、外部数据域 (Wind)
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `70147d9954d589f5`
- source_refs: `context/tables.md#L801`

#### 结构化事实

- business_role: 记录银行理财产品的基本资料，如发行人、发售地区等。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名 (Oracle库)**: `WIND.CHINABWMDESC`
* **业务用途**: 记录银行理财产品的基本资料，如发行人、发售地区等。
* **业务主键**: `S_INFO_WINDCODE` (Wind代码)
* **核心字段**:
  * `S_INFO_WINDCODE`: Wind代码
  * `FULLNAME`: 产品名称
  * `ISSUERNAME`: 发行人
  * `ISSUINGPLACE`: 发售地区
* **预设关联路径**: 关联理财净值表(CHINABWMNAV)获取时间序列数据。

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
