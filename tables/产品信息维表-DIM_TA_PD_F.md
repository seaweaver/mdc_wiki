---
title: "产品信息维表｜DIM_TA_PD_F"
aliases: ["产品信息维表", "DIM_TA_PD_F", "data_project:DIM_TA_PD_F", "产品信息维表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["产品信息维表", "DIM_TA_PD_F", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 产品信息维表｜DIM_TA_PD_F

## 概览

- 来源项目：`data_project`
- 物理表名：`DIM_TA_PD_F`
- 业务名称：产品信息维表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:DIM_TA_PD_F
- canonical_key: DIM_TA_PD_F
- table_name: DIM_TA_PD_F
- object_name: 产品信息维表
- domain: 四、产品销售商维度域
- platform: 大数据平台/Oracle
- status: project-only
- change_type: unchanged
- content_hash: `ab8572afe0cf9630`
- source_refs: `context/tables.md#L366`

#### 结构化事实

- business_role: 未显式说明
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名（Oracle库）**: `CJHX_CDM.DIM_TA_PD_F`
* **物理表名（大数据平台）**: `dccdm.cdm_dim_ta_pd_f` ⭐ **优先使用**
* **核心字段**:
  * `pd_code`: 产品代码
  * `pd_abbr`: 产品名称
  * `coll_strt_date`: 募集开始日期
  * `coll_end_date`: 募集结束日期

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
