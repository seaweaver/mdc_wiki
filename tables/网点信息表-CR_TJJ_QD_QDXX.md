---
title: "网点信息表｜CR_TJJ_QD_QDXX"
aliases: ["网点信息表", "CR_TJJ_QD_QDXX", "data_project:CR_TJJ_QD_QDXX", "网点信息表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/组织, 业务域/渠道, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["网点信息表", "CR_TJJ_QD_QDXX", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 网点信息表｜CR_TJJ_QD_QDXX

## 概览

- 来源项目：`data_project`
- 物理表名：`CR_TJJ_QD_QDXX`
- 业务名称：网点信息表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:CR_TJJ_QD_QDXX
- canonical_key: CR_TJJ_QD_QDXX
- table_name: CR_TJJ_QD_QDXX
- object_name: 网点信息表
- domain: 三、渠道网点域
- platform: 大数据平台/Oracle
- status: project-only
- change_type: unchanged
- content_hash: `8860781ac255c961`
- source_refs: `context/tables.md#L277`

#### 结构化事实

- business_role: 存储渠道/网点详细信息，包括地理位置信息和机构代码
- key_fields: `id`
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名（大数据平台）**: `dcods.ods_cr_tjj_qd_qdxx_f` ⭐ **优先使用**
* **物理表名（Oracle库）**: `STAGE.CR_TJJ_QD_QDXX`
* **说明**: 同一张表在不同平台的存储路径
* **表类型**: ODS层（操作数据存储层）
* **业务用途**: 存储渠道/网点详细信息，包括地理位置信息和机构代码
* **主键**: `id`
* **核心字段**:
  * `id`: 渠道网点ID（主键，蕴含多层级的渠道网点信息，关联 ods_cr_t_qd_cfjg_jy_di.qdid）
  * `qdmc`: 渠道名称
  * `dxjgdm`: 代销机构代码（用于匹配归属规则中的 attr_channel）
  * `sfmc`: 省份名称（用于匹配归属规则中的 attr_province）
  * `csmc`: 城市名称（用于匹配归属规则中的 attr_city）
  * `sjdm`: 渠道网点上级ID

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
