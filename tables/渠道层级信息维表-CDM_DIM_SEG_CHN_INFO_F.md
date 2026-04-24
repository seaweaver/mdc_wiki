---
title: "渠道层级信息维表｜CDM_DIM_SEG_CHN_INFO_F"
aliases: ["渠道层级信息维表", "CDM_DIM_SEG_CHN_INFO_F", "data_project:CDM_DIM_SEG_CHN_INFO_F", "渠道层级信息维表表"]
created: 2026-04-24
updated: 2026-04-24
type: data-object
tags: [知识类型/数据对象, 业务域/渠道, 业务动作/分类, 数据技术/表, 数据技术/字段, 数据技术/大数据平台, 治理状态/生效]
keywords: ["渠道层级信息维表", "CDM_DIM_SEG_CHN_INFO_F", "data_project", "营销域", "数据对象"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# 渠道层级信息维表｜CDM_DIM_SEG_CHN_INFO_F

## 概览

- 来源项目：`data_project`
- 物理表名：`CDM_DIM_SEG_CHN_INFO_F`
- 业务名称：渠道层级信息维表
- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 相关字典：[[concepts/营销域语义字典]]
- 项目入口：[[scenarios/data_project知识快照导入]]

## 快照事实

- local_id: data-project:CDM_DIM_SEG_CHN_INFO_F
- canonical_key: CDM_DIM_SEG_CHN_INFO_F
- table_name: CDM_DIM_SEG_CHN_INFO_F
- object_name: 渠道层级信息维表
- domain: 三、渠道网点域
- platform: Doris
- status: project-only
- change_type: unchanged
- content_hash: `8976999da162bcdd`
- source_refs: `context/tables.md#L309`

#### 结构化事实

- business_role: 存储渠道层级信息（最多5级），用于查询根渠道及子渠道、渠道层级树形结构展示。
- key_fields: `qdid`
- preset_join_paths: 见下方原始事实摘录中的“预设关联路径”
- related_dictionary: 无显式命中

#### 原始事实摘录

* **物理表名（Doris平台）**: `cjhx_dwms.cdm_dim_seg_chn_info_f` ⭐ **优先使用**
* **表类型**: CDM层（数据仓库中间层）
* **业务用途**: 存储渠道层级信息（最多5级），用于查询根渠道及子渠道、渠道层级树形结构展示。
* **主键**: `qdid`
* **核心字段**:
  * `qdid`: 渠道网点ID（主键）
  * `retl_num`: 销售商编码/根渠道代码（用于关联根渠道）
  * `qddj`: 渠道等级（1=根渠道，2=二级渠道，...，5=五级渠道）
  * `pri_chn_name`: 一级渠道名称（根渠道名称）
  * `scd_chn_name`: 二级渠道名称
  * `thir_chn_name`: 三级渠道名称
  * `four_chn_name`: 四级渠道名称
  * `pri_chn_name`: 一级渠道名称（根渠道名称）
  * `scd_chn_code`: 二级渠道代码
  * `scd_chn_name`: 二级渠道名称
  * `thir_chn_code`: 三级渠道代码
  * `thir_chn_name`: 三级渠道名称
  * `four_chn_code`: 四级渠道代码
  * `four_chn_name`: 四级渠道名称
  * `fift_chn_code`: 五级渠道代码
  * `fift_chn_name`: 五级渠道名称
  * `father_qdid`: 父级渠道网点ID
* **预设关联路径 (Relationships)**:
  * **查询根渠道列表**: 
    ```sql
    -- 获取所有根渠道（一级渠道）
    SELECT DISTINCT 
        retl_num AS `根渠道代码`,
        qdid AS `根渠道网点ID`,
        pri_chn_name AS `根渠道名称`
    FROM cjhx_dwms.cdm_dim_seg_chn_info_f
    WHERE qddj = '1'
    ORDER BY pri_chn_name
    ```
  * **查询根渠道下的子渠道（模糊搜索）**: 
    ```sql
    -- 获取指定根渠道下的所有子渠道（支持模糊搜索）
    SELECT 
        qdid AS `子渠道代码`,
        CONCAT_WS('/', pri_chn_name, scd_chn_name, thir_chn_name, four_chn_name, fift_chn_name) AS `子渠道名称`
    FROM cjhx_dwms.cdm_dim_seg_chn_info_f
    WHERE retl_num = '{root_channel_code}'  -- 根渠道代码
        AND CONCAT_WS('/', pri_chn_name, scd_chn_name, thir_chn_name, four_chn_name, fift_chn_name) LIKE '%{search_keyword}%'
    ORDER BY qddj, pri_chn_name, scd_chn_name, thir_chn_name, four_chn_name, fift_chn_name
    ```
* **注意事项**:
  * 该表为Doris平台表，库名、表名、字段名全部小写
  * 中文别名必须使用反引号（`` `渠道名称` ``）
  * `qddj` 字段用于区分渠道层级，值为字符串类型（'1', '2', ...）
  * 子渠道名称通过 CONCAT_WS 拼接各级渠道名称，以 '/' 分隔
  * 查询根渠道时使用 `WHERE qddj = '1'`

---

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页由知识快照导入生成，事实边界以快照为准。
