---
title: "部门维度表｜DWMS_DIM_DEPARTMENT"
aliases: ["部门维度表", "DWMS_DIM_DEPARTMENT", "data_project:DWMS_DIM_DEPARTMENT", "部门维度表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/组织, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["部门维度表", "DWMS_DIM_DEPARTMENT", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 部门维度表｜DWMS_DIM_DEPARTMENT

## 概览

- 来源项目：`data_project`
- 物理表名：`DWMS_DIM_DEPARTMENT`
- 业务名称：部门维度表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:DWMS_DIM_DEPARTMENT
- canonical_key: DWMS_DIM_DEPARTMENT
- table_name: DWMS_DIM_DEPARTMENT
- object_name: 部门维度表
- domain: 五、组织人员域
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `77f6c35678820c31`
- source_refs: `context/tables.md#L400`

#### 结构化事实

- business_role: 未显式说明
- key_fields: `dept_id`
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名 (Oracle库)**: `CJHX_DWMS.DWMS_DIM_DEPARTMENT`
* **主键**: `dept_id`
* **核心字段**:
  * `dept_name`: 部门名称

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
