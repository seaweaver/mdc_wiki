---
title: "销售人员-部门属性日表｜CDM_DWMS_SALR_BRCH_ATTR_DF"
aliases: ["销售人员-部门属性日表", "CDM_DWMS_SALR_BRCH_ATTR_DF", "data_project:CDM_DWMS_SALR_BRCH_ATTR_DF", "销售人员-部门属性日表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/组织, 业务域/销售, 数据技术/表, 数据技术/字段, 数据技术/大数据平台, 治理状态/生效]
keywords: ["销售人员-部门属性日表", "CDM_DWMS_SALR_BRCH_ATTR_DF", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 销售人员-部门属性日表｜CDM_DWMS_SALR_BRCH_ATTR_DF

## 概览

- 来源项目：`data_project`
- 物理表名：`CDM_DWMS_SALR_BRCH_ATTR_DF`
- 业务名称：销售人员-部门属性日表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/营销域数据分析项目知识快照导入]]

## 快照事实

- local_id: data-project:CDM_DWMS_SALR_BRCH_ATTR_DF
- canonical_key: CDM_DWMS_SALR_BRCH_ATTR_DF
- table_name: CDM_DWMS_SALR_BRCH_ATTR_DF
- object_name: 销售人员-部门属性日表
- domain: 五、组织人员域
- platform: Doris
- status: project-only
- change_type: unchanged
- content_hash: `014ea088b5f5202a`
- source_refs: `context/tables.md#L417`

#### 结构化事实

- business_role: 存储销售人员与部门/网点的归属关系日快照数据，用于查询销售人员列表、人员归属分析等。
- key_fields: 未显式说明
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名（Doris平台）**: `cjhx_dwms.cdm_dwms_salr_brch_attr_df` ⭐ **优先使用**
* **表类型**: CDM层（数据仓库中间层）
* **业务用途**: 存储销售人员与部门/网点的归属关系日快照数据，用于查询销售人员列表、人员归属分析等。
* **核心字段**:
  * `cjdt`: 数据日期（格式: YYYYMMDD，数据快照日期）
  * `salr`: 销售人员姓名（用于人员列表查询）
  * `cjdt`: 数据日期（格式: YYYYMMDD，数据快照日期）
  * `salr`: 销售人员姓名（用于人员列表查询）
  * `pd_code`: 产品代码 (关联 cdm_dwms_dim_bank_pd_f.pd_code)
  * `qdid`: 渠道网点ID (关联 cdm_dim_seg_chn_info_f.qdid)
  * `tot_amt`: 总保有量/总规模 (用于计算规模及规模净增)
  * `purs_amt`: 申购金额
  * `redp_amt`: 赎回金额
  * `aep`: 管理费
  * `fivm_amt`: 定投金额
  * `scrp_amt`: 认购金额
* **预设关联路径 (Relationships)**:
  * **查询近期人员列表**: 
    ```sql
    -- 获取近一年内最新数据日期的人员列表
    SELECT DISTINCT 
        salr AS `人员姓名`
    FROM cjhx_dwms.cdm_dwms_salr_brch_attr_df
    WHERE cjdt = (
            SELECT MAX(cjdt) 
            FROM cjhx_dwms.cdm_dwms_salr_brch_attr_df 
            WHERE cjdt >= date_sub(current_date(), INTERVAL 1 YEAR)
        )
        AND salr IS NOT NULL
    ORDER BY `人员姓名`
    ```
* **注意事项**:
  * 该表为日快照表，每日更新一次
  * 查询时建议使用最新数据日期（通过MAX(cjdt)获取）
  * `salr` 字段可能存在NULL值，查询时需过滤
  * Doris平台表，库名、表名、字段名全部小写
  * 中文别名必须使用反引号（`` `人员姓名` ``）

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
