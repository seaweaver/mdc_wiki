# Page Templates｜页面模板

## Purpose｜用途

本页定义最重要的几类 wiki 页面模板。
这些模板的目标不是追求英文技术文档风格，而是让页面同时满足：
- 中文业务语义容易命中
- 英文路径和锚点稳定可复用
- agent 容易拆解、链接和组合

通用规则：
- 文件路径用英文
- 页面标题用中英混合
- 页面正文默认中文为主
- `aliases` 和 `keywords` 要优先覆盖中文问法
- 先写概览，再写细节
- 优先链接到对象页和规则页，而不是在场景页里重复解释一切

## Template A｜Rule / Metric Page

适用场景：
- 业务规则
- 指标口径
- 带可执行含义的术语
- 规则优先级体系

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

适用场景：
- 表
- 视图
- 数据源
- 映射表
- 字典
- 标签对象

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

适用场景：
- 业务场景
- 建设主题
- 端到端项目页
- 闭环流程页

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

如果某个页面不能完全套用某一个模板，至少保留这三点：
- 标题中英混合
- 中文检索别名完整
- 明确链接到相关对象页、规则页和场景页
