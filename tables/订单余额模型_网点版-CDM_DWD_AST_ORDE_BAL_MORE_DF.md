---
title: "订单余额模型_网点版｜CDM_DWD_AST_ORDE_BAL_MORE_DF"
aliases: ["订单余额模型_网点版", "CDM_DWD_AST_ORDE_BAL_MORE_DF", "data_project:CDM_DWD_AST_ORDE_BAL_MORE_DF", "订单余额模型_网点版表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/订单, 业务域/组织, 业务域/渠道, 数据技术/表, 数据技术/字段, 数据技术/大数据平台, 治理状态/生效]
keywords: ["订单余额模型_网点版", "CDM_DWD_AST_ORDE_BAL_MORE_DF", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 订单余额模型_网点版｜CDM_DWD_AST_ORDE_BAL_MORE_DF

## 概览

- 来源项目：`data_project`
- 物理表名：`CDM_DWD_AST_ORDE_BAL_MORE_DF`
- 业务名称：订单余额模型_网点版
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:CDM_DWD_AST_ORDE_BAL_MORE_DF
- canonical_key: CDM_DWD_AST_ORDE_BAL_MORE_DF
- table_name: CDM_DWD_AST_ORDE_BAL_MORE_DF
- object_name: 订单余额模型_网点版
- domain: 一、交易订单域
- platform: 大数据平台
- status: project-only
- change_type: unchanged
- content_hash: `aca1f3b4a36a829b`
- source_refs: `context/tables.md#L72`

#### 结构化事实

- business_role: 存储订单在某一数据日期的余额明细，**包含地理位置/网点信息**，用于按订单维度统计剩余金额、订单留存情况，特别适用于省份城市网点维度的保有规模统计。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名 (大数据平台)**: `dccdm.cdm_dwd_ast_orde_bal_more_df`
* **分区字段**: `data_date` (数据日期，格式: YYYYMMDD)
* **业务用途**: 存储订单在某一数据日期的余额明细，**包含地理位置/网点信息**，用于按订单维度统计剩余金额、订单留存情况，特别适用于省份城市网点维度的保有规模统计。
* **⚠️ 使用场景**: 当需要统计涉及省份、城市、网点等地域信息的保有/存量规模时，优先使用此表。
* **核心字段**:
  * `fund_acc`: 基金账号
  * `trd_acc`: 交易账号
  * `pd_code`: 产品代码
  * `shr_type`: 份额类型
  * `orde_no`: 订单编号
  * `orde_bal`: 订单余额
  * `orde_bal_amt`: 订单余额金额
  * `retl_num`: 销售商编码
  * `brch_num`: 网点编码
  * `cnfm_date`: 确认日期
  * `init_amt`: 初始金额
  * `init_shr`: 初始份额
  * `init_unit_net_val`: 初始单位净值
  * `aep`: 管理费
  * **地理位置字段**:
    * `brch_code`: 网点代码
    * `brch_name`: 网点名称
    * `brch_grad`: 网点等级
    * `prov_code`: 省份代码
    * `prov_name`: 省份名称
    * `city_code`: 城市代码
    * `city_name`: 城市名称
* **预设关联路径 (Relationships)**:
  * **关联 [订单表] 获取订单初始金额/确认金额等信息**: `JOIN DCCDM.DWD_CUST_PR_DTL_DI o ON bal.orde_no = o.mtch_no`
  * **按指定快照日统计订单余额**: `WHERE bal.data_date = '{snapshot_date}'`
  * **关联渠道信息表过滤部门**: 
    ```sql
    JOIN (
        SELECT DISTINCT main_agencyno, agencybelong 
        FROM dcods.ods_dwms_8_dim_agency_info_f
    ) agency ON bal.retl_num = agency.main_agencyno
    WHERE agency.agencybelong = '券商'  -- 筛选券商渠道部
    ```

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
