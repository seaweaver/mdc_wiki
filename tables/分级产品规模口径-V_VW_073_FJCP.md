---
title: "分级产品规模口径｜V_VW_073_FJCP"
aliases: ["分级产品规模口径", "V_VW_073_FJCP", "qudaojiankong:V_VW_073_FJCP", "分级产品规模"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/基金, 数据技术/表, 数据技术/Oracle, 治理状态/生效]
keywords: ["V_VW_073_FJCP", "qudaojiankong", "CJHX_DSCL", "分级产品规模", "VC_FJCPDM", "我司口径"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 分级产品规模口径｜V_VW_073_FJCP

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`CJHX_DSCL.V_VW_073_FJCP`
- 业务名称：分级产品规模数据
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:V_VW_073_FJCP
- canonical_key: V_VW_073_FJCP
- table_name: V_VW_073_FJCP
- object_name: 分级产品规模口径
- domain: Oracle 内部源表
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `323533390c889279`
- source_refs: `context/tables.md#L343`

### 结构化事实

- business_role: 分级产品规模数据，用于计算 FUND_TOTAL_SCALE_CJHX（我司口径规模）
- key_fields: 未显式说明
- preset_join_paths: 见下方
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `CJHX_DSCL.V_VW_073_FJCP`
* **说明**: 分级产品规模数据
* **核心字段**:
  * `VC_FJCPDM`: 分级产品代码
  * `VC_0001`: 规模指标值
  * `D_YWRQ`: 业务日期

---

## 关联

被 `[[rules/产品信息与规模]]`（R04 基金规模计算 我司口径）消费。
配套表：`[[tables/非分级组合规模口径-A025_KB_ZTBH_SUM]]`

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`323533390c889279`
- 本页由知识快照导入生成，事实边界以快照为准。
