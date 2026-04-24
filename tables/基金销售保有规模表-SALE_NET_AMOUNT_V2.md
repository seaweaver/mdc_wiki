---
title: "基金销售保有规模表｜SALE_NET_AMOUNT_V2"
aliases: ["基金销售保有规模表", "SALE_NET_AMOUNT_V2", "data_project:SALE_NET_AMOUNT_V2", "基金销售保有规模表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/销售, 业务域/产品, 业务动作/持仓, 业务动作/计算, 资产类型/基金, 数据技术/表, 治理状态/生效]
keywords: ["基金销售保有规模表", "SALE_NET_AMOUNT_V2", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 基金销售保有规模表｜SALE_NET_AMOUNT_V2

## 概览

- 来源项目：`data_project`
- 物理表名：`SALE_NET_AMOUNT_V2`
- 业务名称：基金销售保有规模表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:SALE_NET_AMOUNT_V2
- canonical_key: SALE_NET_AMOUNT_V2
- table_name: SALE_NET_AMOUNT_V2
- object_name: 基金销售保有规模表
- domain: 十、行业分析
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `bfa46aef443727c3`
- source_refs: `context/tables.md#L782`

#### 结构化事实

- business_role: 存储基金业协会每半年公布的一次的基金销售机构公募基金销售保有规模数据。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名 (Oracle库)**: `CJHX_DWMS.SALE_NET_AMOUNT_V2`
* **业务用途**: 存储基金业协会每半年公布的一次的基金销售机构公募基金销售保有规模数据。
* **数据周期**: 2024年开始改为半年公布一次（Q2/Q4），分别代表6月30日快照和12月31日快照。
* **核心字段**:
  * `d_year`: 年份 (VARCHAR2)
  * `d_quater`: 季度 (VARCHAR2, e.g. 'Q2', 'Q4')
  * `agency_fullname`: 机构名称/渠道全称 (VARCHAR2)
  * `prop_amount`: 权益基金保有规模（亿元） (NUMBER)
  * `non_monetary_amount`: 非货币市场基金保有规模（亿元） (NUMBER)
  * `stock_amount`: 股票型指数基金保有规模（亿元） (NUMBER)
* **注意事项**:
  * 仅包含头部代销机构的公开数据
  * 2024年后数据仅有Q2和Q4

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
