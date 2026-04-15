# Data Objects Catalog｜数据对象目录说明

## Purpose｜用途

这个目录用于存放稳定、可被 agent 直接识别的数据对象资产。

典型对象包括：
- tables
- views
- source systems
- platforms
- field groups
- mapping tables
- enum dictionaries
- tag objects

## Organization｜组织方式

建议文件命名：
- `marketing-domain-data-objects-overview.md`
- `dwms-dim-rules-employee.md`
- `cr-tjj-qd-qdxx.md`

建议页面标题格式：
- `DWMS DIM RULES EMPLOYEE｜人员归属规则表`
- `CR TJJ QD QDXX｜渠道网点信息表`

## Writing Rules｜编写规则

- one object page per durable object
- do not mix multiple unrelated tables into one page unless it is an overview page
- always record platform, grain, key fields, and join gotchas
- link each object page to related rule pages and scenario pages

补充说明：
- 路径保持英文稳定
- 页面说明以中文为主
- 中文别名和关键词要覆盖业务同事的自然语言问法
