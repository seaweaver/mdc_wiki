---
title: "中国共同基金基金经理｜ChinaMutualFundManager"
aliases: ["中国共同基金基金经理", "ChinaMutualFundManager", "qudaojiankong:ChinaMutualFundManager", "基金经理任职记录"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/基金, 数据技术/表, 数据技术/Wind, 治理状态/生效]
keywords: ["ChinaMutualFundManager", "qudaojiankong", "基金经理", "F_INFO_MANAGER_STARTDATE", "F_INFO_MANAGER_LEAVEDATE", "WIND2_CHINAMUTUALFUNDMANAGER"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 中国共同基金基金经理｜ChinaMutualFundManager

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`STAGE.WIND2_CHINAMUTUALFUNDMANAGER`
- 业务名称：基金经理任职记录
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:ChinaMutualFundManager
- canonical_key: ChinaMutualFundManager
- table_name: ChinaMutualFundManager
- object_name: 中国共同基金基金经理
- domain: Wind 源表
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `28e78ffd52c94880`
- source_refs: `context/tables.md#L192`

### 结构化事实

- business_role: 基金经理任职记录
- key_fields: `F_INFO_WINDCODE`, `F_INFO_FUNDMANAGER`, `F_INFO_FUNDMANAGER_ID`, `F_INFO_MANAGER_STARTDATE`
- preset_join_paths: 见下方
- related_dictionary: 无显式命中

### 原始事实摘录

* **物理表名**: `STAGE.WIND2_CHINAMUTUALFUNDMANAGER`
* **主键**: `F_INFO_WINDCODE` + `F_INFO_FUNDMANAGER`(或 `F_INFO_FUNDMANAGER_ID`) + `F_INFO_MANAGER_STARTDATE`
* **说明**: 基金经理任职记录
* **核心字段**:
  * `F_INFO_WINDCODE`: 基金 Wind 代码
  * `F_INFO_FUNDMANAGER`: 基金经理姓名
  * `F_INFO_FUNDMANAGER_ID`: 基金经理 ID
  * `F_INFO_MANAGER_STARTDATE`: 任职日期 (YYYYMMDD)
  * `F_INFO_MANAGER_LEAVEDATE`: 离职日期 (YYYYMMDD，00000000 表示未离职)
  * `ANN_DATE`: 公告日期
* **预设关联路径**:
  > **判断当前在任**:
  ```sql
  NVL(TO_DATE(NULLIF(M.F_INFO_MANAGER_LEAVEDATE, '00000000'), 'YYYYMMDD'), DATE '2999-12-31')
    >= TRUNC(TO_DATE(v_buss_date_8, 'yyyymmdd'))
  ```
  > **取同基金经理所有产品**:
  ```sql
  JOIN ON MGR_KEY = COALESCE(M.F_INFO_FUNDMANAGER_ID, M.F_INFO_FUNDMANAGER)
  ```

---

## 关联

被 `[[rules/基金经理关联]]`（R05 同基金经理产品、R06 投资年限）消费。

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`28e78ffd52c94880`
- 本页由知识快照导入生成，事实边界以快照为准。
