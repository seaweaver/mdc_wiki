---
title: "订单归属网点关系表｜CR_T_QD_CFJG_JY"
aliases: ["订单归属网点关系表", "CR_T_QD_CFJG_JY", "data_project:CR_T_QD_CFJG_JY", "订单归属网点关系表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/订单, 业务域/组织, 业务域/渠道, 业务动作/归属, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["订单归属网点关系表", "CR_T_QD_CFJG_JY", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 订单归属网点关系表｜CR_T_QD_CFJG_JY

## 概览

- 来源项目：`data_project`
- 物理表名：`CR_T_QD_CFJG_JY`
- 业务名称：订单归属网点关系表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:CR_T_QD_CFJG_JY
- canonical_key: CR_T_QD_CFJG_JY
- table_name: CR_T_QD_CFJG_JY
- object_name: 订单归属网点关系表
- domain: 三、渠道网点域
- platform: 大数据平台/Oracle
- status: project-only
- change_type: unchanged
- content_hash: `d78509c8d63bbc11`
- source_refs: `context/tables.md#L294`

#### 结构化事实

- business_role: 存储渠道分配结果明细数据，记录订单或基金账号对应的渠道网点ID
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名（大数据平台）**: `dcods.ods_cr_t_qd_cfjg_jy_di` ⭐ **优先使用**
* **物理表名（Oracle库）**: `STAGE.CR_T_QD_CFJG_JY`
* **说明**: 同一张表在不同平台的存储路径
* **表类型**: ODS层（操作数据存储层）
* **业务用途**: 存储渠道分配结果明细数据，记录订单或基金账号对应的渠道网点ID
* **核心字段**:
  * `taqrlsh`: 成交编号 (关联 DWD_CUST_PR_DTL_DI.mtch_no，Oracle库字段名)
  * `jjzh`: 基金账号 (大数据平台字段名，对应订单表DWD_CUST_PR_DTL_DI的src_cust_num，关联 cdm_dwms_customer_assets_sum_df.fund_acco)
  * `qdid`: 渠道网点ID（蕴含多层级的渠道网点信息，关联 ods_cr_tjj_qd_qdxx_f.id）
  * `pt_time`: 分配时间（大数据平台字段，用于排序去重）
* **去重逻辑**: 当通过基金账号关联时，使用 `ROW_NUMBER() OVER (PARTITION BY jjzh ORDER BY pt_time DESC, taqrlsh DESC)` 取每个基金账号最新的一条记录（按时间降序排序）

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
