---
title: "正收益客户占比计算｜R_Profit_Customer_Ratio"
aliases: ["正收益客户占比计算", "R_Profit_Customer_Ratio", "data_project:R_Profit_Customer_Ratio", "Profit Customer Ratio"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/客户, 业务动作/校验, 业务动作/计算, 治理状态/生效]
keywords: ["正收益客户占比计算", "R_Profit_Customer_Ratio", "Profit Customer Ratio", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 正收益客户占比计算｜R_Profit_Customer_Ratio

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Profit_Customer_Ratio`
- 英文锚点：`Profit Customer Ratio`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:R_Profit_Customer_Ratio
- canonical_key: R_Profit_Customer_Ratio
- rule_id: R_Profit_Customer_Ratio
- rule_name: 正收益客户占比计算 (Profit Customer Ratio)
- status: project-only
- change_type: unchanged
- content_hash: `ff947be50b7b066c`
- source_refs:
  - `context/rules.md#L273`
  - `context/rules.md#L273`

#### 结构化事实

- business_definition: 统计持有某产品的客户中，累计收益率为正的客户所占比例。
- use_cases: 产品盈利能力分析、客户投资收益评估。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: 无显式命中
- related_dictionary: `客户类别代码 (cust_clas_code)`

#### 原始事实摘录

* **业务定义**: 统计持有某产品的客户中，累计收益率为正的客户所占比例。
* **适用场景**: 产品盈利能力分析、客户投资收益评估。
* **计算口径**:
  * **收益客户占比** = (累计收益率>0的客户数) / (持有该产品的总客户数)
  * **数据来源**: `dccdm.dws_ast_cust_hldp_payf_di` (客户持仓收益表)
  * **核心字段**: `aggr_yld` (累计收益率)
  * **收益判定**: `aggr_yld > 0` 视为收益为正
  * **持有判定**: `hldp_shr > 0` 确保确实持有该产品
* **SQL 逻辑模板**:
  ```sql
  -- 收益客户占比计算
  WITH holding_customers AS (
      SELECT
          hp.src_cust_num,
          hp.pd_code,
          hp.aggr_yld,
          CASE WHEN hp.aggr_yld > 0 THEN 1 ELSE 0 END AS is_profit
      FROM dccdm.dws_ast_cust_hldp_payf_di hp
      JOIN dccdm.cdm_dim_ta_pd_f p ON hp.pd_code = p.pd_code
      LEFT JOIN dccdm.cdm_dim_cust_f c ON hp.src_cust_num = c.src_cust_num
      WHERE hp.busi_date = '{snapshot_date}'     -- 快照日
        AND p.pd_abbr LIKE '%产品名%'              -- 产品过滤
        AND c.cust_clas_code = '01'              -- 个人客户
        AND COALESCE(hp.hldp_shr, 0) > 0         -- 确实持有
  )
  SELECT
      pd_code,
      COUNT(DISTINCT src_cust_num) AS total_customers,        -- 持有客户总数
      SUM(is_profit) AS profit_customers,                     -- 收益为正客户数
      CASE 
          WHEN COUNT(DISTINCT src_cust_num) = 0 THEN 0
          ELSE SUM(is_profit) * 100.0 / COUNT(DISTINCT src_cust_num)
      END AS profit_customer_ratio                            -- 收益客户占比
  FROM holding_customers
  GROUP BY pd_code
  ```
* **注意事项**:
  * 基于客户维度统计，不是订单维度
  * 使用快照日数据，统计当日持有情况
  * 收益判定基于累计收益率，反映客户整体投资表现
  * 与留存率的区别：留存率基于订单，收益客户占比基于客户
  * 使用大数据平台表，字段名全部小写

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
