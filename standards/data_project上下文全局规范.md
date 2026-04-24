---
title: "data_project上下文全局规范"
aliases: ["data_project全局规范", "营销域SQL规范", "平台识别规则", "跨平台查询禁混"]
created: 2026-04-24
updated: 2026-04-24
type: standard
tags: [知识类型/规范, 业务动作/校验, 治理状态/内部, 治理状态/生效]
keywords: ["SQL规范", "中文字段别名", "跨平台查询", "平台识别", "data_project"]
sources: ["raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md"]
status: active
---
# data_project上下文全局规范

## 定位

本页承载知识快照中的项目级全局说明，尤其是 SQL 输出、编码、平台识别、跨平台查询限制等会影响后续数据开发与 agent 生成 SQL 的约束。

- 快照 ID：`data-project:2026-04-24:bc37852`
- 来源工件：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 项目入口：[[scenarios/data_project知识快照导入]]

## 全局知识摘录

### tables.md 文件级说明

> 以下为文件级摘录。为避免污染快照主章节结构，原始标题已转为普通文本。
>
> \# 营销域物理模型定义
>
> > **使用说明**：本文件定义了所有物理表结构及固定的关联路径。编写 SQL 时必须严格遵守 [预设关联路径]。
> > 
> > **文档结构**：本文档按业务域分类，分为三大部分：
> > * **第一部分**：核心业务表（按业务域分类，优先大数据平台）
> > * **第二部分**：8倍镜财务考核域（Oracle平台专属）
> > * **第三部分**：其他辅助表
> > 
> > **路径优先级**：部分表在Oracle库和大数据平台都有存储（同一张表），文档中优先使用**大数据平台路径**进行描述，同时标注Oracle库路径作为参考。
> > 
> > **库名映射说明**:
> > * **Oracle 平台**: `CJHX_VIEW`, `CJHX_DWMS`, `CJHX_CDM`, `STAGE`
> > * **大数据平台**: `dcods`, `dcmkt`, `dccdm`
> > * **Doris 平台**: `cjhx_dwms` (小写)
> > 
> > **平台识别规则**:
> > * **如何识别表所在平台**：通过库名前缀判断
> >   * 库名为 `CJHX_DWMS`、`CJHX_VIEW`、`CJHX_CDM`、`STAGE` → **Oracle 平台**
> >   * 库名为 `dcods`、`dcmkt`、`dccdm` → **大数据平台**
> >   * 库名为 `cjhx_dwms` (小写) → **Doris 平台**
> > * **严格禁止跨平台查询**：同一个SQL中严禁混合使用不同平台的表
> >   * ❌ 错误：`FROM CJHX_DWMS.TABLE1 JOIN dccdm.TABLE2` (Oracle + 大数据平台)
> >   * ✅ 正确：`FROM CJHX_DWMS.TABLE1 JOIN CJHX_DWMS.TABLE2` (纯Oracle平台)
> >   * ✅ 正确：`FROM dccdm.TABLE1 JOIN dccdm.TABLE2` (纯大数据平台)
>
> \---
>
> \# 第一部分：核心业务表
>
> \## 一、交易订单域

### rules.md 文件级说明

> 以下为文件级摘录。为避免污染快照主章节结构，原始标题已转为普通文本。
>
> \# 营销域业务逻辑库
> > **使用说明**：本文件定义了通用的计算口径和过滤逻辑。
>
> > **SQL输出规范（大数据平台）**:
> > * **中文字段别名规范**:
> >   * 大数据平台（Hive/SparkSQL/Doris）要求中文别名必须使用反引号（\`）包围
> >   * ❌ 错误：`SELECT COUNT(*) AS 客户总数`
> >   * ✅ 正确：`SELECT COUNT(*) AS \`客户总数\``
> >   * 原因：中文字符在SQL解析器中可能被识别为特殊字符，反引号确保正确识别
> > * **英文字段别名规范**:
> >   * 英文别名可以不使用反引号（推荐snake_case命名）
> >   * ✅ 正确：`SELECT COUNT(*) AS total_customers`
> > * **平台差异**:
> >   * Oracle平台：中文别名使用双引号（"）或不使用引号
> >   * 大数据平台：中文别名必须使用反引号（\`）
> > * **适用范围**：所有大数据平台SQL输出（dccdm.*、dcods.*库）
>
> > **SQL编码规范（通用）**:
> > * **R1. 禁止行内注释与代码混排**:
> >   * 行内注释 `-- xxx` 不要放在函数参数行末尾，否则可能导致解析器将逗号/括号误判为注释的一部分
> >   * ❌ 错误：`REGEXP_REPLACE(col, '^中国', ''), -- 去前缀`
> >   * ✅ 正确：在代码块上方添加注释 `-- 去前缀`，代码行不带注释
> > * **R2. 避免使用正则函数**:
> >   * `REGEXP_REPLACE`、`REGEXP_SUBSTR` 等正则函数在不同平台语法存在差异，容易引发兼容性问题
> >   * ✅ 推荐：优先使用 `REPLACE`、`SUBSTR`、`TRIM` 等 ANSI 标准字符串函数
> >   * 示例：`REPLACE(REPLACE(col, '（', ''), '）', '')` 替代 `REGEXP_REPLACE(col, '[(（].*[)）]', '')`
> > * **R3. 函数括号紧跟函数名**:
> >   * 函数名与左括号之间不要有空格
> >   * ❌ 错误：`REPLACE (str, 'a', 'b')`
> >   * ✅ 正确：`REPLACE(str, 'a', 'b')`
> > * **R4. 嵌套函数保持统一缩进**:
> >   * 每层嵌套增加 4 空格缩进，右括号与对应函数名对齐
> >   * 示例：
> >     ```sql
> >     REPLACE(
> >         REPLACE(
> >             REPLACE(col, '中国', ''),
> >             '股份有限公司', ''
> >         ),
> >         '有限公司', ''
> >     )
> >     ```

### dictionary.md 文件级说明

> 以下为文件级摘录。为避免污染快照主章节结构，原始标题已转为普通文本。
>
> \# 营销域语义字典
>
> \## 1. 核心枚举值 (Enums)
> > AI 在生成 SQL 过滤条件时，必须使用这里的 Code。

## 来源与追溯

- 原始快照：`raw/knowledge-snapshots/data-project/data_project-知识快照-2026-04-24-bc37852.md`
- 源仓库提交：`bc37852`
- 源内容哈希：`8db680bd642d5917`
- 本页用于显式提升快照中的全局约束，不替代 raw 快照。
