---
title: "客户资产汇总表｜CDM_DWMS_CUSTOMER_ASSETS_SUM_DF"
aliases: ["客户资产汇总表", "CDM_DWMS_CUSTOMER_ASSETS_SUM_DF", "data_project:CDM_DWMS_CUSTOMER_ASSETS_SUM_DF", "客户资产汇总表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/客户, 业务动作/统计, 数据技术/表, 数据技术/字段, 数据技术/大数据平台, 治理状态/生效]
keywords: ["客户资产汇总表", "CDM_DWMS_CUSTOMER_ASSETS_SUM_DF", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 客户资产汇总表｜CDM_DWMS_CUSTOMER_ASSETS_SUM_DF

## 概览

- 来源项目：`data_project`
- 物理表名：`CDM_DWMS_CUSTOMER_ASSETS_SUM_DF`
- 业务名称：客户资产汇总表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:CDM_DWMS_CUSTOMER_ASSETS_SUM_DF
- canonical_key: CDM_DWMS_CUSTOMER_ASSETS_SUM_DF
- table_name: CDM_DWMS_CUSTOMER_ASSETS_SUM_DF
- object_name: 客户资产汇总表
- domain: 二、客户资产域
- platform: 大数据平台
- status: project-only
- change_type: unchanged
- content_hash: `d2ae0a55379c7fa9`
- source_refs: `context/tables.md#L132`

#### 结构化事实

- business_role: 存储客户资产汇总数据，用于历史订单归属分析
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名 (大数据平台)**: `dccdm.cdm_dwms_customer_assets_sum_df`
* **物理表名 (Oracle库)**: `CJHX_DWMS.DWMS_CUSTOMER_ASSETS_SUM`
* **表类型**: CDM层（数据仓库中间层）
* **业务用途**: 存储客户资产汇总数据，用于历史订单归属分析
* **核心字段**:
  * `fund_acco`: 基金账号（主键/关联键，对应订单表DWD_CUST_PR_DTL_DI的src_cust_num，用于关联渠道信息）
  * `cjdt`: 数据日期（格式: YYYYMMDD，数据快照日期）
  * `hold_balance`: 持有余额（客户在某个时点的基金持有余额）
* **预设关联路径 (Relationships)**:
  * **关联 [渠道信息] (通过基金账号获取渠道)**: 
    ```sql
    -- 路径: 客户资产 -> 渠道分配结果表 -> 渠道信息表
    LEFT JOIN (
        SELECT DISTINCT 
            jjzh, qdid,  -- qdid: 渠道网点ID（蕴含多层级的渠道网点信息）
            ROW_NUMBER() OVER (PARTITION BY jjzh ORDER BY pt_time DESC, taqrlsh DESC) AS rn  -- 按时间降序排序，取最新的一条
        FROM dcods.ods_cr_t_qd_cfjg_jy_di
    ) t2 ON t1.fund_acco = t2.jjzh AND t2.rn = 1
    LEFT JOIN dcods.ods_cr_tjj_qd_qdxx_f t3 ON t2.qdid = t3.id
    -- 输出: t3.qdmc (渠道名称), t3.dxjgdm (代销机构代码), t3.sfmc (省份), t3.csmc (城市)
    ```

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
