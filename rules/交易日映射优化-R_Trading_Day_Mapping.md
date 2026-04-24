---
title: "交易日映射优化｜R_Trading_Day_Mapping"
aliases: ["交易日映射优化", "R_Trading_Day_Mapping", "data_project:R_Trading_Day_Mapping", "Trading Day Mapping Optimization"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/交易, 业务动作/映射, 业务动作/校验, 治理状态/生效]
keywords: ["交易日映射优化", "R_Trading_Day_Mapping", "Trading Day Mapping Optimization", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 交易日映射优化｜R_Trading_Day_Mapping

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Trading_Day_Mapping`
- 英文锚点：`Trading Day Mapping Optimization`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:R_Trading_Day_Mapping
- canonical_key: R_Trading_Day_Mapping
- rule_id: R_Trading_Day_Mapping
- rule_name: 交易日映射优化 (Trading Day Mapping Optimization)
- status: project-only
- change_type: unchanged
- content_hash: `3f0a3fda149fc71c`
- source_refs:
  - `context/rules.md#L437`
  - `context/rules.md#L437`

#### 结构化事实

- business_definition: 将目标日期（如每季末自然日）映射到最近的前一个交易日。
- use_cases: 行业数据（自然日）与内部数据（交易日）关联分析。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: `DWMS_V_8_DAY_AGENCY_FUND_HIVE`
- related_dictionary: 无显式命中

#### 原始事实摘录

* **业务定义**: 将目标日期（如每季末自然日）映射到最近的前一个交易日。
* **适用场景**: 行业数据（自然日）与内部数据（交易日）关联分析。
* **性能痛点**: 直接 JOIN 交易表并使用 `MAX(CJDT)` 或 `DISTINCT` 容易导致全表扫描，性能极差。
* **优化方案**: 使用 **标量子查询 (Scalar Subquery)** 配合 **时间窗口过滤**，利用索引/分区裁剪。
* **SQL 逻辑模板**:
  ```sql
  -- ✅ 推荐：标量子查询 + 30天回溯窗口
  SELECT 
      qtr.quarter_end,
      (
          SELECT MAX(A.CJDT)
          FROM CJHX_DWMS.DWMS_V_8_DAY_AGENCY_FUND_HIVE A
          WHERE A.CJDT <= qtr.quarter_end
            AND A.CJDT >= TO_CHAR(TO_DATE(qtr.quarter_end, 'YYYYMMDD') - 30, 'YYYYMMDD')
      ) AS last_trading_day
  FROM dates qtr
  ```

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
