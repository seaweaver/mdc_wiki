---
title: "8倍镜_产品简称维表｜DWMS_8_DIM_FUND_SHORTNAME"
aliases: ["8倍镜_产品简称维表", "DWMS_8_DIM_FUND_SHORTNAME", "data_project:DWMS_8_DIM_FUND_SHORTNAME", "8倍镜_产品简称维表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 业务域/财务, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["8倍镜_产品简称维表", "DWMS_8_DIM_FUND_SHORTNAME", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 8倍镜_产品简称维表｜DWMS_8_DIM_FUND_SHORTNAME

## 概览

- 来源项目：`data_project`
- 物理表名：`DWMS_8_DIM_FUND_SHORTNAME`
- 业务名称：8倍镜_产品简称维表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:DWMS_8_DIM_FUND_SHORTNAME
- canonical_key: DWMS_8_DIM_FUND_SHORTNAME
- table_name: DWMS_8_DIM_FUND_SHORTNAME
- object_name: 8倍镜_产品简称维表
- domain: 八、8倍镜维度表
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `8e4eece393e763b2`
- source_refs: `context/tables.md#L715`

#### 结构化事实

- business_role: 存储基金产品的简称信息，用于报表展示和查询优化。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名 (Oracle库)**: `CJHX_DWMS.DWMS_8_DIM_FUND_SHORTNAME`
* **业务用途**: 存储基金产品的简称信息，用于报表展示和查询优化。
* **核心字段**:
  * `FUNDCODE`: 基金代码（主键，关联其他表的外键）
  * `SHORTNAME`: 基金简称（用于报表显示）
* **预设关联路径 (Relationships)**:
  * **关联8倍镜统计表获取基金简称**: 
    ```sql
    LEFT JOIN CJHX_DWMS.DWMS_8_DIM_FUND_SHORTNAME f
        ON base.FUNDCODE = f.FUNDCODE
    ```
  * **通常与基金信息维表一起使用**: 同时关联 `DWMS_8_DIM_FUND_INFO` (获取详细信息) 和 `DWMS_8_DIM_FUND_SHORTNAME` (获取简称)

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
