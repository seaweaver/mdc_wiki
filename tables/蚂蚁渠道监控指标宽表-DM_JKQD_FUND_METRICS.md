---
title: "蚂蚁渠道监控指标宽表｜DM_JKQD_FUND_METRICS"
aliases: ["目标宽表", "DM_JKQD_FUND_METRICS", "qudaojiankong:DM_JKQD_FUND_METRICS", "蚂蚁渠道监控指标结果表"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/渠道, 业务动作/监控, 资产类型/基金, 数据技术/表, 数据技术/Oracle, 治理状态/生效]
keywords: ["目标宽表", "DM_JKQD_FUND_METRICS", "qudaojiankong", "CJHX_DWMS", "蚂蚁渠道", "监控指标", "结果表"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 蚂蚁渠道监控指标宽表｜DM_JKQD_FUND_METRICS

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`CJHX_DWMS.DM_JKQD_FUND_METRICS`
- 业务名称：蚂蚁渠道监控指标结果表
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:DM_JKQD_FUND_METRICS
- canonical_key: DM_JKQD_FUND_METRICS
- table_name: DM_JKQD_FUND_METRICS
- object_name: 目标宽表
- domain: 未分类
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `36544dab65f30c06`
- source_refs: `context/tables.md#L6`

### 结构化事实

- business_role: 渠道监控指标宽表，由窄表 `T_DM_JKQD_FUND_METRICS` 经 6 个 MERGE 批次聚合写入，最终对外输出
- key_fields: `PRODUCT_CODE`, `DATA_DATE`
- preset_join_paths: 窄表到宽表通过 PRODUCT_CODE + DATA_DATE 聚合，数值型字段用 SUM，字符串型字段用 MAX
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `CJHX_DWMS.DM_JKQD_FUND_METRICS`
* **主键**: `PRODUCT_CODE` + `DATA_DATE`
* **说明**: 渠道监控指标宽表，由窄表 `T_DM_JKQD_FUND_METRICS` 经 6 个 MERGE 批次聚合写入
* **字段总数**: 89
* **关联路径**:
  > 窄表到宽表通过 PRODUCT_CODE + DATA_DATE 聚合，数值型字段用 SUM，字符串型字段用 MAX。
  > 每个 MERGE 批次先 UPDATE 对应字段为默认值，再 MERGE INTO。

---

## 加工流程

1. 窄表 `[[tables/蚂蚁渠道监控指标窄表-T_DM_JKQD_FUND_METRICS]]` 通过 13 个 INSERT 步骤分批写入
2. 然后通过 6 个 MERGE 批次聚合约 89 个字段到宽表
3. 详见 `[[rules/封闭期与聚合规则]]`（R23 窄表→宽表 MERGE 聚合规则）

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`36544dab65f30c06`
- 本页由知识快照导入生成，事实边界以快照为准。
