---
title: "Year-to-Date Drawdown｜YTD回撤"
aliases:
  - 年初至今回撤
  - 年度回撤
created: 2026-04-17
updated: 2026-04-24
type: concept
tags: [知识类型/概念, 知识类型/指标, 业务域/风控, 业务动作/监控, 资产类型/基金, 治理状态/生效]
keywords: [YTD回撤, 年初至今回撤, 年度回撤, year to date drawdown]
sources:
  - raw/internal-docs/ant-selection/蚂蚁渠道基金产品提报监控-工作表11分级触发阈值与对应动作.xlsx
status: active
---

# Year-to-Date Drawdown｜YTD回撤

## 定义｜Definition

YTD 回撤，是指从当年年初到当前监控时点，产品净值在年内发生的回撤幅度。

它是提报后监控中用于预警分级的年度视角风险指标。

## 为什么重要｜Why It Matters

在蚂蚁提报后监控场景里，YTD 回撤不是一般风险描述，而是直接驱动一级、二级、三级预警的核心阈值之一。

## 当前规则中的典型应用｜Current Rule Applications

当前已知分级预警表达包括：

- 第一阶梯：
  - 极低波 `0.5%`
  - 低波 `1.0%`
- 第二阶梯：
  - 极低波 `1.0%`
  - 低波 `1.5%`
  - 中波 `2.0%`
  - 高波 `4.0%`
- 第三阶梯：
  - 极低波 `1.5%`
  - 低波 `2.0%`
  - 中波 `3.0%`
  - 高波 `5.0%`

## 当前团队理解｜Current Team Understanding

YTD 回撤的核心是“年度窗口固定”，因此它和区间最大回撤不同：

- 区间最大回撤：统计窗口可变，常见是近 1/2/3 年或成立以来
- YTD 回撤：窗口固定为“当年起点到当前”

## 易错点｜Gotchas

- 不能把 YTD 回撤和近 1 年最大回撤混用
- 年初的起始日口径、节假日处理、净值缺失补法，都会影响结果
- 在极端行情场景下，YTD 回撤可能还要叠加特殊豁免逻辑

## 关联页面｜Related Pages

- [[rules/蚂蚁提报后监控规则]]
- [[rules/蚂蚁选品指标框架]]
- [[concepts/预警分级机制]]
- [[concepts/区间最大回撤]]
- [[concepts/极端行情豁免]]

## 来源｜Sources

- `raw/internal-docs/ant-selection/蚂蚁渠道基金产品提报监控-工作表11分级触发阈值与对应动作.xlsx`
