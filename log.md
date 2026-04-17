# Wiki Log

> Chronological record of wiki actions.
> Format: `## [YYYY-MM-DD] action | subject`
> Actions: create, ingest, update, query, lint, archive

## [2026-04-15] create | Wiki initialized

- Scope: shared markdown wiki for the data development team
- Wiki root: `D:\Dropbox\Project\mdc_wiki`
- Created: `SCHEMA.md`, `index.md`, `log.md`
- Created directories: `raw/`, `raw/articles/`, `raw/papers/`, `raw/transcripts/`, `raw/assets/`, `entities/`, `concepts/`, `comparisons/`, `queries/`, `_archive/`

## [2026-04-15] update | Agent-first wiki architecture

- Added directories: `data-objects/`, `rules-and-metrics/`, `scenarios-and-projects/`, `capabilities/`, `standards/`
- Updated `SCHEMA.md` with bilingual naming and agent-first organization rules
- Rewrote `index.md` into mixed Chinese-English, agent-first navigation
- Prepared standards entry point for future page templates

## [2026-04-15] create | Ant selection pilot pages

- Created scenario page: `scenarios-and-projects/ant-selection-pilot.md`
- Created metric framework page: `rules-and-metrics/ant-selection-metric-framework.md`
- Created lane rule pages for `求赚纯债`、`求赚固收`、`定开场景`、`超额宝`、`增益宝`、`FOF`
- Created post-submission monitoring rule page covering warning ladders and drawdown exemptions
- Updated `index.md` to register the first pilot knowledge pages

## [2026-04-15] update | Raw archive and Chinese-first presentation

- Copied Ant selection source files into `raw/internal-docs/ant-selection/`
- Updated `SCHEMA.md` to require Chinese-first page content with English path stability
- Rewrote `index.md` to use Chinese-first descriptions and entry labels
- Updated page templates and data object writing guidance to prefer Chinese-first body content

## [2026-04-15] create | Ant selection verification cases

- Created `scenarios-and-projects/ant-selection-verification-cases.md`
- Added business-facing verification cases to prove agent can use skill + wiki for Ant selection Q&A
- Updated `index.md` to register the verification entry page

## [2026-04-17] update | Schema hardening for atomic pages and Chinese filenames

- Updated `SCHEMA.md` to add placement rules and atomic extraction triggers for `concepts/` and `entities/`
- Switched naming guidance from English-first filenames to Chinese-first filenames for new content
- Updated project and template guidance to prefer Chinese-primary content with English as supporting anchors

## [2026-04-17] update | 一级目录标准命名调整

- Updated `SCHEMA.md` to switch the preferred first-layer directory names to `tables/`, `rules/`, and `scenarios/`
- Updated project guidance and page templates to follow the new naming standard for future content
- Kept existing physical directories unchanged for now; this change only defines the new standard and migration direction

## [2026-04-17] update | 目录与文件名批量重构

- Renamed physical directories from `data-objects/`, `rules-and-metrics/`, `scenarios-and-projects/` to `tables/`, `rules/`, `scenarios/`
- Renamed first-layer page files to Chinese filenames and updated wiki links, `sources`, index entries, and local workspace paths
- Kept `SCHEMA.md`, `index.md`, `log.md`, and `AGENTS.md` as fixed control files for agent orientation and project governance

## [2026-04-17] create | 蚂蚁选品原子页首批补齐

- Added entity pages: `entities/蚂蚁渠道.md`, `entities/天相债基指数体系.md`, `entities/货币基金基准.md`
- Added concept pages: `concepts/滚动超额收益胜率.md`, `concepts/持有期正胜率.md`, `concepts/区间最大回撤.md`, `concepts/最大日回撤.md`, `concepts/平均含权仓位.md`, `concepts/定开豁免机制.md`
- Updated `index.md`, `rules/蚂蚁选品指标框架.md`, `scenarios/蚂蚁选品试点场景.md`, and key rule pages to link the new atomic pages

## [2026-04-17] create | 蚂蚁选品原子页第二批补齐

- Added entity pages: `entities/固收+组合基准.md`, `entities/中证纯债基金指数.md`
- Added concept pages: `concepts/封闭期正胜率.md`, `concepts/同类前50%替代条件.md`, `concepts/极端行情豁免.md`, `concepts/单一风险资产仓位.md`
- Updated the Ant scenario page, metric framework page, and related rule pages to link the second-batch atomic pages

## [2026-04-17] create | 蚂蚁选品原子页第三批补齐

- Added concept pages: `concepts/YTD回撤.md`, `concepts/单季报含权仓位.md`, `concepts/久期范围.md`, `concepts/基金合计规模.md`, `concepts/同策略产品佐证.md`
- Updated the Ant scenario page, metric framework page, and related rule pages to link the third-batch atomic pages

## [2026-04-17] create | 蚂蚁选品原子页第四批补齐

- Added concept pages: `concepts/基金经理公募经验.md`, `concepts/管理当前产品时长.md`, `concepts/持有期类型.md`, `concepts/封闭期类型.md`, `concepts/连续回撤天数.md`
- Updated the Ant scenario page, metric framework page, and related rule pages to link the fourth-batch atomic pages

## [2026-04-17] create | 蚂蚁选品原子页第五批补齐

- Added concept pages: `concepts/成立时长.md`, `concepts/投资年限.md`, `concepts/区间年化收益率.md`, `concepts/业绩基准达标.md`, `concepts/成立以来替代规则.md`
- Updated `index.md`, the Ant scenario page, the metric framework page, and related rule pages to link the fifth-batch atomic pages

## [2026-04-17] create | 蚂蚁选品原子页第六批补齐

- Added concept pages: `concepts/月度季度年度正收益概率.md`, `concepts/近1年收益.md`, `concepts/多资产类型产品经验.md`, `concepts/滚动1年平均含权仓位.md`
- Updated `index.md`, the Ant scenario page, the metric framework page, and related rule pages to link the sixth-batch atomic pages

## [2026-04-17] update | 收紧概念建页标准并合并家族页

- Updated `SCHEMA.md` to require concept pages to be independently explainable, family-oriented, and resistant to over-atomization
- Added merged concept pages: `concepts/基金经理资质要求.md`, `concepts/产品运作期限结构.md`, `concepts/仓位与暴露约束.md`
- Archived overly granular concept pages into `_archive/concepts/` and rewired active links, `index.md`, and related pages to the merged family pages

## [2026-04-17] create | 收紧标准后的概念与对象补充

- Added concept pages: `concepts/相对收益超额门槛.md`, `concepts/波动分层体系.md`, `concepts/预警分级机制.md`
- Added entity page: `entities/蚂蚁选品赛道体系.md`
- Updated `index.md`, the Ant scenario page, the metric framework page, and related rule pages to link the new family concepts and lane-system entity

## [2026-04-17] update | 高价值对象补充与规则页去重精修

- Added entity pages: `entities/纯债期限层级.md`, `entities/超额宝层级体系.md`
- Refined rule pages to move repeated object semantics out of `rules/` and into stable entity/concept pages while keeping thresholds in place
- Updated index, scenario page, related concept pages, and lane-system entity to link the new stable business objects
