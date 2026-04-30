---
title: "持有期封闭期配置｜MD_PROD_CXQ_CFG"
aliases: ["持有期/封闭期配置", "MD_PROD_CXQ_CFG", "qudaojiankong:MD_PROD_CXQ_CFG", "持有期配置表"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/基金, 数据技术/表, 数据技术/Oracle, 治理状态/生效]
keywords: ["MD_PROD_CXQ_CFG", "qudaojiankong", "CJHX_SMI", "FUND_HOLD_PERIOD", "持有期", "UPPER_BK_PRODUCT"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 持有期封闭期配置｜MD_PROD_CXQ_CFG

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`CJHX_SMI.MD_PROD_CXQ_CFG`
- 业务名称：持有期/封闭期配置表
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:MD_PROD_CXQ_CFG
- canonical_key: MD_PROD_CXQ_CFG
- table_name: MD_PROD_CXQ_CFG
- object_name: 持有期/封闭期配置
- domain: Oracle 内部源表
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `d0c6a0bc16b47f99`
- source_refs: `context/tables.md#L373`

### 结构化事实

- business_role: 持有人持有期配置，用于判定 HOLD_PERIOD_TYPE
- key_fields: 未显式说明
- preset_join_paths: 见下方
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `CJHX_SMI.MD_PROD_CXQ_CFG`
* **核心字段**:
  * `UPPER_BK_PRODUCT`: 产品代码
  * `FUND_HOLD_PERIOD`: 基金持有期

---

## 关联

被 `[[rules/仓位久期与期限结构]]`（R21 持有期类型）消费。
配套表：`[[tables/PLMS-基金竖表字段-PLMS2_TFUNDINFOVERTICAL]]`（封闭期数据）、`[[tables/PLMS-公募基金信息-PLMS2_TPDTFUNDINFO]]`

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`d0c6a0bc16b47f99`
- 本页由知识快照导入生成，事实边界以快照为准。
