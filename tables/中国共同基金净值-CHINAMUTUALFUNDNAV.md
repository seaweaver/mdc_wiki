---
title: "中国共同基金净值｜CHINAMUTUALFUNDNAV"
aliases: ["中国共同基金净值", "CHINAMUTUALFUNDNAV", "data_project:CHINAMUTUALFUNDNAV", "中国共同基金净值表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/基金, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["中国共同基金净值", "CHINAMUTUALFUNDNAV", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 中国共同基金净值｜CHINAMUTUALFUNDNAV

## 概览

- 来源项目：`data_project`
- 物理表名：`CHINAMUTUALFUNDNAV`
- 业务名称：中国共同基金净值
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:CHINAMUTUALFUNDNAV
- canonical_key: CHINAMUTUALFUNDNAV
- table_name: CHINAMUTUALFUNDNAV
- object_name: 中国共同基金净值
- domain: 十一、外部数据域 (Wind)
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `cd12e3a5f3581631`
- source_refs: `context/tables.md#L838`

#### 结构化事实

- business_role: 记录公募基金定期的单位净值与累计净值、复权净值等。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名 (Oracle库)**: `WIND.CHINAMUTUALFUNDNAV`
* **业务用途**: 记录公募基金定期的单位净值与累计净值、复权净值等。
* **业务主键**: `F_INFO_WINDCODE` (Wind代码), `PRICE_DATE` (截止日期)
* **核心字段**:
  * `F_INFO_WINDCODE`: Wind代码
  * `PRICE_DATE`: 截止日期 (格式: YYYYMMDD)
  * `F_NAV_UNIT`: 单位净值
  * `F_NAV_ACCUMULATED`: 累计净值
  * `F_NAV_ADJUSTED`: 复权单位净值

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
