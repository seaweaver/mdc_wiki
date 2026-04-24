---
title: "分红方式占比计算｜R_Dividend_Mode_Ratio"
aliases: ["分红方式占比计算", "R_Dividend_Mode_Ratio", "data_project:R_Dividend_Mode_Ratio", "Dividend Mode Ratio"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/交易, 业务动作/分红, 业务动作/校验, 业务动作/计算, 治理状态/生效]
keywords: ["分红方式占比计算", "R_Dividend_Mode_Ratio", "Dividend Mode Ratio", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 分红方式占比计算｜R_Dividend_Mode_Ratio

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Dividend_Mode_Ratio`
- 英文锚点：`Dividend Mode Ratio`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:R_Dividend_Mode_Ratio
- canonical_key: R_Dividend_Mode_Ratio
- rule_id: R_Dividend_Mode_Ratio
- rule_name: 分红方式占比计算 (Dividend Mode Ratio)
- status: project-only
- change_type: unchanged
- content_hash: `674ca0d0aeed08c6`
- source_refs:
  - `context/rules.md#L672`

#### 结构化事实

- business_definition: 统计持仓某产品的客户中，选择不同分红方式（如现金分红、红利再投资）的占比情况。
- use_cases: 产品分红方式偏好分析。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: 无显式命中
- related_dictionary: `分红方式代码 (bons_mode_code)`

#### 原始事实摘录

* **业务定义**: 统计持仓某产品的客户中，选择不同分红方式（如现金分红、红利再投资）的占比情况。
* **适用场景**: 产品分红方式偏好分析。
* **数据来源**: `dccdm.dwd_ast_cust_hldp_di` 或 `dccdm.dws_ast_cust_hldp_payf_di`
* **核心字段**: `bons_mode_code` (0: 红利再投资, 1: 现金分红)
* **SQL 逻辑模板**:
  ```sql
  -- 分红方式占比计算
  WITH holding_customers AS (
      SELECT
          hp.src_cust_num,
          hp.bons_mode_code,
          COUNT(1) AS cnt
      FROM dccdm.dws_ast_cust_hldp_payf_di hp
      JOIN dccdm.cdm_dim_ta_pd_f p ON hp.pd_code = p.pd_code
      WHERE hp.busi_date = '{snapshot_date}'
        AND p.pd_abbr LIKE '%{fund_name_keyword}%'
        AND COALESCE(hp.hldp_shr, 0) > 0
      GROUP BY hp.src_cust_num, hp.bons_mode_code
  )
  SELECT
      CASE 
          WHEN bons_mode_code = '0' THEN '红利再投资'
          WHEN bons_mode_code = '1' THEN '现金分红'
          ELSE '其他'
      END AS `分红方式`,
      COUNT(DISTINCT src_cust_num) AS `客户数量`,
      ROUND(COUNT(DISTINCT src_cust_num) * 100.0 / SUM(COUNT(DISTINCT src_cust_num)) OVER (), 2) AS `占比(%)`
  FROM holding_customers
  GROUP BY bons_mode_code
  ORDER BY `客户数量` DESC;
  ```

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
