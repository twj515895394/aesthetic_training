# 05｜素材、案例、知识与实践资产管理规范

状态：**目录方案与元数据为首版建议规范，已作为初始化结构落地；后续可继续 Grill 修改**。

## 1. 存储目标

让“看过的作品、学到的原理、自己改过的图”互相关联，能按照**周次、知识点、领域、作者、作品、个人复盘**快速找回。

不要把本项目仅当图片相册，也不要让图片和笔记互相脱节。

## 2. 建议目录

```text
aesthetic_training/
├── docs/
│   ├── 01-vision-and-principles.md
│   ├── 02-roadmap-12-weeks.md
│   ├── 03-daily-protocol.md
│   ├── 04-case-and-practice.md
│   ├── 05-asset-management.md
│   ├── 06-week01-plan.md
│   ├── 07-decision-log.md
│   ├── 08-open-questions.md
│   └── templates/
├── materials/
│   ├── classic/           # 经典/精选作品来源卡；可授权图片
│   └── personal/          # 个人收集的图片/作品来源卡
├── practices/
│   ├── daily/             # W01-D01 这类每日记录
│   ├── experiments/       # 单变量前后对比、练习项目
│   └── reviews/           # 每周与阶段复盘
└── knowledge/             # 知识卡和概念之间的链接
```

目录中的 README 会说明如何新增素材。Git 不追踪空目录，所以先使用 README 建立实际结构。

## 3. 命名方案（建议）

- 每日记录：`practices/daily/W01-D01-visual-focus.md`
- 经典案例：`materials/classic/vermeer-the-milkmaid.md`
- 个人案例：`materials/personal/2026-11-11-window-photo.md`
- 对比实验：`practices/experiments/W01-D01-crop-comparison.md`
- 概念知识卡：`knowledge/visual-focus.md`
- 周复盘：`practices/reviews/W01-review.md`

路径尽量使用简短的英文或拼音，正文用中文。不要把“已确认”写进无时间概念的素材文件名。

## 4. 必需的案例元数据（建议）

```yaml
---
id: case-0001
title: The Milkmaid
creator: Johannes Vermeer
domain: painting
source_url: https://...
license: link-only
rights_note: "仅保存原作链接与自写分析，未引入原作图片"
related_concepts: [visual-focus, lighting]
related_sessions: [W01-D01]
status: draft
---
```

必需信息：作品名、作者（未知则写未知）、领域、可靠来源链接、授权状态、关联训练。其他元数据按需扩充。

建议许可值：`link-only`（仅链接），`public-domain`，`cc0`，`cc-by`（需满足署名），`own-work`，`permission-granted`，`unknown`（不提交原图）。不要将网站可浏览或可下载等同于可重新发布。

## 5. 案例与训练的关联关系

`case.id` ← `session.main_case_id / compare_case_id` → `experiment.id` → `knowledge.concept_id` → `review.week`

一张案例可复用在不同周，但保留每次观察记录；案例卡沉淀原作出处，训练卡保存当时任务与学习者结论。

## 6. 图片与大文件

- **公开仓库**：只提交自己持有权利或经明确授权的原始媒体；其他优先用链接、文字分析、自绘简图。
- 原始素材、裁切、调色或 AI 实验结果，若有合法再分发权限，可按实践编号组织版本。
- 目前**未决定**使用 Git LFS、大文件上限、对象存储或外部资产系统；这些后续需依据体量/版权/成本单独 Grill。
- 禁止提交任何 API key、个人隐私、未经许可的第三方媒体。
- 如来源失效，案例卡保留原始出处与记录日期，另附可合法替代的来源。

## 7. 最小入库检查（建议）

- [ ] 标题、领域、作者/未知、出处链接
- [ ] 授权/版权状态明确
- [ ] 为什么选这张作品（研究主题）
- [ ] 今日观察与证据
- [ ] 如有改动，目标、改动项和对照结果
- [ ] 关联周次/知识点/个人复盘
