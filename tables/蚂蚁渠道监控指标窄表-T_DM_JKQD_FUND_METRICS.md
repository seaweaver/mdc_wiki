---
title: "蚂蚁渠道监控指标窄表｜T_DM_JKQD_FUND_METRICS"
aliases: ["窄表", "T_DM_JKQD_FUND_METRICS", "qudaojiankong:T_DM_JKQD_FUND_METRICS", "中间工作表"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/渠道, 业务动作/监控, 资产类型/基金, 数据技术/表, 数据技术/Oracle, 治理状态/生效]
keywords: ["窄表", "T_DM_JKQD_FUND_METRICS", "qudaojiankong", "CJHX_DWMS", "蚂蚁渠道", "中间工作表"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 蚂蚁渠道监控指标窄表｜T_DM_JKQD_FUND_METRICS

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`CJHX_DWMS.T_DM_JKQD_FUND_METRICS`
- 业务名称：中间工作表（窄表）
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:T_DM_JKQD_FUND_METRICS
- canonical_key: T_DM_JKQD_FUND_METRICS
- table_name: T_DM_JKQD_FUND_METRICS
- object_name: 窄表
- domain: 未分类
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `d686416b7699e0fe`
- source_refs: `context/tables.md#L116`

### 结构化事实

- business_role: 中间工作表，13 个 INSERT 步骤写入，每个步骤写入部分字段，随后分批 MERGE 到宽表
- key_fields: `PRODUCT_CODE`, `DATA_DATE`
- preset_join_paths: 最终按 PRODUCT_CODE 聚合
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `CJHX_DWMS.T_DM_JKQD_FUND_METRICS`
* **主键**: `PRODUCT_CODE` + `DATA_DATE`
* **说明**: 窄表/中间工作表，13 个 INSERT 步骤写入，随后分批 MERGE 到宽表。每个步骤写入部分字段，最终按 PRODUCT_CODE 聚合
* **数据生命周期**: 保留最近 30 天数据，每次跑批先 DELETE 当前日期及过期数据

---

## 加工流程

从基金池入口表 `[[tables/基金池入口表-TMP_JKQD_FUND_METRICS]]` 及各 Wind/内部源表取数，分 13 个步骤 INSERT：

| 步骤 | 内容 | 关联规则 |
|------|------|----------|
| 步骤1 | 产品信息（成立时长、规模） | R03, R04 |
| 步骤2 | 同基金经理产品 | R05 |
| 步骤3 | 投资年限与公募经验 | R06 |
| 步骤4 | 月度/季度/年度胜率 | R07 |
| 步骤5 | 收益率计算 | R08 |
| 步骤6 | 跑赢货币指数概率 | R09, R10 |
| 步骤7 | 同类排名（超额收益） | R11 |
| 步骤8 | 持有期正收益概率 | R12 |
| 步骤9 | 同类排名（正收益） | R13 |
| 步骤10 | 回撤指标 | R14, R15, R16 |
| 步骤11 | 仓位、久期 | R17, R18, R19, R20 |
| 步骤12 | 持有期/封闭期类型 | R21 |
| 步骤13 | 封闭期正收益概率 | R22 |

最终通过 6 个 MERGE 批次聚合到宽表 `[[tables/蚂蚁渠道监控指标宽表-DM_JKQD_FUND_METRICS]]`。

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`d686416b7699e0fe`
- 本页由知识快照导入生成，事实边界以快照为准。
