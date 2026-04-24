---
title: "部门归属规则维度表｜DWMS_DIM_RULES_DEPARTMENT"
aliases: ["部门归属规则维度表", "DWMS_DIM_RULES_DEPARTMENT", "data_project:DWMS_DIM_RULES_DEPARTMENT", "部门归属规则维度表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/组织, 业务动作/归属, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["部门归属规则维度表", "DWMS_DIM_RULES_DEPARTMENT", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 部门归属规则维度表｜DWMS_DIM_RULES_DEPARTMENT

## 概览

- 来源项目：`data_project`
- 物理表名：`DWMS_DIM_RULES_DEPARTMENT`
- 业务名称：部门归属规则维度表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:DWMS_DIM_RULES_DEPARTMENT
- canonical_key: DWMS_DIM_RULES_DEPARTMENT
- table_name: DWMS_DIM_RULES_DEPARTMENT
- object_name: 部门归属规则维度表
- domain: 六、归属规则域
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `945f24bd79f68ebb`
- source_refs: `context/tables.md#L460`

#### 结构化事实

- business_role: 未显式说明
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: `策略组 (strategy_group)`

#### 原始事实摘录

* **物理表名 (Oracle库)**: `CJHX_DWMS.DWMS_DIM_RULES_DEPARTMENT`
* **核心字段**:
  * `strategy_group`: 规则策略组
  * `attr_prod`: 匹配产品
  * `attr_channel`: 匹配渠道
  * `attr_province`: 匹配省份
  * `attr_city`: 匹配城市
  * `dept_id`: 归属部门ID

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
