---
title: "内部产品维表(分级)｜V5_DIM_PRODUCT"
aliases: ["内部产品维表(分级)", "V5_DIM_PRODUCT", "qudaojiankong:V5_DIM_PRODUCT", "分级产品维度表"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/基金, 数据技术/表, 数据技术/Oracle, 治理状态/生效]
keywords: ["V5_DIM_PRODUCT", "qudaojiankong", "CJHX_DW", "分级产品", "BK_PRODUCT", "内部产品维表"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 内部产品维表(分级)｜V5_DIM_PRODUCT

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`CJHX_DW.V5_DIM_PRODUCT`
- 业务名称：分级产品的内部维度表
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:V5_DIM_PRODUCT
- canonical_key: V5_DIM_PRODUCT
- table_name: V5_DIM_PRODUCT
- object_name: 内部产品维表(分级)
- domain: Oracle 内部源表
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `744e5d96c274ce41`
- source_refs: `context/tables.md#L321`

### 结构化事实

- business_role: 分级产品的内部维度表，提供产品全称等基础信息
- key_fields: 未显式说明
- preset_join_paths: 见下方
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `CJHX_DW.V5_DIM_PRODUCT`
* **说明**: 分级产品的内部维度表
* **核心字段**:
  * `BK_PRODUCT`: 内部产品代码
  * `PRODUCT_FULLNAME`: 产品全称

---

## 相关页面

- 配套表：`[[tables/内部产品维表-非分级-V6_DIM_PRODUCT]]`（非分级产品维度表）
- 产品映射：`[[tables/产品维表-组合映射-V2_DIM_PRODUCT]]`

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`744e5d96c274ce41`
- 本页由知识快照导入生成，事实边界以快照为准。
