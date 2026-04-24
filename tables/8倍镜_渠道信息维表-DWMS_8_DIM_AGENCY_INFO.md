---
title: "8倍镜_渠道信息维表｜DWMS_8_DIM_AGENCY_INFO"
aliases: ["8倍镜_渠道信息维表", "DWMS_8_DIM_AGENCY_INFO", "data_project:DWMS_8_DIM_AGENCY_INFO", "8倍镜_渠道信息维表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/渠道, 业务域/财务, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["8倍镜_渠道信息维表", "DWMS_8_DIM_AGENCY_INFO", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 8倍镜_渠道信息维表｜DWMS_8_DIM_AGENCY_INFO

## 概览

- 来源项目：`data_project`
- 物理表名：`DWMS_8_DIM_AGENCY_INFO`
- 业务名称：8倍镜_渠道信息维表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:DWMS_8_DIM_AGENCY_INFO
- canonical_key: DWMS_8_DIM_AGENCY_INFO
- table_name: DWMS_8_DIM_AGENCY_INFO
- object_name: 8倍镜_渠道信息维表
- domain: 八、8倍镜维度表
- platform: 大数据平台/Oracle
- status: project-only
- change_type: unchanged
- content_hash: `09805b25de250b6b`
- source_refs: `context/tables.md#L731`

#### 结构化事实

- business_role: 部门与渠道匹配的唯一数据源，用于确定渠道归属哪个部门。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: `渠道编码 (chn_num)`, `部门代码/部门名称 (AGENCYBELONG)`

#### 原始事实摘录

* **物理表名 (Oracle库)**: `CJHX_DWMS.DWMS_8_DIM_AGENCY_INFO`
* **物理表名 (大数据平台)**: `dcods.ods_dwms_8_dim_agency_info_f`
* **业务用途**: 部门与渠道匹配的唯一数据源，用于确定渠道归属哪个部门。
* **核心字段**:
  * `AGENCYNAME`: 渠道名称
  * `AGENCYNO`: 渠道代码
  * `AGENCYBELONG_CODE`: 部门代码
  * `AGENCYBELONG`: 部门名称（枚举值：网金、银行、券商、其他）
  * `MAIN_AGENCYNO`: 主渠道代码
  * `NETNO_DIR`: 网点目录
* **⚠️ 重要关联说明**:
  * **必须使用 `DISTINCT main_agencyno` 关联订单表或持仓表的 `retl_num`（销售商编码/渠道编码）**
  * **不能使用 `agencyno`** 进行关联，因为 `main_agencyno:agencyno` 是一对多关系
  * 示例：同一个主渠道编码 `022` 对应多个子渠道编码 `0226810`, `0220388`, `0229387`
* **AGENCYBELONG 枚举值说明**:
  | AGENCYBELONG | 对应部门 |
  | :--- | :--- |
  | 网金 | 网金业务部 |
  | 银行 | 银行渠道部 |
  | 券商 | 券商渠道部 |
  | 其他 | 其他部门 |
* **预设关联路径 (Relationships)**:
  * **关联订单/持仓表获取部门信息**: 
    ```sql
    -- 使用 DISTINCT main_agencyno 关联，避免数据重复
    JOIN (
        SELECT DISTINCT main_agencyno, agencybelong 
        FROM dcods.ods_dwms_8_dim_agency_info_f
    ) agency ON order_table.retl_num = agency.main_agencyno
    WHERE agency.agencybelong = '券商'  -- 过滤券商渠道部
    ```

---

# 第三部分：其他辅助表

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
