---
title: "机构类型分类｜R_Inst_Class"
aliases: ["机构类型分类", "R_Inst_Class", "data_project:R_Inst_Class", "Institution Classification"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/组织, 业务动作/校验, 业务动作/分类, 治理状态/生效]
keywords: ["机构类型分类", "R_Inst_Class", "Institution Classification", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 机构类型分类｜R_Inst_Class

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Inst_Class`
- 英文锚点：`Institution Classification`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:R_Inst_Class
- canonical_key: R_Inst_Class
- rule_id: R_Inst_Class
- rule_name: 机构类型分类 (Institution Classification)
- status: project-only
- change_type: unchanged
- content_hash: `916ccd45815ebfbf`
- source_refs:
  - `context/rules.md#L402`
  - `context/rules.md#L402`

#### 结构化事实

- business_definition: 根据渠道名称将机构分类为“券商”或“城农商行”。
- use_cases: 销量统计中区分机构类型。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: 无显式命中
- related_dictionary: `机构类型 (inst_type) - 券商渠道部专用`

#### 原始事实摘录

* **业务定义**: 根据渠道名称将机构分类为“券商”或“城农商行”。
* **适用场景**: 销量统计中区分机构类型。
* **SQL 逻辑模板**:
  ```sql
  CASE 
      WHEN qdmc LIKE '%证券%' THEN '券商'
      WHEN qdmc LIKE '%农商%' OR qdmc LIKE '%城商%' OR qdmc LIKE '%农村合作%' OR qdmc LIKE '%村镇银行%' THEN '城农商行'
      ELSE '其他'
  END
  ```

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
