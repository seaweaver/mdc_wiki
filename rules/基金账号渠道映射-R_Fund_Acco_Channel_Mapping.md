---
title: "基金账号渠道映射｜R_Fund_Acco_Channel_Mapping"
aliases: ["基金账号渠道映射", "R_Fund_Acco_Channel_Mapping", "data_project:R_Fund_Acco_Channel_Mapping", "Fund Account Channel Mapping"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/渠道, 业务域/产品, 业务动作/映射, 业务动作/校验, 资产类型/基金, 治理状态/生效]
keywords: ["基金账号渠道映射", "R_Fund_Acco_Channel_Mapping", "Fund Account Channel Mapping", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 基金账号渠道映射｜R_Fund_Acco_Channel_Mapping

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Fund_Acco_Channel_Mapping`
- 英文锚点：`Fund Account Channel Mapping`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:R_Fund_Acco_Channel_Mapping
- canonical_key: R_Fund_Acco_Channel_Mapping
- rule_id: R_Fund_Acco_Channel_Mapping
- rule_name: 基金账号渠道映射 (Fund Account Channel Mapping)
- status: project-only
- change_type: unchanged
- content_hash: `7be2b07da5667c24`
- source_refs:
  - `context/rules.md#L231`

#### 结构化事实

- business_definition: 通过基金账号关联渠道信息，使用ROW_NUMBER去重取最新记录。
- use_cases: 历史订单归属、客户资产归属分析。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: `DWD_CUST_PR_DTL_DI`
- related_dictionary: 无显式命中

#### 原始事实摘录

* **业务定义**: 通过基金账号关联渠道信息，使用ROW_NUMBER去重取最新记录。
* **适用场景**: 历史订单归属、客户资产归属分析。
* **去重逻辑**: 每个基金账号可能有多条渠道分配记录，按时间降序排序取最新的一条（按 pt_time DESC, taqrlsh DESC 排序）
* **SQL 逻辑模板**:
  ```sql
  -- 基金账号渠道映射（去重）
  LEFT JOIN (
      SELECT DISTINCT 
          jjzh,           -- 基金账号（对应订单表DWD_CUST_PR_DTL_DI的src_cust_num）
          qdid,           -- 渠道网点ID（蕴含多层级的渠道网点信息）
          ROW_NUMBER() OVER (PARTITION BY jjzh ORDER BY pt_time DESC, taqrlsh DESC) AS rn
      FROM dcods.ods_cr_t_qd_cfjg_jy_di
  ) t2 
      ON t1.fund_acco = t2.jjzh
      AND t2.rn = 1  -- 只取每个基金账号的第一条记录（最新）
  ```

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
