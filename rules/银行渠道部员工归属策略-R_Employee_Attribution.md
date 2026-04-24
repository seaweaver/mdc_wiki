---
title: "银行渠道部员工归属策略｜R_Employee_Attribution"
aliases: ["银行渠道部员工归属策略", "R_Employee_Attribution", "data_project:R_Employee_Attribution", "Bank Channel Employee Attribution"]
created: 2026-04-24
updated: 2026-04-24
type: rule
tags: [知识类型/规则, 知识类型/指标, 业务域/组织, 业务域/渠道, 业务域/产品, 业务动作/归属, 业务动作/校验, 治理状态/生效]
keywords: ["银行渠道部员工归属策略", "R_Employee_Attribution", "Bank Channel Employee Attribution", "data_project", "业务规则", "指标口径"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 银行渠道部员工归属策略｜R_Employee_Attribution

## 概览

- 来源项目：`data_project`
- 规则 ID：`R_Employee_Attribution`
- 英文锚点：`Bank Channel Employee Attribution`
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:R_Employee_Attribution
- canonical_key: R_Employee_Attribution
- rule_id: R_Employee_Attribution
- rule_name: 银行渠道部员工归属策略 (Bank Channel Employee Attribution)
- status: project-only
- change_type: unchanged
- content_hash: `89667e8c1f3cc6a9`
- source_refs:
  - `context/rules.md#L120`

#### 结构化事实

- business_definition: 根据渠道、省份、城市、网点匹配规则确定归属的渠道经理。**银行渠道部的业绩归属精确到网点**，即通过网点到人的映射关系确定归属。
- use_cases: 银行渠道部业绩归属统计，筛选条件 `strategy_group = '银行渠道部业绩归属'`。
- inputs: 见 SQL 逻辑模板或原始事实摘录
- outputs: 见 SQL 逻辑模板或原始事实摘录
- key_logic: 见原始事实摘录
- related_tables: `DWMS_DIM_EMPLOYEE`
- related_dictionary: `策略组 (strategy_group)`

#### 原始事实摘录

* **业务定义**: 根据渠道、省份、城市、网点匹配规则确定归属的渠道经理。**银行渠道部的业绩归属精确到网点**，即通过网点到人的映射关系确定归属。
* **适用场景**: 银行渠道部业绩归属统计，筛选条件 `strategy_group = '银行渠道部业绩归属'`。
* **⚠️ 重要说明**:
  * **emp_id 直接存储员工姓名**，无需再关联员工信息表 (DWMS_DIM_EMPLOYEE) 获取姓名
  * 银行渠道部使用4字段匹配（渠道+省份+城市+网点），**包含网点维度**
* **匹配逻辑**: 
  * 支持通配符 '*' 表示匹配该维度的所有值
  * 四个维度（渠道、省份、城市、网点）独立匹配
  * **日期有效性校验**：数据日期必须在规则生效期内，即 数据日期 >= eff_start_dt AND (eff_end_dt IS NULL OR 数据日期 <= eff_end_dt)
    * eff_end_dt IS NULL 表示规则永久有效
    * **重要**：pt_time 字段本身就是字符串格式 yyyyMMdd，无需使用 DATE_FORMAT 转换，直接进行字符串比较即可
  * **优先级与拆分**：
    * priority：同一策略组下，不同规则组ID的命中优先级，数字越大越优先
    * rule_group_id：同一命中场景下的拆分分组，允许一组规则拆分给多个员工
    * attr_pct：拆分比例（如 100%/50%），对同一 rule_group_id 的多员工进行分摊
* **SQL 逻辑模板**:
  ```sql
  -- 通配符匹配逻辑（4字段：渠道+省份+城市+网点）+ 日期有效性校验
  -- 先找到匹配规则，再按 priority 选最高优先级的 rule_group_id，并展开该组内的多员工拆分
  WITH latest_trade AS (
      SELECT DISTINCT
          jjzh,                -- 基金账号
          qdid,                -- 渠道网点ID
          pt_time,             -- 分配时间（字符串格式 yyyyMMdd，无需转换）
          ROW_NUMBER() OVER (PARTITION BY jjzh ORDER BY pt_time DESC, taqrlsh DESC) AS rn
      FROM dcods.ods_cr_t_qd_cfjg_jy_di
  ),
  base AS (
      SELECT
          t1.fund_acco,
          t1.cjdt,
          t1.hold_balance,
          t2.qdid,
          t2.pt_time,         -- pt_time 是字符串格式 yyyyMMdd
          t3.qdmc,
          t3.dxjgdm,
          t3.sfmc,
          t3.csmc
      FROM dccdm.cdm_dwms_customer_assets_sum_df t1
      LEFT JOIN latest_trade t2
          ON t1.fund_acco = t2.jjzh AND t2.rn = 1
      LEFT JOIN dcods.ods_cr_tjj_qd_qdxx_f t3
          ON t2.qdid = t3.id
  ),
  matched_rules AS (
      SELECT
          b.fund_acco,
          b.qdmc,
          r.emp_id,
          r.priority,
          r.rule_group_id,
          r.attr_pct
      FROM base b
      JOIN dcmkt.mkt_dim_rules_employee r
          ON (r.attr_channel = '*' OR r.attr_channel = b.dxjgdm)
         AND (r.attr_province = '*' OR r.attr_province = b.sfmc)
         AND (r.attr_city = '*' OR r.attr_city = b.csmc)
         AND (r.attr_branch = '*' OR r.attr_branch = CAST(b.qdid AS STRING))
         AND r.strategy_group = '银行渠道部业绩归属'
         AND b.pt_time >= r.eff_start_dt                    -- 直接字符串比较，无需 DATE_FORMAT
         AND (r.eff_end_dt IS NULL OR b.pt_time <= r.eff_end_dt)  -- 直接字符串比较
  ),
  max_priority AS (
      SELECT fund_acco, MAX(priority) AS max_pri
      FROM matched_rules
      GROUP BY fund_acco
  )
  -- 最终输出：为保持"客户-渠道经理"1对1关系，如同一客户匹配到多个员工（同优先级拆分），随机保留1个
  SELECT m.fund_acco, m.qdmc, m.emp_id, m.rule_group_id, m.attr_pct
  FROM (
      SELECT
          m.fund_acco,
          m.qdmc,
          m.emp_id,
          m.rule_group_id,
          m.attr_pct,
          ROW_NUMBER() OVER (PARTITION BY m.fund_acco ORDER BY RAND()) AS rn
      FROM matched_rules m
      JOIN max_priority mp
          ON m.fund_acco = mp.fund_acco AND m.priority = mp.max_pri
      WHERE m.emp_id IS NOT NULL
  ) m
  WHERE m.rn = 1;
  ```

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
