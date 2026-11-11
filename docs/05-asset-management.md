# 05｜素材、案例、知识与实践资产管理规范

状态：**小型基础候选库 + 按课补充（D-015）和本地优先媒体存储（D-016）均已确认**；部分标签/字段及跨文件索引仍待 Q-007。

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
├── knowledge/             # 知识卡和概念之间的链接（同步）
└── local-assets/          # 本机创建的图片、视频与练习文件；gitignore，不同步
```

目录中的 README 会说明如何新增素材。Git 不追踪空目录，所以先使用 README 建立实际结构。

## 3. 案例获取与入库工作流（D-015 已确认）

1. **预备**：按本周视觉知识点和跨领域训练范围准备少量有可靠出处的候选案例，不要求一开始建成大规模素材全集。
2. **选用**：根据当天目标，从候选或新发现的作品中选一主案例、一不同领域对照；如有自选图片，也可作为当天个人案例。
3. **核验**：记录作品名、作者（未知则标未知）、尽量可信的原始来源、训练用途与许可状态；来源不明不杜撰；无法确认再分发许可，不上传图片实体。
4. **使用后沉淀**：为实际分析/练习的作品建立独立案例资料卡，关联当日训练和视觉概念；同一作品重复使用时复用案例卡、增加训练链接，不重复建卡。
5. **后续检索**：按周次、领域、知识点和练习目标检索；库的规模、字段粒度与选图质量指标可根据使用情况优化。

具体协议见 [11 案例获取与积累](11-case-acquisition.md)。媒体存储已经按 D-016 定案为**本地优先**，详见 [12 本地媒体管理](12-local-asset-storage.md)。

## 4. 命名方案（建议）

- 每日记录：`practices/daily/W01-D01-visual-focus.md`
- 经典案例：`materials/classic/vermeer-the-milkmaid.md`
- 个人案例：`materials/personal/2026-11-11-window-photo.md`
- 对比实验：`practices/experiments/W01-D01-crop-comparison.md`
- 概念知识卡：`knowledge/visual-focus.md`
- 周复盘：`practices/reviews/W01-review.md`

路径尽量使用简短的英文或拼音，正文用中文。不要把“已确认”写进无时间概念的素材文件名。

## 5. 必需的案例元数据（建议）

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

## 6. 案例与训练的关联关系

`case.id` ← `session.main_case_id / compare_case_id` → `experiment.id` → `knowledge.concept_id` → `review.week`

一张案例可复用在不同周，但保留每次观察记录；案例卡沉淀原作出处，训练卡保存当时任务与学习者结论。

## 7. 媒体文件本地优先（已确认 D-016）

- **GitHub**：保留 Spec、案例/训练/知识 Markdown 以及可公开的链接与元数据；不将其当作图片、音视频原始素材库。
- **本地**：clone 后在根目录创建 `local-assets/`，保存可合法持有的原始素材、标注、裁切、调色、AI 实验、视频与音频；该目录被 `.gitignore` 排除。
- **防误提交**：常见图片、视频、音频、设计文件扩展名也在 `.gitignore` 中默认排除；如未来特意发布少量合法轻量示意图，必须另外确认并检查授权。
- **关联方式**：案例卡记录可靠的 `source_url` 和可选的 `local_media` 仓库相对路径。GitHub 网页不会拥有这些本地媒体，不能将本地路径当作远程图片链接。
- **Git LFS / 云存储**：当前不引入，不额外要求同步大文件；`git clone` 不会恢复本机素材，需单独考虑备份和迁移。
- 禁止提交 API key、私人资料、未经授权的第三方媒体。如来源失效，保留原始出处记录，另找合法替代来源。

完整说明：[12 本地媒体管理](12-local-asset-storage.md)。

## 8. 双层训练档案入库（已确认原则，D-012）

1. 学员在练习中自然记录自己的观察、依据、选择和自评，不要求课后手工补写完整报告。
2. AI 根据当次真实对话与可验证素材整理详细 Markdown 草稿，保留个人观察与教练分析的来源分层。
3. 未完成的实验、未验证的图片来源、没有表达过的观点标记为缺项，不得凭空补全。
4. 学员审核草稿后再入库；不把 AI 草稿直接视作最终学习成果。
5. 精确字段、自动化提交方式、版本化细则仍可根据实践量进一步讨论。

## 9. 最小入库检查（建议）

- [ ] 标题、领域、作者/未知、出处链接
- [ ] 授权/版权状态明确
- [ ] 为什么选这张作品（研究主题）
- [ ] 今日观察与证据
- [ ] 如有改动，目标、改动项和对照结果
- [ ] 关联周次/知识点/个人复盘
