---
title: "中国债券衍生指标｜CBondValuation"
aliases: ["中国债券衍生指标", "CBondValuation", "qudaojiankong:CBondValuation", "债券久期"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/债券, 数据技术/表, 数据技术/Wind, 治理状态/生效]
keywords: ["CBondValuation", "qudaojiankong", "B_ANAL_DURATION", "WIND2_CBONDVALUATION", "分析久期", "债券衍生指标"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 中国债券衍生指标｜CBondValuation

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`STAGE.WIND2_CBONDVALUATION`
- 业务名称：债券风险收益率指标，包含久期数据
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:CBondValuation
- canonical_key: CBondValuation
- table_name: CBondValuation
- object_name: 中国债券衍生指标
- domain: Wind 源表
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `9284009e22c92081`
- source_refs: `context/tables.md#L267`

### 结构化事实

- business_role: 债券风险收益率指标，包含久期数据，用于组合久期计算
- key_fields: `S_INFO_WINDCODE`, `TRADE_DT`
- preset_join_paths: 取季报末最近估值久期(15天窗口)
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `STAGE.WIND2_CBONDVALUATION`
* **主键**: `S_INFO_WINDCODE` + `TRADE_DT`
* **说明**: 债券风险收益率指标，包含久期数据
* **核心字段**:
  * `S_INFO_WINDCODE`: 债券 Wind 代码
  * `TRADE_DT`: 交易日期 (YYYYMMDD)
  * `B_ANAL_DURATION`: 分析久期 — 用于组合久期计算
* **预设关联路径**:
  > **取季报末最近估值久期(15天窗口)**:
  ```sql
  LEFT JOIN STAGE.WIND2_CBONDVALUATION V
    ON V.S_INFO_WINDCODE = B.S_INFO_BONDWINDCODE
   AND V.TRADE_DT <= B.F_PRT_ENDDATE
   AND V.TRADE_DT >= TO_CHAR(TO_DATE(B.F_PRT_ENDDATE, 'YYYYMMDD') - 15, 'YYYYMMDD')
  ```

---

## 关联

- 下游：与 `[[tables/中国共同基金投资组合持券明细-ChinaMutualFundBondPortfolio]]` 结合，写入 `[[tables/债券久期中间表-TMP_BOND_LAST_DURATION]]`
- 被 `[[rules/仓位久期与期限结构]]`（R20 组合久期计算）消费

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`9284009e22c92081`
- 本页由知识快照导入生成，事实边界以快照为准。
