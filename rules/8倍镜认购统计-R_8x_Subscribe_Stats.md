---
title: "8倍镜认购统计｜R_8x_Subscribe_Stats"
aliases: ["8倍镜认购统计", "R_8x_Subscribe_Stats", "data_project:R_8x_Subscribe_Stats", "8x Mirror Subscription Stats"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/交易, 业务域/财务, 业务动作/认购, 业务动作/校验, 业务动作/统计, 治理状态/生效]
keywords: ["8倍镜认购统计", "R_8x_Subscribe_Stats", "8x Mirror Subscription Stats", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 8倍镜认购统计｜R_8x_Subscribe_Stats

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_8x_Subscribe_Stats`
- 英文锚点：`8x Mirror Subscription Stats`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:R_8x_Subscribe_Stats
- canonical_key: R_8x_Subscribe_Stats
- rule_id: R_8x_Subscribe_Stats
- rule_name: 8倍镜认购统计 (8x Mirror Subscription Stats)
- status: project-only
- change_type: unchanged
- content_hash: `3cfb214be1445c7a`
- source_refs:
  - `context/rules.md#L327`
  - `context/rules.md#L327`

#### 结构化事实

- business_definition: 统计按部门、渠道、产品维度汇总的认购数据。
- use_cases: 认购业绩统计、部门认购分析。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: `DWMS_8_SUB_AGENCY_FUND`
- related_dictionary: `部门代码/部门名称 (AGENCYBELONG)`

#### 原始事实摘录

* **业务定义**: 统计按部门、渠道、产品维度汇总的认购数据。
* **适用场景**: 认购业绩统计、部门认购分析。
* **数据来源**: `CJHX_DWMS.DWMS_8_SUB_AGENCY_FUND`
* **SQL 逻辑模板**:
  ```sql
  -- 8倍镜认购统计
  SELECT 
      CJDT,                          -- 交易确认日期
      AGENCYBELONG,                   -- 部门名称
      AGENCYNAME,                     -- 渠道名称
      FUNDCODE,                       -- 基金代码
      FUNDNAME,                       -- 基金名称
      SUM(SUBSCRIBE_AMOUNT) AS SUBSCRIBE_AMOUNT  -- 认购金额
  FROM CJHX_DWMS.DWMS_8_SUB_AGENCY_FUND
  WHERE cjdt >= '{start_date}'        -- 起始日期
    AND SUBSCRIBE_AMOUNT > 0          -- 排除无效数据
  GROUP BY CJDT, AGENCYBELONG, AGENCYNAME, FUNDCODE, FUNDNAME
  ORDER BY CJDT DESC
  ```

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
