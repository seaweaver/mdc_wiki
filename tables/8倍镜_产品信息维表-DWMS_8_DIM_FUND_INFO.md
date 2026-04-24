---
title: "8倍镜_产品信息维表｜DWMS_8_DIM_FUND_INFO"
aliases: ["8倍镜_产品信息维表", "DWMS_8_DIM_FUND_INFO", "data_project:DWMS_8_DIM_FUND_INFO", "8倍镜_产品信息维表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 业务域/财务, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["8倍镜_产品信息维表", "DWMS_8_DIM_FUND_INFO", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 8倍镜_产品信息维表｜DWMS_8_DIM_FUND_INFO

## 概览

- 来源项目：`data_project`
- 物理表名：`DWMS_8_DIM_FUND_INFO`
- 业务名称：8倍镜_产品信息维表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:DWMS_8_DIM_FUND_INFO
- canonical_key: DWMS_8_DIM_FUND_INFO
- table_name: DWMS_8_DIM_FUND_INFO
- object_name: 8倍镜_产品信息维表
- domain: 八、8倍镜维度表
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `fdbfd7aec3ef882d`
- source_refs: `context/tables.md#L705`

#### 结构化事实

- business_role: 未显式说明
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名 (Oracle库)**: `CJHX_DWMS.DWMS_8_DIM_FUND_INFO`
* **核心字段**:
  * `FUNDCODE`: 基金代码
  * `FUNDNAME`: 基金名称
  * `MANAGER_FEE_RATE`: 管理费率
  * `FUNDTYPE`: 基金类型

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
