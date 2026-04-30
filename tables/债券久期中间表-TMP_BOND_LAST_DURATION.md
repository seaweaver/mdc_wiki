---
title: "债券久期中间表｜TMP_BOND_LAST_DURATION"
aliases: ["债券久期中间表", "TMP_BOND_LAST_DURATION", "qudaojiankong:TMP_BOND_LAST_DURATION", "久期中间表"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/债券, 数据技术/表, 数据技术/Oracle, 治理状态/生效]
keywords: ["久期", "TMP_BOND_LAST_DURATION", "qudaojiankong", "CJHX_DWMS", "组合久期", "B_ANAL_DURATION", "债券持仓"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 债券久期中间表｜TMP_BOND_LAST_DURATION

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`CJHX_DWMS.TMP_BOND_LAST_DURATION`
- 业务名称：债券久期中间表
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:TMP_BOND_LAST_DURATION
- canonical_key: TMP_BOND_LAST_DURATION
- table_name: TMP_BOND_LAST_DURATION
- object_name: 债券久期中间表
- domain: 未分类
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `2cfab308e5fdcd27`
- source_refs: `context/tables.md#L134`

### 结构化事实

- business_role: 组合久期计算的关键中间表，每次跑批先 DELETE 全表再 INSERT
- key_fields: 未显式说明
- preset_join_paths: 来自最新季报的债券持仓 + CBondValuation 久期
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `CJHX_DWMS.TMP_BOND_LAST_DURATION`
* **说明**: 组合久期计算的关键中间表。每次跑批先 DELETE 全表再 INSERT。来自最新季报的债券持仓 + CBondValuation 久期
* **核心字段**:
  * `FUND_CODE`: 基金代码
  * `RPT_ENDDATE`: 报告截止日期
  * `BOND_CODE`: 债券代码
  * `DURATION`: 久期 (取自 `B_ANAL_DURATION`)

---

## 关联

- 上游：`[[tables/中国共同基金投资组合持券明细-ChinaMutualFundBondPortfolio]]`（债券持仓）+ `[[tables/中国债券衍生指标-CBondValuation]]`（单券久期）
- 下游：被 `[[rules/仓位久期与期限结构]]`（R20 组合久期计算）消费

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`2cfab308e5fdcd27`
- 本页由知识快照导入生成，事实边界以快照为准。
