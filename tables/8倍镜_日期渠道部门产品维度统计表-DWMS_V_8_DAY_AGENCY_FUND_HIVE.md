---
title: "8倍镜_日期渠道部门产品维度统计表｜DWMS_V_8_DAY_AGENCY_FUND_HIVE"
aliases: ["8倍镜_日期渠道部门产品维度统计表", "DWMS_V_8_DAY_AGENCY_FUND_HIVE", "data_project:DWMS_V_8_DAY_AGENCY_FUND_HIVE", "8倍镜_日期渠道部门产品维度统计表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/组织, 业务域/渠道, 业务域/产品, 业务域/财务, 业务动作/统计, 数据技术/表, 治理状态/生效]
keywords: ["8倍镜_日期渠道部门产品维度统计表", "DWMS_V_8_DAY_AGENCY_FUND_HIVE", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 8倍镜_日期渠道部门产品维度统计表｜DWMS_V_8_DAY_AGENCY_FUND_HIVE

## 概览

- 来源项目：`data_project`
- 物理表名：`DWMS_V_8_DAY_AGENCY_FUND_HIVE`
- 业务名称：8倍镜_日期渠道部门产品维度统计表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:DWMS_V_8_DAY_AGENCY_FUND_HIVE
- canonical_key: DWMS_V_8_DAY_AGENCY_FUND_HIVE
- table_name: DWMS_V_8_DAY_AGENCY_FUND_HIVE
- object_name: 8倍镜_日期渠道部门产品维度统计表
- domain: 七、8倍镜统计表
- platform: Oracle
- status: project-only
- change_type: unchanged
- content_hash: `ff80228dade440ec`
- source_refs: `context/tables.md#L607`

#### 结构化事实

- business_role: 按日期、渠道、产品维度统计的财务考核数据。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: `部门代码/部门名称 (AGENCYBELONG)`

#### 原始事实摘录

* **物理表名 (Oracle平台)**: `CJHX_DWMS.DWMS_V_8_DAY_AGENCY_FUND_HIVE`
* **业务用途**: 按日期、渠道、产品维度统计的财务考核数据。
* **核心字段**:
  * `CJDT`: 交易确认日期
  * `AGENCYNO`: 渠道代码
  * `AGENCYNAME`: 渠道名称（⚠️ 关联外键，用于获取部门信息）
  * `FUNDCODE`: 基金代码
  * `TOTALUSERS`: 累计客户数
  * `FEE`: 管理费收入
  * `USERS`: 存量客户数
  * `SHARES`: 存量份额
  * `AMOUNT`: 存量金额
  * `BUY_USERS`: 申购客户数
  * `BUY_SHARES`: 申购份额
  * `BUY_AMOUNT`: 申购金额
  * `AUTOSHARES`: 定投份额
  * `AUTOAMOUNT`: 定投金额
  * `SELL_USERS`: 赎回客户数
  * `SELL_SHARES`: 赎回份额
  * `SELL_AMOUNT`: 赎回金额
* **⚠️ 重要说明**:
  * **该表不包含 AGENCYBELONG（部门信息）字段**
  * **必须通过 AGENCYNAME 关联 DWMS_8_DIM_AGENCY_INFO 表来获取部门归属**
* **预设关联路径 (Relationships)**:
  * **标准关联模式（基金信息+基金简称+渠道信息）**:
    ```sql
    -- 关联基金信息维表（获取基金详细信息）
    JOIN CJHX_DWMS.DWMS_8_DIM_FUND_INFO B
        ON A.FUNDCODE = B.FUNDCODE
    -- 关联基金简称维表（获取基金简称）
    LEFT JOIN CJHX_DWMS.DWMS_8_DIM_FUND_SHORTNAME C
        ON A.FUNDCODE = C.FUNDCODE
    -- ⚠️ 必须关联渠道信息维表（获取部门归属 AGENCYBELONG）
    JOIN (
        SELECT AGENCYNAME, AGENCYBELONG 
        FROM CJHX_DWMS.DWMS_8_DIM_AGENCY_INFO 
        GROUP BY AGENCYNAME, AGENCYBELONG
    ) D ON A.AGENCYNAME = D.AGENCYNAME
    ```
  * **按部门过滤（必须先关联表D）**: `WHERE D.AGENCYBELONG = '{dept_name}'` (例如: '券商', '银行', '网金')
  * **按时间范围过滤**: `WHERE A.CJDT >= '{start_date}' AND A.CJDT <= '{end_date}'`
* **注意事项**:
  * 该表已按日期、渠道、产品维度预聚合
  * 表中没有部门字段，部门信息必须通过关联 DWMS_8_DIM_AGENCY_INFO 获取
  * 关联渠道信息表时需要去重（使用 GROUP BY），因为同一渠道名称可能有多条记录

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
