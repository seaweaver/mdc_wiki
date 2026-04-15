---
title: "Ant Selection Pilot｜蚂蚁选品试点场景"
aliases:
  - 蚂蚁选品
  - 蚂蚁提报
  - 蚂蚁渠道基金产品提报监控
  - 蚂蚁选品试点
created: 2026-04-15
updated: 2026-04-15
type: scenario
tags: [scenario, project, workflow, fund, strategy, retail, internal]
keywords: [蚂蚁选品, 蚂蚁提报, 蚂蚁稳健货架, 产品提报监控, ant selection, ant submission]
sources: []
status: active
---

# Ant Selection Pilot｜蚂蚁选品试点场景

## Overview｜概览

本场景用于把蚂蚁渠道基金产品提报监控材料，沉淀为可被 agent 检索、解释、串联和后续执行的知识页体系。

当前目标不是直接构建自动打标程序，而是先把规则、指标、赛道和提报后监控逻辑整理为结构化知识底座。

## Trigger and Goal｜触发条件与目标

触发条件：
- 蚂蚁渠道更新赛道准入要求
- 内部需要判断哪些基金可提报或即将可提报
- 运营同事需要对提报前、提报后进行持续监控

目标输出：
- 赛道准入规则清单
- 指标框架和口径目录
- 提报前预警与提报后预警逻辑
- 后续可演进的打标逻辑、规则配置和业务问答基础

## End-to-End Flow｜端到端流程

1. 读取原始业务规则文档和配套规则表
2. 将规则按赛道和阶段拆分
3. 识别每条规则所依赖的指标与对象
4. 形成“提报前判断”和“提报后监控”两套规则视图
5. 为后续产品标签、Skill、MCP、规则引擎留出接口

## Current Source Package｜当前来源材料

- 主文档：蚂蚁渠道基金产品提报监控 `.docx`
- 配套表格：
  - 工作表1：流程概要
  - 工作表2：数据指标
  - 工作表3：求赚纯债赛道
  - 工作表4：求赚固收赛道
  - 工作表5：定开场景
  - 工作表6：超额宝
  - 工作表7：增益宝
  - 工作表8：FOF 赛道
  - 工作表9：业绩考核目标
  - 工作表10：不同赛道对应的回撤豁免条件
  - 工作表11：分级触发阈值与对应动作

## Stage Design｜阶段设计

### Stage A｜准入前

包含两类预警：
- 培育产品预警：业务先配置培养产品清单，系统监控“即将满足”赛道准入条件的产品
- 提报产品预警：对创金产品池进行监控，当符合或接近符合某赛道准入条件时进行提示

### Stage B｜准入后

入池产品需要持续监控：
- 是否触发出池风险
- 是否进入一级、二级、三级预警
- 是否满足极端行情豁免条件

## Required Rules｜依赖规则页

- [[rules-and-metrics/ant-selection-metric-framework]]
- [[rules-and-metrics/ant-qiuzhuan-pure-bond-rule]]
- [[rules-and-metrics/ant-qiuzhuan-fixed-income-plus-rule]]
- [[rules-and-metrics/ant-dingkai-rule]]
- [[rules-and-metrics/ant-chaoebao-rule]]
- [[rules-and-metrics/ant-zengyibao-rule]]
- [[rules-and-metrics/ant-fof-rule]]
- [[rules-and-metrics/ant-post-submission-monitoring-rule]]

## Future Capabilities｜后续能力形态

后续可演进的能力包括：
- 产品可提报标签
- 赛道适配判断
- 边缘达标预警
- 提报后出池预警
- 极端行情豁免解释
- 面向业务同事的问答输出

## Current Gaps｜当前缺口

目前已经具备规则框架，但仍有待补齐：
- 具体数据来源与字段映射
- 各指标的实现 SQL 或脚本
- 产品标签输出样例
- 历史提报成功/失败经验
- 原始材料入 `raw/` 的归档版本

## Follow-up Assets｜后续沉淀资产

- 可提报标签对象页
- 赛道适配规则配置页
- 指标实现说明页
- 提报案例和出池案例页

