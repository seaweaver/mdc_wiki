---
title: "行业机构名称匹配｜R_Industry_Agency_Map"
aliases: ["行业机构名称匹配", "R_Industry_Agency_Map", "data_project:R_Industry_Agency_Map", "Industry Agency Name Mapping"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/组织, 业务动作/映射, 业务动作/校验, 治理状态/生效]
keywords: ["行业机构名称匹配", "R_Industry_Agency_Map", "Industry Agency Name Mapping", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 行业机构名称匹配｜R_Industry_Agency_Map

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Industry_Agency_Map`
- 英文锚点：`Industry Agency Name Mapping`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:R_Industry_Agency_Map
- canonical_key: R_Industry_Agency_Map
- rule_id: R_Industry_Agency_Map
- rule_name: 行业机构名称匹配 (Industry Agency Name Mapping)
- status: project-only
- change_type: unchanged
- content_hash: `28a260606a8a07be`
- source_refs:
  - `context/rules.md#L426`
  - `context/rules.md#L426`

#### 结构化事实

- business_definition: 将行业协会公布的机构名称映射到我司内部渠道名称。
- use_cases: 行业数据分析、对标分析。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: `DWMS_8_DIM_AGENCY_INFO`
- related_dictionary: `机构别名映射 (Agency Alias Mapping)`

#### 原始事实摘录

* **业务定义**: 将行业协会公布的机构名称映射到我司内部渠道名称。
* **适用场景**: 行业数据分析、对标分析。
* **核心原则**: **取交集 (Intersection Only)**。行业表有但内部渠道表(DWMS_8_DIM_AGENCY_INFO)没有的机构，视为未合作，直接忽略。
* **匹配逻辑**:
  1. **预处理**: 去除 "中国" 前缀，去除 "股份有限公司", "有限公司" 等后缀，去除括号内容。
  2. **关键字匹配**: 优先匹配 `dictionary.md` 中的 [机构别名映射] 表。
  3. **模糊匹配**: 
     * 如果清洗后的名称包含 "证券" 且在我司渠道表中存在，直接匹配。
     * 如果清洗后的名称包含 "银行" 且在我司渠道表中存在，直接匹配。

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
