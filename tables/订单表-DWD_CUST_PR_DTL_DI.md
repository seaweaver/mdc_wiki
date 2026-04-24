---
title: "订单表｜DWD_CUST_PR_DTL_DI"
aliases: ["订单表", "DWD_CUST_PR_DTL_DI", "data_project:DWD_CUST_PR_DTL_DI", "订单表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/订单, 业务域/客户, 数据技术/表, 数据技术/字段, 数据技术/大数据平台, 治理状态/生效]
keywords: ["订单表", "DWD_CUST_PR_DTL_DI", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 订单表｜DWD_CUST_PR_DTL_DI

## 概览

- 来源项目：`data_project`
- 物理表名：`DWD_CUST_PR_DTL_DI`
- 业务名称：订单表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:DWD_CUST_PR_DTL_DI
- canonical_key: DWD_CUST_PR_DTL_DI
- table_name: DWD_CUST_PR_DTL_DI
- object_name: 订单表
- domain: 一、交易订单域
- platform: 大数据平台
- status: project-only
- change_type: unchanged
- content_hash: `35e3eb6362d46666`
- source_refs: `context/tables.md#L33`

#### 结构化事实

- business_role: 未显式说明
- key_fields: `mtch_no`
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: `交易类型 (ta_trd_mode_code)`, `渠道编码 (chn_num)`, `策略组 (strategy_group)`

#### 原始事实摘录

* **物理表名 (大数据平台)**: `DCCDM.DWD_CUST_PR_DTL_DI`
* **主键**: `mtch_no` (成交编号)
* **核心字段**:
  * `data_date`: 数据日期 (格式: YYYYMMDD)
  * `mtch_no`: 成交编号
  * `src_cust_num`: 来源系统客户编码 (用于计算户数)
  * `cnfm_amt`: 确认金额 (用于计算销量)
  * `pd_code`: 产品代码
  * `retl_num`: 销售商编码
  * `chn_num`: 渠道编码
  * `ta_trd_mode_code`: TA交易方式代码
* **预设关联路径 (Relationships)**:
  > AI 注意：当需要关联 [地理位置] 或 [业绩归属] 时，必须使用以下路径，严禁自行发挥。
  
  * **关联 [地理位置] (获取省市信息)**: 
    ```sql
    -- 路径: 订单 -> 中间表 -> 网点表
    -- 优先使用大数据平台路径
    LEFT JOIN dcods.ods_cr_t_qd_cfjg_jy_di B ON base.mtch_no = B.taqrlsh
    LEFT JOIN dcods.ods_cr_tjj_qd_qdxx_f C ON B.qdid = C.id
    -- 输出: C.sfmc (省份), C.csmc (城市)
    -- 注意: Oracle库路径为 STAGE.CR_T_QD_CFJG_JY 和 STAGE.CR_TJJ_QD_QDXX
    ```

  * **关联 [业绩归属] (获取归属部门)**:
    ```sql
    -- 前置条件: 必须先关联 [地理位置] 获取 C.sfmc, C.csmc
    -- 匹配逻辑: 产品 + 渠道 + 省份 + 城市 -> 规则表
    LEFT JOIN CJHX_DWMS.DWMS_DIM_RULES_DEPARTMENT R 
      ON base.pd_code = R.attr_prod 
      AND base.retl_num = R.attr_channel
      AND C.sfmc = R.attr_province
      AND C.csmc = R.attr_city
      AND R.strategy_group = '{Strategy_Group_Param}' -- 例如: '银行渠道部业绩归属'
    ```

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
