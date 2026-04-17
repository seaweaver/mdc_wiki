# 知识库结构规范｜Wiki Schema

## 领域定位｜Domain

本 wiki 是数据开发团队面向零售业务场景建设的共享 markdown 知识库。

它用于沉淀可长期复用的知识资产，包括：
- 项目背景与建设方案
- 数据来源与对象说明
- 业务规则与指标口径
- 技术实现约束
- 场景流程与经验结论
- 排障与演进记录

它不是普通笔记堆，也不是只给人看的文档站。  
它的目标是成为一个**可被 agent 持续读取、定位、串联、增量维护**的知识底座。

## 通用约定｜Conventions

- 本项目仓库根目录就是 wiki 根目录
- 新增页面文件名优先使用中文，只有在明确需要兼容历史路径或技术集成时才保留英文文件名
- 每个 wiki 页面都必须包含 YAML frontmatter
- 页面正文、摘要、标签、索引说明默认以中文为主
- 英文只作为稳定锚点、技术标签、缩写或兼容检索使用
- 页面之间尽量使用 `[[wikilinks]]` 建立链接
- 页面要保持可扫描；如果内容已经不适合快速浏览，应拆页
- 页面更新时必须同步更新 `updated` 日期
- 新增页面后必须登记到 `index.md`
- 重要操作、结构变化、批量导入等动作必须写入 `log.md`
- 原始材料一旦归档到 `raw/`，默认不再修改；修正和解释应写入结构化页面
- 矛盾结论、未知状态、`null` 结果都可以是有效知识状态，不能为了“整齐”而隐藏

## 仓库结构｜Repository Layout

- `SCHEMA.md`：本知识库的结构规范、命名约定、更新规则
- `index.md`：总导航页和内容目录
- `log.md`：追加式活动日志
- `raw/internal-docs/`：复制归档的内部原始材料，例如 Word、Excel、PPT、PDF
- `tables/`：数据对象页，如表、视图、字段集合、平台、数据源
- `rules/`：业务规则、指标口径、术语定义、阈值逻辑
- `scenarios/`：业务场景、建设专题、试点页面、端到端流程页
- `capabilities/`：MCP、Skill、CLI、规则引擎、标签引擎等能力资产
- `standards/`：模板、命名规则、写作规范、流程规则
- `raw/`：原始来源材料
- `entities/`：稳定对象页，如渠道、指数、平台、系统、数据集、供应商
- `concepts/`：抽象概念页，如指标逻辑、共享术语、计算思想、通用约束
- `comparisons/`：对比分析页，只有明确需要横向比较时才建立
- `queries/`：高价值问答沉淀页，只保存值得反复复用的答案
- `_archive/`：已被替代但仍需保留追溯链路的历史内容

## Frontmatter 规范｜Frontmatter

```yaml
---
title: 页面标题
aliases: [别名1, 别名2]
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: data-object | rule | metric | scenario | project | capability | standard | entity | concept | comparison | query | summary
tags: [标签]
keywords: [中文检索词, English keyword]
sources: [raw/articles/source-name.md]
status: draft | active | archived
---
```

说明：
- `title` 建议使用 `英文锚点｜中文标题` 的形式
- `aliases` 必须优先覆盖业务人员常见中文说法
- `keywords` 可中英混合，但中文问法优先
- frontmatter 的字段名保持英文，便于 agent 和工具统一处理

## 文件名规范｜Filename Convention

- 新增内容优先使用中文文件名
- 文件名应直接反映业务对象、概念或场景名称，避免缩写过多
- 例如：
  - `滚动超额收益胜率.md`
  - `蚂蚁渠道.md`
  - `蚂蚁选品试点场景.md`
- 如果已有英文文件名已被引用或已形成稳定路径，可以暂时保留，不强制重命名

## 检索规范｜Retrieval Convention

- `aliases` 应覆盖业务同事会直接说出口的中文问题表达
- `keywords` 应覆盖中文主表达，同时保留必要英文术语或代码
- 页面标题、摘要、正文第一段都应尽量让中文语义足够清晰，便于 agent 低成本命中

## 标签体系｜Tag Taxonomy

所有页面使用的标签，都应尽量落在以下范围内，避免标签无限扩散：

- 团队与范围：`team`、`project`、`domain`、`internal`、`external`
- 数据相关：`datasource`、`lineage`、`metric`、`schema`、`field`、`quality`、`validation`、`cache`
- 工程相关：`architecture`、`pipeline`、`workflow`、`tooling`、`automation`、`integration`、`testing`
- 运维与问题：`incident`、`troubleshooting`、`deployment`、`runbook`、`monitoring`
- 研究与判断：`vendor`、`methodology`、`benchmark`、`assumption`、`contradiction`、`unknown`
- 业务上下文：`fund`、`stock`、`strategy`、`report`、`compliance`、`metadata`

## 建页阈值｜Page Thresholds

