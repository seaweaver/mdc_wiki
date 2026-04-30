---
title: "中国共同基金业绩表现｜ChinaMFPerformance"
aliases: ["中国共同基金业绩表现", "ChinaMFPerformance", "qudaojiankong:ChinaMFPerformance", "Wind收益率直取"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/基金, 数据技术/表, 数据技术/Wind, 治理状态/生效]
keywords: ["ChinaMFPerformance", "qudaojiankong", "F_AVGRETURN_YEAR", "F_ANNUALYEILD", "WIND2_CHINAMFPERFORMANCE", "收益率"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 中国共同基金业绩表现｜ChinaMFPerformance

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`STAGE.WIND2_CHINAMFPERFORMANCE`
- 业务名称：Wind 直取收益率数据
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:ChinaMFPerformance
- canonical_key: ChinaMFPerformance
- table_name: ChinaMFPerformance
- object_name: 中国共同基金业绩表现
- domain: Wind 源表
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `5e5617c9e6cda1d8`
- source_refs: `context/tables.md#L214`

### 结构化事实

- business_role: Wind 直取的基金收益率数据，作为净值自算收益率的补充数据源
- key_fields: `S_INFO_WINDCODE`, `TRADE_DT`
- preset_join_paths: 取最新一期业绩，按 TRADE_DT DESC ROW_NUMBER 取 RN=1
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `STAGE.WIND2_CHINAMFPERFORMANCE`
* **主键**: `S_INFO_WINDCODE` + `TRADE_DT`
* **说明**: 基金业绩表现，Wind 直取的收益率数据
* **核心字段**:
  * `S_INFO_WINDCODE`: 基金 Wind 代码
  * `TRADE_DT`: 交易日期 (YYYYMMDD)
  * `F_AVGRETURN_YEAR`: 近1年平均收益率
  * `F_AVGRETURN_TWOYEA`: 近2年平均收益率
  * `F_AVGRETURN_THREEYEAR`: 近3年平均收益率
  * `F_ANNUALYEILD`: 近1年年化收益率
* **预设关联路径**:
  > **取最新一期业绩**:
  ```sql
  LEFT JOIN (SELECT S_INFO_WINDCODE, ...,
             ROW_NUMBER() OVER (PARTITION BY S_INFO_WINDCODE ORDER BY TRADE_DT DESC) AS RN
             FROM STAGE.WIND2_CHINAMFPERFORMANCE
             WHERE TRADE_DT <= v_buss_date_8) P ON P.S_INFO_WINDCODE = ... AND P.RN = 1
  ```

---

## 关联

被 `[[rules/收益与胜率计算]]`（R08 收益率计算 Wind直取部分）消费。

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`5e5617c9e6cda1d8`
- 本页由知识快照导入生成，事实边界以快照为准。
