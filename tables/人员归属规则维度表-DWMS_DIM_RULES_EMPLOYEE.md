---
title: "人员归属规则维度表｜DWMS_DIM_RULES_EMPLOYEE"
aliases: ["人员归属规则维度表", "DWMS_DIM_RULES_EMPLOYEE", "data_project:DWMS_DIM_RULES_EMPLOYEE", "人员归属规则维度表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/组织, 业务动作/归属, 数据技术/表, 数据技术/字段, 治理状态/生效]
keywords: ["人员归属规则维度表", "DWMS_DIM_RULES_EMPLOYEE", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 人员归属规则维度表｜DWMS_DIM_RULES_EMPLOYEE

## 概览

- 来源项目：`data_project`
- 物理表名：`DWMS_DIM_RULES_EMPLOYEE`
- 业务名称：人员归属规则维度表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:DWMS_DIM_RULES_EMPLOYEE
- canonical_key: DWMS_DIM_RULES_EMPLOYEE
- table_name: DWMS_DIM_RULES_EMPLOYEE
- object_name: 人员归属规则维度表
- domain: 六、归属规则域
- platform: 大数据平台/Oracle
- status: project-only
- change_type: unchanged
- content_hash: `8c3a681610413e2a`
- source_refs: `context/tables.md#L472`

#### 结构化事实

- business_role: 定义员工归属规则，根据渠道、省份、城市、网点匹配规则确定归属的渠道经理，支持规则生效期管理与多员工拆分
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: `策略组 (strategy_group)`

#### 原始事实摘录

* **物理表名（大数据平台）**: `dcmkt.mkt_dim_rules_employee` ⭐ **优先使用**
* **物理表名（Oracle库）**: `CJHX_DWMS.DWMS_DIM_RULES_EMPLOYEE`
* **说明**: 同一张表在不同平台的存储路径
* **表类型**: MKT层（营销域）/ DWMS层
* **业务用途**: 定义员工归属规则，根据渠道、省份、城市、网点匹配规则确定归属的渠道经理，支持规则生效期管理与多员工拆分
* **核心字段**:
  * `rule_id`: 规则行唯一ID
  * `rule_group_id`: 规则组ID（同一命中场景的拆分分组；同一命中可拆分给多个员工）
  * `priority`: 优先级（数字越大，优先级越高；用于同一策略组下不同规则组的命中优先级）
  * `strategy_group`: 规则策略组（如：'银行渠道部业绩归属'）
  * `attr_prod`: 匹配的产品名称（支持通配符 '*' 或具体产品名称）
  * `attr_channel`: 匹配渠道（支持通配符 '*' 或具体机构代码，如 dxjgdm）
  * `attr_province`: 匹配省份（支持通配符 '*' 或具体省份名称，如 sfmc）
  * `attr_city`: 匹配城市（支持通配符 '*' 或具体城市名称，如 csmc）
  * `attr_branch`: 匹配的销售网点（支持通配符 '*' 或具体渠道网点ID，如 qdid）
  * `emp_id`: 归属员工ID（⚠️ **注意：该字段直接存储员工姓名，无需再关联员工信息表获取姓名**）
  * `attr_pct`: 归属比例（同一 rule_group_id 内可拆分到多员工，比例可为100%、50%等）
  * `eff_start_dt`: 规则生效起始日期（格式: YYYYMMDD）
  * `eff_end_dt`: 规则生效结束日期（格式: YYYYMMDD，NULL表示永久有效）
  * `created_by_user`: 规则录入人员
* **匹配规则**: 
  * 支持通配符匹配：`'*'` 表示匹配该维度的所有值
  * 4字段匹配逻辑：`(attr_channel = '*' OR attr_channel = 实际值) AND (attr_province = '*' OR attr_province = 实际值) AND (attr_city = '*' OR attr_city = 实际值) AND (attr_branch = '*' OR attr_branch = 实际值)`
  * 日期有效性校验：数据日期必须在规则生效期内，即 `数据日期 >= eff_start_dt AND (eff_end_dt IS NULL OR 数据日期 <= eff_end_dt)`
  * 优先级/拆分逻辑：先按 `priority` 选出同一策略组下匹配规则的最高优先级规则组，再按 `rule_group_id` 展开多员工拆分，使用 `attr_pct` 表示各员工归属比例
* **⚠️ 策略组说明**:
  * `strategy_group = '银行渠道部业绩归属'`: 筛选银行渠道人员归属规则，精确到网点
  * `strategy_group = '券商业绩归属'`: 筛选券商渠道人员归属规则，仅精确到省份/城市
* **预设关联路径 (Relationships)**:
  * **关联 [员工归属] (通过渠道、省份、城市、网点匹配 + 日期有效性校验)**: 
    ```sql
    -- 前置条件: 必须先关联渠道信息表获取 dxjgdm, sfmc, csmc, qdid
    -- 匹配逻辑: 渠道 + 省份 + 城市 + 网点 -> 规则表（支持通配符）+ 日期有效性校验
    -- 优先使用大数据平台路径
    JOIN dcmkt.mkt_dim_rules_employee r 
        ON (r.attr_channel = '*' OR r.attr_channel = t3.dxjgdm)      -- 渠道匹配
            AND (r.attr_province = '*' OR r.attr_province = t3.sfmc)  -- 省份匹配
            AND (r.attr_city = '*' OR r.attr_city = t3.csmc)          -- 城市匹配
            AND (r.attr_branch = '*' OR r.attr_branch = CAST(t2.qdid AS STRING))  -- 网点匹配（渠道网点ID）
            AND r.strategy_group = '银行渠道部业绩归属'
            AND t1.cjdt >= r.eff_start_dt                              -- 规则生效起始日期校验
            AND (r.eff_end_dt IS NULL OR t1.cjdt <= r.eff_end_dt)     -- 规则生效结束日期校验（NULL表示永久有效）
    -- 输出: r.emp_id (归属员工ID)
    -- 注意: Oracle库路径为 CJHX_DWMS.DWMS_DIM_RULES_EMPLOYEE
    ```

---

# 第二部分：8倍镜财务考核域 (Oracle平台专属)

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
