---
title: "非分级组合规模口径｜A025_KB_ZTBH_SUM"
aliases: ["非分级组合规模口径", "A025_KB_ZTBH_SUM", "qudaojiankong:A025_KB_ZTBH_SUM", "非分级组合规模"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/组合, 数据技术/表, 数据技术/Oracle, 治理状态/生效]
keywords: ["A025_KB_ZTBH_SUM", "qudaojiankong", "CJHX_DW", "非分级组合规模", "S_ZTBH", "AA0001", "我司口径"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 非分级组合规模口径｜A025_KB_ZTBH_SUM

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`CJHX_DW.A025_KB_ZTBH_SUM`
- 业务名称：非分级组合规模汇总
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:A025_KB_ZTBH_SUM
- canonical_key: A025_KB_ZTBH_SUM
- table_name: A025_KB_ZTBH_SUM
- object_name: 非分级组合规模口径
- domain: Oracle 内部源表
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `143eee584d18a893`
- source_refs: `context/tables.md#L351`

### 结构化事实

- business_role: 非分级组合规模汇总，用于计算 FUND_TOTAL_SCALE_CJHX（我司口径规模）
- key_fields: 未显式说明
- preset_join_paths: 见下方
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `CJHX_DW.A025_KB_ZTBH_SUM`
* **说明**: 非分级组合规模汇总
* **核心字段**:
  * `S_ZTBH`: 组合编号
  * `AA0001`: 规模指标值
  * `DATA_DATE`: 数据日期

---

## 关联

被 `[[rules/产品信息与规模]]`（R04 基金规模计算 我司口径）消费。
配套表：`[[tables/分级产品规模口径-V_VW_073_FJCP]]`

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`143eee584d18a893`
- 本页由知识快照导入生成，事实边界以快照为准。
