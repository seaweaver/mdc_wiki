---
title: "产品维表(组合映射)｜V2_DIM_PRODUCT"
aliases: ["产品维表(组合映射)", "V2_DIM_PRODUCT", "qudaojiankong:V2_DIM_PRODUCT", "组合映射表"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/组合, 数据技术/表, 数据技术/Oracle, 治理状态/生效]
keywords: ["V2_DIM_PRODUCT", "qudaojiankong", "CJHX_DW", "BK_PORTFOLIO", "组合映射", "持有期"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 产品维表(组合映射)｜V2_DIM_PRODUCT

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`CJHX_DW.V2_DIM_PRODUCT`（也引用 `DW.V2_DIM_PRODUCT`）
- 业务名称：产品与组合的映射表，用于持有期/封闭期从组合反查产品代码
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:V2_DIM_PRODUCT
- canonical_key: V2_DIM_PRODUCT
- table_name: V2_DIM_PRODUCT
- object_name: 产品维表(组合映射)
- domain: Oracle 内部源表
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `db9df9bddd011211`
- source_refs: `context/tables.md#L336`

### 结构化事实

- business_role: 产品与组合的映射表，用于持有期/封闭期从组合反查产品代码
- key_fields: 未显式说明
- preset_join_paths: 见下方
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `CJHX_DW.V2_DIM_PRODUCT`（也引用 `DW.V2_DIM_PRODUCT`）
* **说明**: 产品与组合的映射表，用于持有期/封闭期从组合反查产品代码
* **核心字段**:
  * `BK_PRODUCT`: 内部产品代码
  * `BK_PORTFOLIO`: 组合编号

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`db9df9bddd011211`
- 本页由知识快照导入生成，事实边界以快照为准。
