---
title: "PLMS-公募基金信息｜PLMS2_TPDTFUNDINFO"
aliases: ["PLMS-公募基金信息", "PLMS2_TPDTFUNDINFO", "qudaojiankong:PLMS2_TPDTFUNDINFO", "PLMS公募基金"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/基金, 数据技术/表, 数据技术/Oracle, 治理状态/生效]
keywords: ["PLMS2_TPDTFUNDINFO", "qudaojiankong", "STAGE", "C_FUNDCODE", "C_TAFUNDCODE", "PLMS"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# PLMS-公募基金信息｜PLMS2_TPDTFUNDINFO

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`STAGE.PLMS2_TPDTFUNDINFO`
- 业务名称：PLMS 系统公募基金信息
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:PLMS2_TPDTFUNDINFO
- canonical_key: PLMS2_TPDTFUNDINFO
- table_name: PLMS2_TPDTFUNDINFO
- object_name: PLMS-公募基金信息
- domain: Oracle 内部源表
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `6a2ed99b56e42904`
- source_refs: `context/tables.md#L379`

### 结构化事实

- business_role: PLMS 系统的公募基金信息表，提供基金代码到 TA 基金代码的映射
- key_fields: 未显式说明
- preset_join_paths: 见下方
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `STAGE.PLMS2_TPDTFUNDINFO`
* **核心字段**:
  * `C_FUNDCODE`: 基金代码
  * `C_TAFUNDCODE`: TA基金代码 (即 PRODUCT_CODE)

---

## 关联

与 `[[tables/PLMS-基金竖表字段-PLMS2_TFUNDINFOVERTICAL]]` 联表取封闭期数据。
被 `[[rules/仓位久期与期限结构]]`（R21 持有期类型）消费。

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`6a2ed99b56e42904`
- 本页由知识快照导入生成，事实边界以快照为准。
