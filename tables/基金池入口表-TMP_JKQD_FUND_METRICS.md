---
title: "基金池入口表｜TMP_JKQD_FUND_METRICS"
aliases: ["基金池入口表", "TMP_JKQD_FUND_METRICS", "qudaojiankong:TMP_JKQD_FUND_METRICS", "基金池"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/渠道, 业务动作/过滤, 资产类型/基金, 数据技术/表, 数据技术/Oracle, 治理状态/生效]
keywords: ["基金池", "TMP_JKQD_FUND_METRICS", "qudaojiankong", "CJHX_DWMS", "S_FROM_PLACE", "蚂蚁渠道", "计算范围"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 基金池入口表｜TMP_JKQD_FUND_METRICS

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`CJHX_DWMS.TMP_JKQD_FUND_METRICS`
- 业务名称：基金池入口表
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 相关字典：`基金池标记 (S_FROM_PLACE)`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:TMP_JKQD_FUND_METRICS
- canonical_key: TMP_JKQD_FUND_METRICS
- table_name: TMP_JKQD_FUND_METRICS
- object_name: 基金池入口表
- domain: 未分类
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `155b8b5ea1bdeaa2`
- source_refs: `context/tables.md#L124`

### 结构化事实

- business_role: 控制哪些基金需要计算指标，多数 Wind 计算依赖 `S_FROM_PLACE = '1'` 进行过滤
- key_fields: `PRODUCT_CODE`
- preset_join_paths: 见下方
- related_dictionary: `基金池标记 (S_FROM_PLACE)`

### 原始事实摘录

* **物理表名**: `CJHX_DWMS.TMP_JKQD_FUND_METRICS`
* **主键**: `PRODUCT_CODE`
* **说明**: 基金池入口表，多数 Wind 计算依赖 `S_FROM_PLACE = '1'` 进行过滤。控制哪些基金需要计算指标
* **核心字段**:
  * `PRODUCT_CODE`: 产品代码 (Wind 代码格式: XXXXXX.OF)
  * `S_FROM_PLACE`: 来源标记 ('1' = 基金池有效)

---

## 关联规则

`S_FROM_PLACE = '1'` 是贯穿几乎所有计算步骤的核心过滤条件，详见 `[[rules/基础参数与过滤]]`（R02 基金池过滤）。

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`155b8b5ea1bdeaa2`
- 本页由知识快照导入生成，事实边界以快照为准。
