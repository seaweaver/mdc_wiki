---
title: "8倍镜_整体日统计结果表｜dwms_v_8_day_all_hive"
aliases: ["8倍镜_整体日统计结果表", "dwms_v_8_day_all_hive", "data_project:dwms_v_8_day_all_hive", "8倍镜_整体日统计结果表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/财务, 业务动作/统计, 数据技术/表, 数据技术/字段, 数据技术/大数据平台, 治理状态/生效]
keywords: ["8倍镜_整体日统计结果表", "dwms_v_8_day_all_hive", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 8倍镜_整体日统计结果表｜dwms_v_8_day_all_hive

## 概览

- 来源项目：`data_project`
- 物理表名：`dwms_v_8_day_all_hive`
- 业务名称：8倍镜_整体日统计结果表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:dwms_v_8_day_all_hive
- canonical_key: dwms_v_8_day_all_hive
- table_name: dwms_v_8_day_all_hive
- object_name: 8倍镜_整体日统计结果表
- domain: 七、8倍镜统计表
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `7f988dd22e829cd0`
- source_refs: `context/tables.md#L525`

#### 结构化事实

- business_role: 反映零售线整体财务考核口径的日统计数据。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名 (Oracle库)**: `CJHX_DWMS.dwms_v_8_day_all_hive`
* **业务用途**: 反映零售线整体财务考核口径的日统计数据。
* **核心字段**:
  * `CJDT`: 交易确认日期 (VARCHAR2(20))
  * `TOTALUSERS`: 累计客户数
  * `FEE`: 总管理费收入
  * `USERS`: 存量用户数
  * `SHARES`: 存量总份额
  * `AMOUNT`: 存量总金额
  * `BUY_USERS`: 申购用户数
  * `BUY_SHARES`: 申购总份额
  * `BUY_AMOUNT`: 申购总金额
  * `SELL_USERS`: 赎回用户数
  * `SELL_SHARES`: 赎回总份额
  * `SELL_AMOUNT`: 赎回总金额
  * `AUTOSHARES`: 定投总份额
  * `AUTOAMOUNT`: 定投总金额

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