- 当某个概念或对象在一个来源中非常核心，或在多个来源中反复出现时，应新建页面
- 当新材料只是补充已有知识时，优先更新已有页，不轻易重复建页
- 不要为一次性、过渡性、没有复用价值的零碎信息单独建页
- 概念页只有在“可脱离具体赛道阈值独立解释”时，才值得单独建页
- 仅以观察窗口、周期、阈值不同的变体，优先并入已有概念家族页，不单独建页
- 单个规则页专属的参数实例、窗口实例、阈值实例，默认留在 `rules/`
- 当页面已经难以在短时间内读完并定位重点时，应拆页
- 当页面内容已被新版本完全替代，但仍需追溯时，应移入 `_archive/`

## 内容落位规则｜Placement Rules

- `scenarios/`：用于解释端到端业务流程、建设专题、上下游依赖和交付逻辑
- `rules/`：用于解释规则集、阈值、口径、业务约束和指标定义
- `concepts/`：用于解释可复用的抽象概念、共享术语、通用指标逻辑、通用计算思想
- `entities/`：用于解释稳定被引用的对象，如渠道、指数、平台、系统、数据集、供应商
- `comparisons/`：只有存在真实横向比较任务时才建立
- `queries/`：只有高价值问答值得回填时才建立

说明：
- 本轮命名调整后，第一层主目录标准名称为 `tables/`、`rules/`、`scenarios/`
- 如果在历史材料、旧日志或旧链接中看到 `data-objects/`、`rules-and-metrics/`、`scenarios-and-projects/`，应将其理解为旧版命名，而不是当前新增内容的默认落位

## 原子化抽取触发条件｜Atomic Extraction Triggers

- 如果某个抽象概念、指标逻辑或术语在两个及以上页面重复出现，就应抽取到 `concepts/`
- 如果某个稳定对象，如渠道、指数、平台、系统、数据集、基准，在两个及以上页面重复出现，就应抽取到 `entities/`
- 如果某个概念只是更大概念家族下的窗口变体、周期变体或场景子变体，应优先并入家族页
- 只有当子概念在多个规则集下都独立演化、且单独检索价值足够高时，才从家族页再拆出
- 场景页和规则页不应长期重复承载同一个概念或对象的完整定义
- 每次完成一轮较大的材料导入后，都应检查是否需要新增 `concepts/` 或 `entities/` 页面，再视为导入完成

## 实体页规范｜Entity Pages

实体页用于记录稳定对象，例如：
- 渠道
- 指数
- 平台
- 系统
- 数据集
- 供应商

典型结构建议包括：
- 概览
- 关键事实
- 在本环境中的作用
- 与其他页面的关系
- 易错点或注意事项
- 来源

## 概念页规范｜Concept Pages

概念页用于记录会跨页面复用的抽象知识，例如：
- 指标定义
- 数据建模约定
- 通用计算逻辑
- 口径规则
- 工作流模式
- 架构思想

典型结构建议包括：
- 定义
- 为什么重要
- 当前团队理解
- 适用边界或约束
- 相关页面
- 来源

额外约束：
- 优先建设“概念家族页”，例如基金经理资质、期限结构、仓位与暴露约束
- 家族页内可以容纳多个相近子概念，不要为每个窗口、周期、阈值变体单独建页
- 只有当家族页过长，或子概念在多个场景下已形成稳定独立语义时，才拆出子页
- 赛道专属阈值、参数实例和窗口实例，应继续留在 `rules/`

## 对比页规范｜Comparison Pages

对比页适用于：
- 方案对比
- 规则差异对比
- 平台差异对比
- 赛道差异对比

应至少包含：
- 比较对象
- 比较维度
- 结论或建议
- 来源与适用边界

## 问答页规范｜Queries Pages

只有满足以下条件时，才把问答沉淀到 `queries/`：
- 回答需要明显的综合分析
- 结果未来很可能被再次复用
- 重新推导的成本较高

简单查值、一次性问题、临时问答，不要塞进 `queries/`

## 更新策略｜Update Policy

当新信息与已有内容冲突时：

1. 先检查日期和来源质量
2. 如果冲突真实存在，不要直接覆盖旧说法
3. 在页面正文里明确写出冲突点
4. 需要时保留 `contradiction` 标签
5. 在 lint 或人工 review 时把未解决矛盾显式暴露出来

## 团队建议｜Team Recommendations

- 优先做增量维护，而不是周期性推倒重写
- 在适合批量验证的场景下优先使用 markdown 和 csv
- 保持“原始证据”和“结构化结论”分离
- 使用 Git 历史和 `log.md` 共同保证可追溯
- 默认以项目根目录作为 wiki 根目录，除非有明确隔离需要
- 当数据库缺少结构化字段、但供应商可按代码和报告期查询时，优先采用本地缓存 + 增量采集 + `null` 作为有效终态的策略
- 场景页要负责串联，不要把所有底层定义都堆在场景页
- 当 wiki 逐渐变大时，优先补齐 `concepts/` 和 `entities/`，但要避免过度原子化
