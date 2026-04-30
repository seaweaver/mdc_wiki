---
title: "中国共同基金滚动运作周期｜CMFundOperatePeriod"
aliases: ["中国共同基金滚动运作周期", "CMFundOperatePeriod", "qudaojiankong:CMFundOperatePeriod", "封闭运作周期"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/基金, 数据技术/表, 数据技术/Wind, 治理状态/生效]
keywords: ["CMFundOperatePeriod", "qudaojiankong", "OPR_STARTDT", "OPR_ENDDT", "WIND2_CMFUNDOPERATEPERIOD", "封闭期"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 中国共同基金滚动运作周期｜CMFundOperatePeriod

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`STAGE.WIND2_CMFUNDOPERATEPERIOD`
- 业务名称：基金封闭运作周期数据
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:CMFundOperatePeriod
- canonical_key: CMFundOperatePeriod
- table_name: CMFundOperatePeriod
- object_name: 中国共同基金滚动运作周期
- domain: Wind 源表
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `b83b33b546615652`
- source_refs: `context/tables.md#L284`

### 结构化事实

- business_role: 基金封闭运作周期数据，用于封闭期正收益概率计算
- key_fields: `S_INFO_WINDCODE`, `OPR_PERIOD`, `BATCH1`
- preset_join_paths: 取近3年封闭期记录
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `STAGE.WIND2_CMFUNDOPERATEPERIOD`
* **主键**: `S_INFO_WINDCODE` + `OPR_PERIOD` + `BATCH1`
* **说明**: 基金封闭运作周期数据
* **核心字段**:
  * `S_INFO_WINDCODE`: 基金 Wind 代码
  * `OPR_PERIOD`: 期数
  * `BATCH1`: 批次
  * `OPR_STARTDT`: 封闭期起始日 (YYYYMMDD)
  * `OPR_ENDDT`: 封闭期结束日 (YYYYMMDD)
* **预设关联路径**:
  > **取近3年封闭期记录**:
  ```sql
  WHERE OPR_ENDDT >= TO_CHAR(ADD_MONTHS(TRUNC(TO_DATE(v_buss_date_8, 'yyyymmdd')), -36), 'YYYYMMDD')
    AND OPR_ENDDT <= v_buss_date_8
  ```

---

## 关联

被 `[[rules/封闭期与聚合规则]]`（R22 封闭期正收益概率）消费。

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`b83b33b546615652`
- 本页由知识快照导入生成，事实边界以快照为准。
