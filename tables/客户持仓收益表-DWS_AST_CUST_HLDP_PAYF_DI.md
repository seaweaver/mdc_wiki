---
title: "客户持仓收益表｜DWS_AST_CUST_HLDP_PAYF_DI"
aliases: ["客户持仓收益表", "DWS_AST_CUST_HLDP_PAYF_DI", "data_project:DWS_AST_CUST_HLDP_PAYF_DI", "客户持仓收益表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/客户, 业务动作/持仓, 数据技术/表, 数据技术/字段, 数据技术/大数据平台, 治理状态/生效]
keywords: ["客户持仓收益表", "DWS_AST_CUST_HLDP_PAYF_DI", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 客户持仓收益表｜DWS_AST_CUST_HLDP_PAYF_DI

## 概览

- 来源项目：`data_project`
- 物理表名：`DWS_AST_CUST_HLDP_PAYF_DI`
- 业务名称：客户持仓收益表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:DWS_AST_CUST_HLDP_PAYF_DI
- canonical_key: DWS_AST_CUST_HLDP_PAYF_DI
- table_name: DWS_AST_CUST_HLDP_PAYF_DI
- object_name: 客户持仓收益表
- domain: 二、客户资产域
- platform: 大数据平台
- status: project-only
- change_type: unchanged
- content_hash: `85613ff945fbdc3a`
- source_refs: `context/tables.md#L177`

#### 结构化事实

- business_role: 存储客户持仓的收益明细，包含累计收益率、持仓收益、近期收益等指标，用于客户收益分析。
- key_fields: `src_cust_num`, `pd_code`, `busi_date`
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: `分红方式代码 (bons_mode_code)`, `渠道编码 (chn_num)`

#### 原始事实摘录

* **物理表名 (大数据平台)**: `dccdm.dws_ast_cust_hldp_payf_di`
* **表类型**: DWS层（数据应用层）
* **业务用途**: 存储客户持仓的收益明细，包含累计收益率、持仓收益、近期收益等指标，用于客户收益分析。
* **主键**: `src_cust_num`, `pd_code`, `busi_date`
* **核心字段**:
  * `src_cust_num`: 来源系统客户编码/基金账号
  * `pd_code`: 产品代码
  * `busi_date`: 业务日期（快照日期，格式: YYYYMMDD）
  * `trd_acc`: 交易账号
  * `retl_num`: 销售商编码
  * `chn_num`: 渠道编码
  * `bons_mode_code`: 分红方式代码（0: 红利再投资, 1: 现金分红）
  * **持仓字段**:
    * `unit_net_val`: 单位净值
    * `hldp_shr`: 持仓份额
    * `hldp_val`: 持仓市值
  * **收益字段**:
    * `aggr_yld`: 累计收益率（核心字段，用于判定收益情况）
    * `tot_payf`: 累计收益
    * `hldp_payf`: 持仓收益
    * `tdy_payf`: 当日收益
  * **近期收益字段**:
    * `rect_7d_payf`: 近七天收益
    * `rect_15d_payf`: 近十五天收益
    * `rect_1m_payf`: 近一个月收益
    * `rect_3m_payf`: 近三个月收益
    * `rect_6m_payf`: 近六个月收益
    * `rect_1y_payf`: 近一年收益
  * **本金字段**:
    * `hold_prin`: 持有本金
    * `aggr_prin`: 累计本金
    * `rect_7d_prin`: 近七天本金
    * `rect_1m_prin`: 近一个月本金
    * `rect_3m_prin`: 近三个月本金
    * `rect_6m_prin`: 近六个月本金
    * `rect_1y_prin`: 近一年本金
* **预设关联路径 (Relationships)**:
  * **关联 [客户信息表] 获取客户基本信息**: `LEFT JOIN dccdm.cdm_dim_cust_f c ON payf.src_cust_num = c.src_cust_num`
  * **关联 [产品信息维表] 获取产品名称**: `LEFT JOIN dccdm.cdm_dim_ta_pd_f p ON payf.pd_code = p.pd_code`
  * **按指定快照日统计客户收益**: `WHERE payf.busi_date = '{snapshot_date}'`
* **注意事项**:
  * 该表按客户+产品维度统计收益，每日生成快照
  * `aggr_yld` (累计收益率) 是核心指标，用于判定客户盈亏情况
  * 筛选持有客户时使用 `hldp_shr > 0` 确保确实持有
  * 收益为正判定标准: `aggr_yld > 0`

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
