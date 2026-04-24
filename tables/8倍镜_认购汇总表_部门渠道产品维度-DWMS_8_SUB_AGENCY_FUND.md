---
title: "8倍镜_认购汇总表_部门渠道产品维度｜DWMS_8_SUB_AGENCY_FUND"
aliases: ["8倍镜_认购汇总表_部门渠道产品维度", "DWMS_8_SUB_AGENCY_FUND", "data_project:DWMS_8_SUB_AGENCY_FUND", "8倍镜_认购汇总表_部门渠道产品维度表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/交易, 业务域/组织, 业务域/渠道, 业务域/产品, 业务域/财务, 业务动作/认购, 治理状态/生效]
keywords: ["8倍镜_认购汇总表_部门渠道产品维度", "DWMS_8_SUB_AGENCY_FUND", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 8倍镜_认购汇总表_部门渠道产品维度｜DWMS_8_SUB_AGENCY_FUND

## 概览

- 来源项目：`data_project`
- 物理表名：`DWMS_8_SUB_AGENCY_FUND`
- 业务名称：8倍镜_认购汇总表_部门渠道产品维度
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:DWMS_8_SUB_AGENCY_FUND
- canonical_key: DWMS_8_SUB_AGENCY_FUND
- table_name: DWMS_8_SUB_AGENCY_FUND
- object_name: 8倍镜_认购汇总表_部门渠道产品维度
- domain: 七、8倍镜统计表
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `3a64781b15164890`
- source_refs: `context/tables.md#L656`

#### 结构化事实

- business_role: 存储按部门、渠道、产品维度汇总的认购数据，用于认购业绩统计分析。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: `交易类型 (ta_trd_mode_code)`, `部门代码/部门名称 (AGENCYBELONG)`

#### 原始事实摘录

* **物理表名 (Oracle库)**: `CJHX_DWMS.DWMS_8_SUB_AGENCY_FUND`
* **业务用途**: 存储按部门、渠道、产品维度汇总的认购数据，用于认购业绩统计分析。
* **核心字段**:
  * `CJDT`: 交易确认日期（格式: YYYYMMDD）
  * `AGENCYBELONG`: 部门代码/部门名称
  * `AGENCYNAME`: 渠道名称
  * `FUNDCODE`: 基金代码
  * `FUNDNAME`: 基金名称
  * `SUBSCRIBE_AMOUNT`: 认购金额（当日认购金额汇总）
* **预设关联路径 (Relationships)**:
  * **按时间范围统计认购数据**: `WHERE cjdt >= '{start_date}' AND cjdt <= '{end_date}'`
  * **按部门过滤**: `WHERE AGENCYBELONG = '{dept_code_or_name}'`
  * **按渠道过滤**: `WHERE AGENCYNAME = '{channel_name}'`
  * **统计认购金额**: `SUM(SUBSCRIBE_AMOUNT)`
* **注意事项**: 
  * 该表已按部门、渠道、产品、日期维度预聚合，直接查询即可
  * 认购金额仅包含认购交易（不含申购、赎回等其他交易类型）
  * `AGENCYBELONG` 字段存储的是部门名称（如：银行、券商 等）

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
