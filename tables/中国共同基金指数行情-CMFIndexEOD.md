---
title: "中国共同基金指数行情｜CMFIndexEOD"
aliases: ["中国共同基金指数行情", "CMFIndexEOD", "qudaojiankong:CMFIndexEOD", "货币市场指数行情"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/指数, 数据技术/表, 数据技术/Wind, 治理状态/生效]
keywords: ["CMFIndexEOD", "qudaojiankong", "h11025.CSI", "S_DQ_CLOSE", "WIND2_CMFINDEXEOD", "货币市场指数"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 中国共同基金指数行情｜CMFIndexEOD

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`STAGE.WIND2_CMFINDEXEOD`
- 业务名称：基金指数日行情，用于获取货币市场指数 (h11025.CSI) 的收盘价
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 相关字典：`货币市场指数`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:CMFIndexEOD
- canonical_key: CMFIndexEOD
- table_name: CMFIndexEOD
- object_name: 中国共同基金指数行情
- domain: Wind 源表
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `273c630aff058889`
- source_refs: `context/tables.md#L234`

### 结构化事实

- business_role: 基金指数日行情，用于获取货币市场指数 (h11025.CSI) 的收盘价
- key_fields: `S_INFO_WINDCODE`, `TRADE_DT`
- preset_join_paths: 见下方
- related_dictionary: `货币市场指数`

### 原始事实摘录

* **物理表名**: `STAGE.WIND2_CMFINDEXEOD`
* **主键**: `S_INFO_WINDCODE` + `TRADE_DT`
* **说明**: 基金指数日行情，用于获取货币市场指数 (h11025.CSI) 的收盘价
* **核心字段**:
  * `S_INFO_WINDCODE`: 指数 Wind 代码
  * `TRADE_DT`: 交易日期 (YYYYMMDD)
  * `S_DQ_CLOSE`: 收盘价
  * `OPDATE`: 操作日期
  * `INSERTTIME`: 插入时间
* **预设关联路径**:
  > **取货币指数 h11025.CSI 日行情**:
  ```sql
  WHERE S_INFO_WINDCODE = 'h11025.CSI'
    AND TRADE_DT <= v_buss_date_8
  ```

---

## 关联

被 `[[rules/超额收益与同类排名]]`（R09 跑赢货币指数概率、R10 货基指数收益率）消费。

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`273c630aff058889`
- 本页由知识快照导入生成，事实边界以快照为准。
