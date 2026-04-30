---
title: "中国共同基金净值｜CHINAMUTUALFUNDNAV"
aliases: ["中国共同基金净值", "CHINAMUTUALFUNDNAV", "data_project:CHINAMUTUALFUNDNAV", "qudaojiankong:ChinaMutualFundNAV", "中国共同基金净值表"]
created: 2026-04-24
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/基金, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["中国共同基金净值", "CHINAMUTUALFUNDNAV", "ChinaMutualFundNAV", "data_project", "qudaojiankong", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md", "raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---
# 中国共同基金净值｜CHINAMUTUALFUNDNAV

## 概览

- 来源项目：`data_project`
- 物理表名：`CHINAMUTUALFUNDNAV`
- 业务名称：中国共同基金净值
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:CHINAMUTUALFUNDNAV
- canonical_key: CHINAMUTUALFUNDNAV
- table_name: CHINAMUTUALFUNDNAV
- object_name: 中国共同基金净值
- domain: 十一、外部数据域 (Wind)
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `cd12e3a5f3581631`
- source_refs: `context/tables.md#L838`

#### 结构化事实

- business_role: 记录公募基金定期的单位净值与累计净值、复权净值等。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名 (Oracle库)**: `WIND.CHINAMUTUALFUNDNAV`
* **业务用途**: 记录公募基金定期的单位净值与累计净值、复权净值等。
* **业务主键**: `F_INFO_WINDCODE` (Wind代码), `PRICE_DATE` (截止日期)
* **核心字段**:
  * `F_INFO_WINDCODE`: Wind代码
  * `PRICE_DATE`: 截止日期 (格式: YYYYMMDD)
  * `F_NAV_UNIT`: 单位净值
  * `F_NAV_ACCUMULATED`: 累计净值
  * `F_NAV_ADJUSTED`: 复权单位净值

---

---

## qudaojiankong 项目使用

在"蚂蚁渠道基金产品提报监控"项目中，此表是**几乎所有指标计算的核心数据源**。

- 物理表名：`STAGE.WIND2_CHINAMUTUALFUNDNAV`（不同于 data_project 的 `WIND.CHINAMUTUALFUNDNAV`）
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 主键：`F_INFO_WINDCODE` + `PRICE_DATE`

### 核心字段

- `F_INFO_WINDCODE`: 基金 Wind 代码
- `PRICE_DATE`: 净值日期 (YYYYMMDD)
- `F_NAV_ADJUSTED`: 复权单位净值（优先使用）
- `F_NAV_UNIT`: 单位净值（复权净值缺失时的回退）
- `F_PRT_NETASSET`: 基金净资产（用于规模计算）
- `ANN_DATE`: 公告日期（用于去重取最新）

### 预设关联路径

> **关联产品代码**:
```sql
LEFT JOIN STAGE.WIND2_CHINAMUTUALFUNDNAV N
  ON N.F_INFO_WINDCODE = target.PRODUCT_CODE
 AND N.PRICE_DATE <= v_buss_date_8
```
> **取复权净值(优先复权，回退单位)**:
```sql
NVL(N.F_NAV_ADJUSTED, N.F_NAV_UNIT) AS NAV_ADJ
```
> **取最新净值(按 ANN_DATE 去重)**:
```sql
MAX(NVL(N.F_NAV_ADJUSTED, N.F_NAV_UNIT))
  KEEP (DENSE_RANK LAST ORDER BY N.ANN_DATE DESC NULLS LAST) AS NAV_ADJ
```

### 关联规则

- `[[rules/收益与胜率计算]]`（R07 胜率、R08 收益率净值计算）
- `[[rules/超额收益与同类排名]]`（R09 跑赢概率）
- `[[rules/正收益概率与排名]]`（R12 持有期正收益概率）
- `[[rules/回撤与风险计算]]`（R14 最大回撤、R15 最大日回撤）
- `[[rules/产品信息与规模]]`（R04 规模计算 Wind口径）
- `[[rules/封闭期与聚合规则]]`（R22 封闭期正收益概率）

## 来源与追溯

- data_project 快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- qudaojiankong 快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- data_project 源仓库提交：`bc37852`
- 本页由知识快照导入生成，事实边界以快照为准。
