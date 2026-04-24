---
title: "8倍镜_管理费自然日统计表｜DWMS_8_DAY_FEE_H"
aliases: ["8倍镜_管理费自然日统计表", "DWMS_8_DAY_FEE_H", "data_project:DWMS_8_DAY_FEE_H", "8倍镜_管理费自然日统计表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/财务, 业务动作/考核, 业务动作/统计, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["8倍镜_管理费自然日统计表", "DWMS_8_DAY_FEE_H", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 8倍镜_管理费自然日统计表｜DWMS_8_DAY_FEE_H

## 概览

- 来源项目：`data_project`
- 物理表名：`DWMS_8_DAY_FEE_H`
- 业务名称：8倍镜_管理费自然日统计表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:DWMS_8_DAY_FEE_H
- canonical_key: DWMS_8_DAY_FEE_H
- table_name: DWMS_8_DAY_FEE_H
- object_name: 8倍镜_管理费自然日统计表
- domain: 七、8倍镜统计表
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `e2b76c9e6cd10619`
- source_refs: `context/tables.md#L678`

#### 结构化事实

- business_role: 存储按自然日统计的管理费数据，用于管理费汇总和分析。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: `部门代码/部门名称 (AGENCYBELONG)`

#### 原始事实摘录

* **物理表名 (Oracle库)**: `CJHX_DWMS.DWMS_8_DAY_FEE_H`
* **业务用途**: 存储按自然日统计的管理费数据，用于管理费汇总和分析。
* **⚠️ 重要说明**: 
  * **该表按自然日存储**，因为管理费在自然日也有数据
  * **其他8倍镜表按交易日存储**，仅在交易日有数据
  * 做管理费汇总和分析时，应优先使用该表
* **核心字段**:
  * `CJDT`: 数据日期（格式: YYYYMMDD，⚠️ 自然日，非交易日）
  * `AGENCYBELONG`: 部门名称（如：银行、券商、网金）
  * `AGENCYNAME`: 渠道名称
  * `FUNDCODE`: 基金代码
  * `FEE`: 管理费收入
* **预设关联路径 (Relationships)**:
  * **按时间范围统计管理费**: `WHERE CJDT >= '{start_date}' AND CJDT <= '{end_date}'`
  * **按部门过滤**: `WHERE AGENCYBELONG = '{dept_name}'` (如: '券商', '银行', '网金')
  * **按渠道过滤**: `WHERE AGENCYNAME = '{channel_name}'`
  * **统计管理费**: `SUM(NVL(FEE, 0))`
* **注意事项**: 
  * 该表已按部门、渠道、产品、日期维度预聚合
  * 日期维度为自然日（包含周末和节假日），与其他8倍镜表（交易日）不同
  * 聚合时需使用 NVL 处理 NULL 值

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
