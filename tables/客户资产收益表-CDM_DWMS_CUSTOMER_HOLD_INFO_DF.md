---
title: "客户资产收益表｜CDM_DWMS_CUSTOMER_HOLD_INFO_DF"
aliases: ["客户资产收益表", "CDM_DWMS_CUSTOMER_HOLD_INFO_DF", "data_project:CDM_DWMS_CUSTOMER_HOLD_INFO_DF", "客户资产收益表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/客户, 数据技术/表, 数据技术/字段, 数据技术/大数据平台, 治理状态/生效]
keywords: ["客户资产收益表", "CDM_DWMS_CUSTOMER_HOLD_INFO_DF", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 客户资产收益表｜CDM_DWMS_CUSTOMER_HOLD_INFO_DF

## 概览

- 来源项目：`data_project`
- 物理表名：`CDM_DWMS_CUSTOMER_HOLD_INFO_DF`
- 业务名称：客户资产收益表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:CDM_DWMS_CUSTOMER_HOLD_INFO_DF
- canonical_key: CDM_DWMS_CUSTOMER_HOLD_INFO_DF
- table_name: CDM_DWMS_CUSTOMER_HOLD_INFO_DF
- object_name: 客户资产收益表
- domain: 二、客户资产域
- platform: 大数据平台
- status: project-only
- change_type: unchanged
- content_hash: `5aa2dbe069795cc6`
- source_refs: `context/tables.md#L226`

#### 结构化事实

- business_role: 存储客户按产品类型分类的资产持有明细和收益统计，用于客户资产结构分析、产品类型偏好分析等。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名 (大数据平台)**: `dccdm.cdm_dwms_customer_hold_info_df`
* **分区字段**: `cjdt` (数据日期，格式: YYYYMMDD)
* **表类型**: CDM层（数据仓库中间层）
* **业务用途**: 存储客户按产品类型分类的资产持有明细和收益统计，用于客户资产结构分析、产品类型偏好分析等。
* **核心字段**:
  * `cjdt`: 数据日期（格式: YYYYMMDD，跑批日期）
  * `fund_acco`: 基金账号（主键/关联键，对应订单表DWD_CUST_PR_DTL_DI的src_cust_num，用于关联客户信息）
  * **持有金额字段（按产品类型）**:
    * `hold_balance_mix`: 混合型产品持有金额
    * `hold_balance_stock`: 股票型产品持有金额
    * `hold_balance_bond`: 债券型产品持有金额
    * `hold_balance_index`: 指数型产品持有金额
    * `hold_balance_cur`: 货币型产品持有金额
    * `hold_balance_fof`: FOF型产品持有金额
  * **持有份额字段（按产品类型）**:
    * `hold_share_mix`: 混合型产品持有份额
    * `hold_share_stock`: 股票型产品持有份额
    * `hold_share_bond`: 债券型产品持有份额
    * `hold_share_index`: 指数型产品持有份额
    * `hold_share_cur`: 货币型产品持有份额
    * `hold_share_fof`: FOF型产品持有份额
  * **产品数量统计字段**:
    * `hold_fund_cnt`: 当前持有产品数
    * `accumu_fund_cnt`: 累计持有产品数
    * `hold_fund_type_cnt`: 持有产品种类数
    * `hold_mix_cnt`: 持有混合型产品数
    * `hold_stock_cnt`: 持有股票型产品数
    * `hold_bond_cnt`: 持有债券型产品数
    * `hold_index_cnt`: 持有指数型产品数
    * `hold_cur_cnt`: 持有货币型产品数
    * `hold_fof_cnt`: 持有FOF型产品数
  * **占比字段**:
    * `cash_dividend_ratio`: 现金红利占比
    * `dividend_reinvest_ratio`: 红利再投资占比
    * `mix_assets_ratio`: 持有混合型产品资金占比
    * `stock_assets_ratio`: 持有股票型产品资金占比
    * `bond_assets_ratio`: 持有债券型产品资金占比
    * `index_assets_ratio`: 持有指数型产品资金占比
    * `cur_assets_ratio`: 持有货币型产品资金占比
    * `fof_assets_ratio`: 持有FOF型产品资金占比
* **预设关联路径 (Relationships)**:
  * **关联 [客户信息表] 获取客户基本信息**: `LEFT JOIN dccdm.cdm_dim_cust_f c ON hold.fund_acco = c.src_cust_num`
  * **关联 [客户资产汇总表] 获取总资产**: `LEFT JOIN dccdm.cdm_dwms_customer_assets_sum_df assets ON hold.fund_acco = assets.fund_acco AND hold.cjdt = assets.cjdt`
  * **关联 [渠道信息] (通过基金账号获取渠道)**: 参考 [客户资产汇总表] 的关联路径
  * **按指定快照日统计客户资产结构**: `WHERE hold.cjdt = '{snapshot_date}'`

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
