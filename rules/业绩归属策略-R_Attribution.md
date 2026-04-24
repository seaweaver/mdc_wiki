---
title: "业绩归属策略｜R_Attribution"
aliases: ["业绩归属策略", "R_Attribution", "data_project:R_Attribution", "Performance Attribution"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/组织, 业务域/产品, 业务动作/归属, 业务动作/校验, 资产类型/策略, 治理状态/生效]
keywords: ["业绩归属策略", "R_Attribution", "Performance Attribution", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 业绩归属策略｜R_Attribution

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Attribution`
- 英文锚点：`Performance Attribution`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:R_Attribution
- canonical_key: R_Attribution
- rule_id: R_Attribution
- rule_name: 业绩归属策略 (Performance Attribution)
- status: project-only
- change_type: unchanged
- content_hash: `dc54d5b73cb33fcc`
- source_refs:
  - `context/rules.md#L107`

#### 结构化事实

- business_definition: 根据订单属性将业绩归属到特定的部门或人员。
- use_cases: 银行渠道部业绩归属统计。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: 无显式命中
- related_dictionary: `策略组 (strategy_group)`

#### 原始事实摘录

* **业务定义**: 根据订单属性将业绩归属到特定的部门或人员。
* **适用场景**: 银行渠道部业绩归属统计。
* **SQL 逻辑模板**:
  ```sql
  -- 4字段精确匹配
  base.pd_code = R.attr_prod 
  AND base.retl_num = R.attr_channel
  AND C.sfmc = R.attr_province
  AND C.csmc = R.attr_city
  AND R.strategy_group = '{Strategy_Group_Param}'
  ```

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
