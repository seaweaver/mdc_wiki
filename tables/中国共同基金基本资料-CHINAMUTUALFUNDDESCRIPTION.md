---
title: "中国共同基金基本资料｜CHINAMUTUALFUNDDESCRIPTION"
aliases: ["中国共同基金基本资料", "CHINAMUTUALFUNDDESCRIPTION", "data_project:CHINAMUTUALFUNDDESCRIPTION", "qudaojiankong:ChinaMutualFundDescription", "中国共同基金基本资料表"]
created: 2026-04-24
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/基金, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["中国共同基金基本资料", "CHINAMUTUALFUNDDESCRIPTION", "ChinaMutualFundDescription", "data_project", "qudaojiankong", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md", "raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---
# 中国共同基金基本资料｜CHINAMUTUALFUNDDESCRIPTION

## 概览

- 来源项目：`data_project`
- 物理表名：`CHINAMUTUALFUNDDESCRIPTION`
- 业务名称：中国共同基金基本资料
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:CHINAMUTUALFUNDDESCRIPTION
- canonical_key: CHINAMUTUALFUNDDESCRIPTION
- table_name: CHINAMUTUALFUNDDESCRIPTION
- object_name: 中国共同基金基本资料
- domain: 十一、外部数据域 (Wind)
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `e7c310da643910fb`
- source_refs: `context/tables.md#L826`

#### 结构化事实

- business_role: 记录公募基金的基本资料（包含管理人、托管人、前后端代码等）。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名 (Oracle库)**: `WIND.CHINAMUTUALFUNDDESCRIPTION`
* **业务用途**: 记录公募基金的基本资料（包含管理人、托管人、前后端代码等）。
* **业务主键**: `F_INFO_WINDCODE` (Wind代码)
* **核心字段**:
  * `F_INFO_WINDCODE`: Wind代码
  * `F_INFO_FRONT_CODE`: 前端代码(6位数字)
  * `F_INFO_NAME`: 基金简称
  * `F_INFO_FULLNAME`: 基金全称

---

---

## qudaojiankong 项目使用

在"蚂蚁渠道基金产品提报监控"项目中，此表用于产品基本信息获取。

- 物理表名：`STAGE.WIND2_CHINAMUTUALFUNDDESCRIPTI`（不同于 data_project 的 `WIND.CHINAMUTUALFUNDDESCRIPTION`）
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 主键：`F_INFO_WINDCODE`

### 核心字段

- `F_INFO_WINDCODE`: 基金 Wind 代码
- `F_INFO_SETUPDATE`: 成立日期 (YYYYMMDD)，用于计算成立时长
- `F_INFO_CORP_FUNDMANAGEMENTCOMP`: 基金管理人名称
- `F_INFO_STATUS`: 基金状态 (101001000 = 正常)

### 预设关联路径

> **关联基金池**:
```sql
INNER JOIN TMP_JKQD_FUND_METRICS E
  ON D.F_INFO_WINDCODE = E.PRODUCT_CODE
  AND E.S_FROM_PLACE = '1'
```

### 关联规则

- `[[rules/产品信息与规模]]`（R03 成立时长）
- `[[rules/基础参数与过滤]]`（R02 基金池过滤）

## 来源与追溯

- data_project 快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- qudaojiankong 快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- data_project 源仓库提交：`bc37852`
- 本页由知识快照导入生成，事实边界以快照为准。
