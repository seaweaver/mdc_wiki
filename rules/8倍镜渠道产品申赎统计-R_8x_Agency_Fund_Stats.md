---
title: "8倍镜渠道产品申赎统计｜R_8x_Agency_Fund_Stats"
aliases: ["8倍镜渠道产品申赎统计", "R_8x_Agency_Fund_Stats", "data_project:R_8x_Agency_Fund_Stats", "8x Mirror Agency Fund Purchase/Redemption Stats"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/渠道, 业务域/产品, 业务域/财务, 业务动作/申购, 业务动作/赎回, 治理状态/生效]
keywords: ["8倍镜渠道产品申赎统计", "R_8x_Agency_Fund_Stats", "8x Mirror Agency Fund Purchase/Redemption Stats", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 8倍镜渠道产品申赎统计｜R_8x_Agency_Fund_Stats

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_8x_Agency_Fund_Stats`
- 英文锚点：`8x Mirror Agency Fund Purchase/Redemption Stats`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:R_8x_Agency_Fund_Stats
- canonical_key: R_8x_Agency_Fund_Stats
- rule_id: R_8x_Agency_Fund_Stats
- rule_name: 8倍镜渠道产品申赎统计 (8x Mirror Agency Fund Purchase/Redemption Stats)
- status: project-only
- change_type: unchanged
- content_hash: `c3f6e22e51b94003`
- source_refs:
  - `context/rules.md#L348`
  - `context/rules.md#L348`

#### 结构化事实

- business_definition: 统计按日期、部门、渠道、产品维度的存量、申购、赎回数据。
- use_cases: 券商部/银行部等部门的申购赎回业绩统计。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: `DWMS_8_DIM_AGENCY_INFO`, `DWMS_8_DIM_FUND_INFO`, `DWMS_V_8_DAY_AGENCY_FUND_HIVE`
- related_dictionary: `部门代码/部门名称 (AGENCYBELONG)`

#### 原始事实摘录

* **业务定义**: 统计按日期、部门、渠道、产品维度的存量、申购、赎回数据。
* **适用场景**: 券商部/银行部等部门的申购赎回业绩统计。
* **数据来源**: `CJHX_DWMS.DWMS_V_8_DAY_AGENCY_FUND_HIVE`
* **⚠️ 重要说明**: 
  * `DWMS_V_8_DAY_AGENCY_FUND_HIVE` 表**不含** `AGENCYBELONG`（部门信息）字段
  * 必须通过 `AGENCYNAME` 关联 `DWMS_8_DIM_AGENCY_INFO` 表（表D）来获取部门信息
* **输出格式**: 日期、渠道名称、产品代码、产品名称、存量规模、申购金额、申购份额、赎回金额、赎回份额
* **SQL 逻辑模板**:
  ```sql
  -- 8倍镜申购赎回统计（渠道+产品维度）
  -- 标准关联模式：主表 + 基金信息 + 渠道信息（获取部门）
  SELECT 
      A.CJDT,                        -- 交易确认日期
      A.AGENCYNAME,                   -- 渠道名称
      A.FUNDCODE,                     -- 基金代码
      B.FUNDNAME,                     -- 基金名称（来自基金信息表）
      A.AMOUNT AS 存量规模,            -- 存量金额
      A.BUY_AMOUNT AS 申购金额,        -- 申购金额
      A.BUY_SHARES AS 申购份额,        -- 申购份额
      A.SELL_AMOUNT AS 赎回金额,       -- 赎回金额
      A.SELL_SHARES AS 赎回份额        -- 赎回份额
  FROM CJHX_DWMS.DWMS_V_8_DAY_AGENCY_FUND_HIVE A
  LEFT JOIN CJHX_DWMS.DWMS_8_DIM_FUND_INFO B    -- 使用LEFT JOIN防止因基金名称缺失导致数据丢失
      ON A.FUNDCODE = B.FUNDCODE
  JOIN (
      SELECT AGENCYNAME, AGENCYBELONG 
      FROM CJHX_DWMS.DWMS_8_DIM_AGENCY_INFO 
      GROUP BY AGENCYNAME, AGENCYBELONG
  ) D ON A.AGENCYNAME = D.AGENCYNAME
  WHERE A.CJDT >= '{start_date}'      -- 统计起始日期
    AND D.AGENCYBELONG = '{dept_name}' -- ⚠️ 部门过滤（使用表D的AGENCYBELONG字段，如：'券商'、'银行'、'网金'）
  ORDER BY A.AMOUNT DESC, A.CJDT DESC -- 默认按存量规模从大到小排序
  ```

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
