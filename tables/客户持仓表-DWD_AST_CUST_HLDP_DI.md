---
title: "客户持仓表｜DWD_AST_CUST_HLDP_DI"
aliases: ["客户持仓表", "DWD_AST_CUST_HLDP_DI", "data_project:DWD_AST_CUST_HLDP_DI", "客户持仓表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/客户, 业务动作/持仓, 数据技术/表, 数据技术/字段, 数据技术/大数据平台, 治理状态/生效]
keywords: ["客户持仓表", "DWD_AST_CUST_HLDP_DI", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 客户持仓表｜DWD_AST_CUST_HLDP_DI

## 概览

- 来源项目：`data_project`
- 物理表名：`DWD_AST_CUST_HLDP_DI`
- 业务名称：客户持仓表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:DWD_AST_CUST_HLDP_DI
- canonical_key: DWD_AST_CUST_HLDP_DI
- table_name: DWD_AST_CUST_HLDP_DI
- object_name: 客户持仓表
- domain: 二、客户资产域
- platform: 大数据平台
- status: project-only
- change_type: unchanged
- content_hash: `0051056069da3472`
- source_refs: `context/tables.md#L157`

#### 结构化事实

- business_role: 未显式说明
- key_fields: `src_cust_num`, `pd_code`, `trd_acc`, `chn_num`, `data_date`
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: `分红方式代码 (bons_mode_code)`, `渠道编码 (chn_num)`

#### 原始事实摘录

* **物理表名 (大数据平台)**: `dccdm.dwd_ast_cust_hldp_di`
* **主键**: `src_cust_num`, `pd_code`, `trd_acc`, `chn_num`, `data_date`
* **核心字段**:
  * `cnfm_date`: 确认日期
  * `src_cust_num`: 来源系统客户编码/基金账号
  * `pd_code`: 产品代码
  * `trd_acc`: 交易账号
  * `chn_num`: 渠道编码
  * `retl_num`: 销售商编码
  * `bons_mode_code`: 分红方式代码（0: 红利再投资, 1: 现金分红）
  * `hldp_vol`: 持仓数量
  * `hldp_val`: 持仓市值
  * `data_date`: 数据日期（分区字段，格式: YYYYMMDD）
* **预设关联路径 (Relationships)**:
  * **关联 [销售商信息维表] 获取销售商名称**: `LEFT JOIN dccdm.cdm_dim_retl_info_f r ON base.retl_num = r.retl_num`
  * **关联 [产品信息维表] 获取产品名称**: `LEFT JOIN dccdm.cdm_dim_ta_pd_f p ON base.pd_code = p.pd_code`

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
