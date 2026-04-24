---
title: "绩效规模计算｜R_Performance_Scale"
aliases: ["绩效规模计算", "R_Performance_Scale", "data_project:R_Performance_Scale", "Performance Scale Calculation"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/财务, 业务动作/考核, 业务动作/校验, 业务动作/计算, 治理状态/生效]
keywords: ["绩效规模计算", "R_Performance_Scale", "Performance Scale Calculation", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 绩效规模计算｜R_Performance_Scale

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Performance_Scale`
- 英文锚点：`Performance Scale Calculation`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:R_Performance_Scale
- canonical_key: R_Performance_Scale
- rule_id: R_Performance_Scale
- rule_name: 绩效规模计算 (Performance Scale Calculation)
- status: project-only
- change_type: unchanged
- content_hash: `8f0d247c5ad960d7`
- source_refs:
  - `context/rules.md#L383`
  - `context/rules.md#L383`

#### 结构化事实

- business_definition: 根据管理费收入计算绩效规模。
- use_cases: 零售8倍镜部门绩效统计。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: 无显式命中
- related_dictionary: `部门代码/部门名称 (AGENCYBELONG)`

#### 原始事实摘录

* **业务定义**: 根据管理费收入计算绩效规模。
* **适用场景**: 零售8倍镜部门绩效统计。
* **计算公式**: `绩效规模 = 管理费 * 365 / 0.005 / 100000000` (单位: 亿, 保留4位小数)
* **SQL 逻辑模板**:
  ```sql
  ROUND(NVL(FEE, 0) * 365 / 0.005 / 100000000, 4)
  ```
* **注意事项**:
  * 8倍镜口径与财务口径一致
  * 该视图已按日期、渠道、产品维度预聚合
  * 存量数据为统计时点的快照数据
  * 申购/赎回为统计周期内的累计数据
  * ⚠️ 表A不含部门字段，部门信息必须通过关联表D获取
  * 关联渠道信息表时需要去重（GROUP BY），避免数据重复
  * ⚠️ WHERE条件中必须使用 `D.AGENCYBELONG`，不能使用 `A.AGENCYBELONG`（表A无此字段）
  * 使用 LEFT JOIN 关联基金信息表，防止因基金名称缺失导致数据丢失
  * ⚠️ 如有特殊业务需求（如申购包含定投、过滤无效记录），在具体SQL中按需实现，不作为公共规则

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
