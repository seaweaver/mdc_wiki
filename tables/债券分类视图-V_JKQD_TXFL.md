---
title: "债券分类视图｜V_JKQD_TXFL"
aliases: ["债券分类视图", "V_JKQD_TXFL", "qudaojiankong:V_JKQD_TXFL", "天相L4债券分类视图"]
created: 2026-04-30
updated: 2026-04-30
type: data-object
tags: [知识类型/数据对象, 业务域/产品, 资产类型/债券, 数据技术/视图, 数据技术/Oracle, 治理状态/生效]
keywords: ["V_JKQD_TXFL", "qudaojiankong", "CJHX_DWMS", "STYPE", "天相L4", "短债", "中短债", "中长债", "债券分类"]
sources: ["raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md"]
status: active
---

# 债券分类视图｜V_JKQD_TXFL

## 概览

- 来源项目：`qudaojiankong`（蚂蚁渠道基金产品提报监控）
- 物理表名：`CJHX_DWMS.V_JKQD_TXFL`
- 业务名称：债券分类视图，提供基金的天相 L4 分类
- 快照 ID：`qudaojiankong:2026-04-30:b722ebd`
- 来源工件：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 相关字典：`天相L4债券分类 (STYPE)`
- 项目入口：[[scenarios/蚂蚁渠道基金产品提报监控-数据加工]]

## 快照事实

- local_id: qudaojiankong:V_JKQD_TXFL
- canonical_key: V_JKQD_TXFL
- table_name: V_JKQD_TXFL
- object_name: 债券分类视图
- domain: Oracle 内部源表
- platform: Oracle
- status: project-only
- change_type: baseline
- content_hash: `eb30498d566ef812`
- source_refs: `context/tables.md#L359`

### 结构化事实

- business_role: 提供基金的天相 L4 分类（短债/中短债/中长债），用于同类排名分组
- key_fields: 未显式说明
- preset_join_paths: 按 STYPE 分组做同类排名
- related_dictionary: `天相L4债券分类 (STYPE)`

### 原始事实摘录

* **物理表名**: `CJHX_DWMS.V_JKQD_TXFL`
* **说明**: 债券分类视图，提供基金的天相 L4 分类（短债/中短债/中长债）
* **核心字段**:
  * `F_INFO_WINDCODE`: 基金 Wind 代码
  * `STYPE`: 债券分类（枚举值：短债 / 中短债 / 中长债）
* **预设关联路径**:
  > **同类排名按 STYPE 分组**:
  ```sql
  JOIN CJHX_DWMS.V_JKQD_TXFL T
    ON T.F_INFO_WINDCODE = target.PRODUCT_CODE
  WHERE T.STYPE IN ('短债', '中短债', '中长债')
  ```

---

## 关联

被同类排名规则 R11 和 R13 使用，详见 `[[rules/超额收益与同类排名]]` 和 `[[rules/正收益概率与排名]]`。

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/qudaojiankong/蚂蚁渠道基金产品提报监控-知识快照-2026-04-30-b722ebd.md`
- 源仓库提交：`b722ebd`
- 源内容哈希：`eb30498d566ef812`
- 本页由知识快照导入生成，事实边界以快照为准。
