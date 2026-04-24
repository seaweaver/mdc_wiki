---
title: "客户信息表｜CDM_DIM_CUST_F"
aliases: ["客户信息表", "CDM_DIM_CUST_F", "data_project:CDM_DIM_CUST_F", "客户信息表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/客户, 数据技术/表, 数据技术/字段, 数据技术/大数据平台, 治理状态/生效]
keywords: ["客户信息表", "CDM_DIM_CUST_F", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 客户信息表｜CDM_DIM_CUST_F

## 概览

- 来源项目：`data_project`
- 物理表名：`CDM_DIM_CUST_F`
- 业务名称：客户信息表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:CDM_DIM_CUST_F
- canonical_key: CDM_DIM_CUST_F
- table_name: CDM_DIM_CUST_F
- object_name: 客户信息表
- domain: 二、客户资产域
- platform: 大数据平台
- status: project-only
- change_type: unchanged
- content_hash: `6426240fffe50a1e`
- source_refs: `context/tables.md#L116`

#### 结构化事实

- business_role: 未显式说明
- key_fields: `src_cust_num`
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: `客户类别代码 (cust_clas_code)`

#### 原始事实摘录

* **物理表名 (大数据平台)**: `dccdm.cdm_dim_cust_f`
* **主键**: `src_cust_num`
* **核心字段**:
  * `src_cust_num`: 来源系统客户编码/基金账号
  * `cust_fn`: 客户全称
  * `cust_abbr`: 客户简称
  * `cust_cert_num`: 客户证件号码/身份证号
  * `cust_cert_type_code`: 客户证件类型代码
  * `cust_clas_code`: 客户类别代码
  * `cust_mobile`: 客户手机号（用于过滤有手机号的客户）
* **预设关联路径 (Relationships)**:
  * **关联 [客户持仓表] 获取客户信息**: `LEFT JOIN dccdm.cdm_dim_cust_f c ON base.src_cust_num = c.src_cust_num`

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
