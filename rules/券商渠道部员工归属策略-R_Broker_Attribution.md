---
title: "券商渠道部员工归属策略｜R_Broker_Attribution"
aliases: ["券商渠道部员工归属策略", "R_Broker_Attribution", "data_project:R_Broker_Attribution", "Broker Channel Employee Attribution"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/组织, 业务域/渠道, 业务域/产品, 业务动作/归属, 业务动作/校验, 治理状态/生效]
keywords: ["券商渠道部员工归属策略", "R_Broker_Attribution", "Broker Channel Employee Attribution", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 券商渠道部员工归属策略｜R_Broker_Attribution

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Broker_Attribution`
- 英文锚点：`Broker Channel Employee Attribution`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:R_Broker_Attribution
- canonical_key: R_Broker_Attribution
- rule_id: R_Broker_Attribution
- rule_name: 券商渠道部员工归属策略 (Broker Channel Employee Attribution)
- status: project-only
- change_type: unchanged
- content_hash: `1e1778b861623bba`
- source_refs:
  - `context/rules.md#L206`

#### 结构化事实

- business_definition: **券商渠道部的业绩归属仅精确到省份/城市**，不精确到网点，通过省份城市归属到人。
- use_cases: 券商渠道部业绩归属，筛选条件 `strategy_group = '券商业绩归属'`。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: `DWD_CUST_PR_DTL_DI`, `DWMS_8_DIM_AGENCY_INFO`, `DWMS_DIM_EMPLOYEE`
- related_dictionary: `策略组 (strategy_group)`, `部门代码/部门名称 (AGENCYBELONG)`

#### 原始事实摘录

* **业务定义**: **券商渠道部的业绩归属仅精确到省份/城市**，不精确到网点，通过省份城市归属到人。
* **适用场景**: 券商渠道部业绩归属，筛选条件 `strategy_group = '券商业绩归属'`。
* **⚠️ 重要说明**:
  * **emp_id 直接存储员工姓名**，无需再关联员工信息表 (DWMS_DIM_EMPLOYEE) 获取姓名
  * 券商渠道部使用3字段匹配（渠道+省份+城市），**不含网点维度**
  * **渠道过滤必须使用**: 通过 `DWMS_8_DIM_AGENCY_INFO` 表 (大数据: `dcods.ods_dwms_8_dim_agency_info_f`) 过滤 `AGENCYBELONG = '券商'`
  * **关联方式**: 使用 `DISTINCT main_agencyno` 关联订单/持仓表的 `retl_num`（销售商编码），不能用 `agencyno`（因为 main_agencyno:agencyno 是一对多关系）
* **数据来源**: 
  * 销量统计: `DCCDM.DWD_CUST_PR_DTL_DI`
  * 保有规模（含地理信息）: `dccdm.cdm_dwd_ast_orde_bal_more_df`
* **匹配逻辑**: 
  * 支持通配符 '*' 表示匹配该维度的所有值
  * 省份匹配: `r.attr_province = '*' OR r.attr_province = b.sfmc`
  * 城市匹配: `r.attr_city = '*' OR r.attr_city = b.csmc`
  * **不含 attr_branch 网点匹配**
* **SQL 逻辑模板**:
  ```sql
  -- 券商归属逻辑 (仅省份+城市匹配，不含网点)
  AND r.strategy_group = '券商业绩归属'
  AND (r.attr_province = '*' OR r.attr_province = b.sfmc)
  AND (r.attr_city = '*' OR r.attr_city = b.csmc)
  -- 注意：不包含 attr_branch 网点匹配条件
  ```

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
