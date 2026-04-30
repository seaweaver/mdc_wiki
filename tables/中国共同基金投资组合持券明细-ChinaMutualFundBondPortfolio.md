---
title: "中国共同基金投资组合持券明细｜ChinaMutualFundBondPortfolio"
aliases: ["中国共同基金投资组合—持券明细", "ChinaMutualFundBondPortfolio", "qudaojiankong:ChinaMutualFundBondPortfolio", "债券持仓明细"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/债券, 资产类型/基金, 数据技术/表, 数据技术/Wind, 治理状态/生效]
keywords: ["ChinaMutualFundBondPortfolio", "qudaojiankong", "F_PRT_BDVALUE", "WIND2_CHINAMUTUALFUNDBONDPORTF", "债券市值", "季报持仓"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 中国共同基金投资组合持券明细｜ChinaMutualFundBondPortfolio

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`STAGE.WIND2_CHINAMUTUALFUNDBONDPORTF`
- 业务名称：基金定期(季度)公布的债券持仓明细
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:ChinaMutualFundBondPortfolio
- canonical_key: ChinaMutualFundBondPortfolio
- table_name: ChinaMutualFundBondPortfolio
- object_name: 中国共同基金投资组合—持券明细
- domain: Wind 源表
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `49b2decfb80860b3`
- source_refs: `context/tables.md#L251`

### 结构化事实

- business_role: 基金定期(季度)公布的债券持仓明细，用于组合久期加权计算
- key_fields: `S_INFO_WINDCODE`, `F_PRT_ENDDATE`, `S_INFO_BONDWINDCODE`
- preset_join_paths: 取最新季报持仓，F_PRT_ENDDATE 的 MMDD 必须为季报截止日
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `STAGE.WIND2_CHINAMUTUALFUNDBONDPORTF`
* **主键**: `S_INFO_WINDCODE` + `F_PRT_ENDDATE` + `S_INFO_BONDWINDCODE`
* **说明**: 基金定期(季度)公布的债券持仓明细
* **核心字段**:
  * `S_INFO_WINDCODE`: 基金 Wind 代码
  * `F_PRT_ENDDATE`: 报告截止日期 (YYYYMMDD)
  * `S_INFO_BONDWINDCODE`: 持有债券 Wind 代码
  * `F_PRT_BDVALUE`: 债券市值(元) — 用于组合久期加权
* **预设关联路径**:
  > **取最新季报持仓**:
  ```sql
  WHERE F_PRT_ENDDATE <= v_buss_date_8
    AND SUBSTR(F_PRT_ENDDATE, 5, 4) IN ('0331','0630','0930','1231')
  ```

---

## 关联

- 下游：与 `[[tables/中国债券衍生指标-CBondValuation]]` 结合，写入 `[[tables/债券久期中间表-TMP_BOND_LAST_DURATION]]`
- 被 `[[rules/仓位久期与期限结构]]`（R20 组合久期计算）消费

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`49b2decfb80860b3`
- 本页由知识快照导入生成，事实边界以快照为准。
