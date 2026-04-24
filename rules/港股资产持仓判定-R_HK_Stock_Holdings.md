---
title: "港股资产持仓判定｜R_HK_Stock_Holdings"
aliases: ["港股资产持仓判定", "R_HK_Stock_Holdings", "data_project:R_HK_Stock_Holdings", "HK Stock Holdings Determination"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/投研, 业务动作/持仓, 业务动作/校验, 业务动作/分类, 资产类型/港股, 治理状态/生效]
keywords: ["港股资产持仓判定", "R_HK_Stock_Holdings", "HK Stock Holdings Determination", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 港股资产持仓判定｜R_HK_Stock_Holdings

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_HK_Stock_Holdings`
- 英文锚点：`HK Stock Holdings Determination`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:R_HK_Stock_Holdings
- canonical_key: R_HK_Stock_Holdings
- rule_id: R_HK_Stock_Holdings
- rule_name: 港股资产持仓判定 (HK Stock Holdings Determination)
- status: variant
- change_type: unchanged
- content_hash: `5e02ee35ea6c294a`
- source_refs:
  - `context/rules.md#L456`
  - `context/rules.md#L456`

#### 结构化事实

- business_definition: 判定某基金是否持有港股资产，可以通过资产配置表或底层持股明细表进行判断。
- use_cases: 查询含港股持仓的基金列表、计算基金的港股持仓比例。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: `CHINAMUTUALFUNDASSETPORTFOLIO`, `CHINAMUTUALFUNDSTOCKPORTFOLIO`
- related_dictionary: 无显式命中

#### 原始事实摘录

* **业务定义**: 判定某基金是否持有港股资产，可以通过资产配置表或底层持股明细表进行判断。
* **适用场景**: 查询含港股持仓的基金列表、计算基金的港股持仓比例。
* **判定方法**:
  * **方法一 (宏观，推荐)**: 通过 `WIND.CHINAMUTUALFUNDASSETPORTFOLIO` (资产配置表) 的 `F_PRT_HKSTOCKVALUE` 字段是否大于0判断。此方法最适用于通过“沪深港通”投资港股的基金。
  * **方法二 (微观下穿)**: 通过 `WIND.CHINAMUTUALFUNDSTOCKPORTFOLIO` (持股明细表)，查找 `S_INFO_STOCKWINDCODE` 后缀是否带有 `.HK`。
* **SQL 逻辑模板**:
  ```sql
  -- 方法一: 依赖资产配置表 (Oracle)
  SELECT S_INFO_WINDCODE,

#### 补充摘录（重复来源）

- 补充来源：`context/rules.md#L456`

* **业务定义**: 判定某基金是否持有港股资产，可以通过资产配置表或底层持股明细表进行判断。
* **适用场景**: 查询含港股持仓的基金列表、计算基金的港股持仓比例。
* **判定方法**:
  * **方法一 (宏观，推荐)**: 通过 `WIND.CHINAMUTUALFUNDASSETPORTFOLIO` (资产配置表) 的 `F_PRT_HKSTOCKVALUE` 字段是否大于0判断。此方法最适用于通过“沪深港通”投资港股的基金。
  * **方法二 (微观下穿)**: 通过 `WIND.CHINAMUTUALFUNDSTOCKPORTFOLIO` (持股明细表)，查找 `S_INFO_STOCKWINDCODE` 后缀是否带有 `.HK`。
* **SQL 逻辑模板**:
  ```sql
  -- 方法一: 依赖资产配置表 (Oracle)
  SELECT S_INFO_WINDCODE,
         CASE WHEN MAX(NVL(F_PRT_HKSTOCKVALUE, 0)) > 0 THEN '是' ELSE '否' END AS 是否持有港股资产
  FROM WIND.CHINAMUTUALFUNDASSETPORTFOLIO
  WHERE S_INFO_WINDCODE IN ('013348.OF', '011206.OF')
  GROUP BY S_INFO_WINDCODE;

  -- 方法二: 依赖持股明细表 (Oracle)
  SELECT S_INFO_WINDCODE,
         CASE WHEN SUM(CASE WHEN S_INFO_STOCKWINDCODE LIKE '%.HK' THEN F_PRT_STKVALUE ELSE 0 END) > 0 THEN '是' ELSE '否' END AS 是否持有港股资产
  FROM WIND.CHINAMUTUALFUNDSTOCKPORTFOLIO
  WHERE S_INFO_WINDCODE IN ('013348.OF', '011206.OF')
  GROUP BY S_INFO_WINDCODE;
  ```

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
