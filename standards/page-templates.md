# Page Templates｜页面模板

## Purpose｜用途

This page defines canonical templates for the most important wiki page types.
Use these templates to keep the wiki consistent, searchable, and reusable by agents.

General rules:
- file path in English
- page title in bilingual form
- Chinese aliases and keywords for retrieval
- concise summary first, details later
- prefer links to object pages and rule pages instead of duplicating content

## Template A｜Rule / Metric Page

Use for:
- business rules
- metric definitions
- terminology with executable implications
- rule priority systems

```markdown
---
title: "English Anchor｜中文标题"
aliases:
  - 中文别名1
  - 中文别名2
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: rule
tags: [rule, metric, business, 中文标签]
keywords: [中文问法, English keyword, 口径, 规则]
sources: []
status: draft
---

# English Anchor｜中文标题

## Overview｜概览

一句话说明这条规则或指标是什么。

## Business Definition｜业务定义

说明业务含义、适用范围、边界条件。

## Rule Logic / Formula｜规则逻辑 / 计算口径

- 条件
- 阈值
- 优先级
- 例外情况

## Data Dependencies｜依赖数据对象

- [[data-objects/example-object]]
- [[entities/example-entity]]

## Gotchas｜易错点

- 易错点 1
- 易错点 2

## Related Scenarios｜关联场景

- [[scenarios-and-projects/example-scenario]]

## Sources｜来源

- raw or external source references
```

## Template B｜Data Object Page

Use for:
- tables
- views
- source systems
- mapping tables
- dictionaries
- tag objects

```markdown
---
title: "English Anchor｜中文标题"
aliases:
  - 中文对象名
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: data-object
tags: [data-object, table, datasource, 中文标签]
keywords: [表名, 字段, 数据源, English keyword]
sources: []
status: draft
---

# English Anchor｜中文标题

## Overview｜概览

一句话说明这个对象是什么、有什么用途。

## Platform and Location｜平台与位置

- platform:
- schema/database:
- object type:
- update frequency:

## Core Fields / Structure｜核心字段 / 结构

| field | meaning | notes |
| --- | --- | --- |
| example_field | 中文含义 | 备注 |

## Join Paths / Dependencies｜关联路径 / 依赖关系

- 与哪些对象关联
- 推荐关联方式
- 去重或过滤注意事项

## Usage Scenarios｜使用场景

- [[scenarios-and-projects/example-scenario]]

## Gotchas｜易错点

- 易错点 1
- 易错点 2

## Related Rules｜关联规则

- [[rules-and-metrics/example-rule]]
```

## Template C｜Scenario / Project Page

Use for:
- business scenarios
- implementation themes
- end-to-end project pages
- closed-loop workflows

```markdown
---
title: "English Anchor｜中文标题"
aliases:
  - 中文场景名
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: scenario
tags: [scenario, project, workflow, 中文标签]
keywords: [中文问法, 业务场景, English keyword]
sources: []
status: draft
---

# English Anchor｜中文标题

## Overview｜概览

一句话说明这个场景要解决什么问题。

## Trigger and Goal｜触发条件与目标

- 什么时候发生
- 要输出什么

## End-to-End Flow｜端到端流程

1. 输入是什么
2. 调用哪些数据对象
3. 使用哪些规则
4. 通过哪些能力交付
5. 结果如何回写

## Required Objects｜依赖对象

- [[data-objects/example-object]]
- [[entities/example-entity]]

## Required Rules｜依赖规则

- [[rules-and-metrics/example-rule]]

## Required Capabilities｜依赖能力

- [[capabilities/example-capability]]

## Risks and Gotchas｜风险与易错点

- 风险 1
- 风险 2

## Follow-up Assets｜后续沉淀资产

- queries
- comparisons
- new rules
- new data objects
```

## Bottom Line｜结论

If a page does not fit one template perfectly, choose the closest one and keep:
- bilingual title
- Chinese retrieval aliases
- explicit links to related objects, rules, and scenarios
