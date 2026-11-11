# 视觉审美训练 | Aesthetic Training

一个以**真实作品、跨领域对照、主动观察与动手实验**为核心的长期视觉审美学习项目。目标是培养独立审美判断力、视觉表达力和创作能力，而不是只学习 AI 生图技巧或电影理论。

> 项目状态：**规划与 Grill Me 决策持续进行中**（2026-11-11）。文档按“已确认 / 建议待确认 / 待讨论”区分；不要把建议误认成既定规则。

## 快速入口

- [文档导航与当前进度](docs/README.md)
- [学习目标、范围与原则](docs/01-vision-and-principles.md)
- [12 周首轮学习路线](docs/02-roadmap-12-weeks.md)
- [每日 20–30 分钟训练协议](docs/03-daily-protocol.md)
- [案例组织与三级实战训练](docs/04-case-and-practice.md)
- [素材与知识资产管理规范](docs/05-asset-management.md)
- [第 1 周训练计划草案](docs/06-week01-plan.md)
- [决策日志（确认/建议/待讨论）](docs/07-decision-log.md)
- [开放问题与下一轮 Grill](docs/08-open-questions.md)
- [评估与复盘机制](docs/09-assessment-and-review.md)
- [固定主线与自适应强化](docs/10-adaptive-training.md)
- [案例获取与积累规范](docs/11-case-acquisition.md)
- [本地媒体管理与 GitHub 分工](docs/12-local-asset-storage.md)
- [Markdown 元数据、标签与交叉索引](docs/13-metadata-and-indexing.md)
- [案例索引](materials/index.md) · [知识点索引](knowledge/index.md) · [训练索引](practices/index.md)
- [训练模板](docs/templates/README.md)

## 项目结构（持续扩展）

```text
aesthetic_training/
├── README.md
├── docs/                  # 课程规格、规则、路线、决策日志、模板
├── materials/             # 学习案例卡、参考链接、来源及授权说明（同步）
├── practices/             # 每日训练、实验说明与复盘 Markdown（同步）
├── knowledge/             # 知识卡片（同步）
└── local-assets/          # clone 后在本地创建；图片/视频/改图等，gitignore，不同步
```

本项目采用 **Spec-as-Learning**：先记录设计共识，边讨论边更新规格；每次训练写入案例、实验与复盘；定期回顾并修订训练策略。

## 已确认关键约束

- 第一轮 **12 周**，不把 12 周当成审美训练的终点。
- **每天 20–30 分钟**；每周 **4 天精选案例 + 2 天个人案例 + 1 天复盘**。
- 案例跨越摄影、电影、绘画、插画、平面设计等领域；不局限于 AI 视频。
- **每天 1 个主案例 + 1 个跨领域对照案例**，围绕同一视觉问题。
- 教学采用**混合引导，以苏格拉底式提问为主**；新知识可先示范，随后独立分析。
- 实战采用**分层方案 C**：观察标注 → 单变量实验 → 复刻或自由创作；不是每天强制做完三级。
- 训练闭环：**观察 → 拆解 → 适量理论 → 实验 → 复盘**。
- 评估采用**证据驱动的混合机制**，每日留痕、每周陌生案例与迁移任务、W04/W08/W12 阶段回顾。
- 自适应训练采用**固定主线 + 薄弱项补练 + 逐步加难**；不破坏 12 周主题和 20–30 分钟时长。
- 案例积累采用**小型基础候选库 + 按课即时补充**；使用后建立资料卡，保留来源与授权信息，不在开课前堆砌素材。
- 素材采取**本地优先**：GitHub 同步 Markdown 规范、案例索引和训练笔记；原图、图片、视频、改图文件主要在本机 `local-assets/` 维护，不向 GitHub 同步大文件。
- 检索采用 **Markdown + YAML 元数据 + 标签 + 稳定 ID + 双向链接**，可以从知识点、案例或训练记录相互查找，不需要数据库。

## 内容与版权

GitHub 是公开文档仓库：对不具备再分发授权的外部作品，仅同步**来源链接、引用信息及原创分析笔记**；图片、视频、原图和改图默认放本机被 Git 忽略的 `local-assets/`，不提交大文件。当前不需要 Git LFS。**注意**：远程 clone/pull 不能恢复本机媒体，需另行备份。

## 贡献方式

每完成一个 Grill Me 决策，先更新 [决策日志](docs/07-decision-log.md)，再更新对应的规格；每次新素材入库都带来源、授权、用途和关联知识点。正在讨论的方案标记为「草案」，不要悄悄升级为「已确认」。
