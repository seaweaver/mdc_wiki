---
title: "交易日历｜MD_PUB_DATE_INFO"
aliases: ["交易日历", "MD_PUB_DATE_INFO", "qudaojiankong:MD_PUB_DATE_INFO", "系统交易日历"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/运营, 数据技术/表, 数据技术/Oracle, 治理状态/生效]
keywords: ["MD_PUB_DATE_INFO", "qudaojiankong", "STAGE", "L_DATE", "C_TRADE_DATE", "交易日历"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 交易日历｜MD_PUB_DATE_INFO

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`STAGE.MD_PUB_DATE_INFO`
- 业务名称：系统交易日历
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:MD_PUB_DATE_INFO
- canonical_key: MD_PUB_DATE_INFO
- table_name: MD_PUB_DATE_INFO
- object_name: 交易日历
- domain: Oracle 内部源表
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `b16caa3d53961d1b`
- source_refs: `context/tables.md#L392`

### 结构化事实

- business_role: 系统交易日历，用于确定跑批基准日期和最近交易日
- key_fields: 未显式说明
- preset_join_paths: 见下方
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `STAGE.MD_PUB_DATE_INFO`
* **说明**: 系统交易日历
* **核心字段**:
  * `L_DATE`: 日期
  * `C_TRADE_DATE`: 是否交易日
  * `C_DATE_TYPE`: 日期类型

---

## 关联

被 `[[rules/基础参数与过滤]]`（R01 业务日期与数据窗口）消费。

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`b16caa3d53961d1b`
- 本页由知识快照导入生成，事实边界以快照为准。
