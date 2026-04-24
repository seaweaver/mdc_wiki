---
title: "银行产品维度表｜CDM_DWMS_DIM_BANK_PD_F"
aliases: ["银行产品维度表", "CDM_DWMS_DIM_BANK_PD_F", "data_project:CDM_DWMS_DIM_BANK_PD_F", "银行产品维度表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 数据技术/表, 数据技术/字段, 数据技术/大数据平台, 治理状态/生效]
keywords: ["银行产品维度表", "CDM_DWMS_DIM_BANK_PD_F", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 银行产品维度表｜CDM_DWMS_DIM_BANK_PD_F

## 概览

- 来源项目：`data_project`
- 物理表名：`CDM_DWMS_DIM_BANK_PD_F`
- 业务名称：银行产品维度表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:CDM_DWMS_DIM_BANK_PD_F
- canonical_key: CDM_DWMS_DIM_BANK_PD_F
- table_name: CDM_DWMS_DIM_BANK_PD_F
- object_name: 银行产品维度表
- domain: 四、产品销售商维度域
- platform: Doris
- status: project-only
- change_type: unchanged
- content_hash: `7749fbfed5217639`
- source_refs: `context/tables.md#L377`

#### 结构化事实

- business_role: 存储银行渠道相关的产品维度信息，包含产品主代码和银行产品类别。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: `渠道相关`

#### 原始事实摘录

* **物理表名 (Doris平台)**: `cjhx_dwms.cdm_dwms_dim_bank_pd_f`
* **表类型**: CDM层 (维度表)
* **业务用途**: 存储银行渠道相关的产品维度信息，包含产品主代码和银行产品类别。
* **核心字段**:
  * `pd_code`: 产品代码 (关联键)
  * `main_pd_code`: 主产品代码
  * `main_pd_name`: 主产品名称
  * `bank_pri_clas`: 银行产品类别 (如: 股票型、债券型等)

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
