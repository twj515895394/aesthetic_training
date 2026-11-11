# 13｜Markdown 元数据、标签与交叉关联规范

> **D-017 / Q-007 已确认（2026-11-11）**：采用 **Markdown + YAML front matter + 标签 + 交叉关联 + 索引**，不引入初期数据库，媒体资产仍然只保存在本地（D-016）。以下字段命名和标签枚举是可演进的**首版实施建议**，不表示已经完成实际训练或已经收集了作品。

## 1. 设计目标

一个案例不仅归属“摄影”目录，还可能关联「视觉焦点」「光影」和「留白」，并被多周课程反复引用。知识卡需要能够找到真实练习和相应的前后对照；训练记录需要追溯所用的主案例、对照案例与个人独立判断。

以 **稳定 ID 作为语义标识 + Markdown 相对链接作为可点击导航**，两者不可混淆：

- **ID**：用于关联、查找与以后生成索引，不因文件搬家而改变。
- **Markdown 链接**：用于在 GitHub 或本地编辑器点击查看另一份已存在的文档。不要创建指向尚不存在文件的“可点击链接”。
- **YAML 标签**：用于跨目录的全文搜索或日后可选的自动索引；保留一套受控词汇，避免同一概念同时出现 `negative-space`、`whitespace`、`留白` 三种不统一的 tag。

## 2. 身份 ID 与存储位置（已确认的是架构；格式为首版建议）

| 对象 | 建议 ID | 所在位置 | 例子说明 |
|---|---|---|---|
| 经典/个人案例 | `case-0001`、`case-0002` | `materials/classic/` / `materials/personal/` | 一件作品一个稳定 ID；重复研究不重复建卡 |
| 视觉知识点 | `visual-focus`、`negative-space` | `knowledge/` | 一个知识点一张卡 |
| 每日训练 | `W01-D01` | `practices/daily/` | 12 周第一轮中按周次/序号排列，不把实际日期当 ID |
| 实验 | `W01-D01-E01` | `practices/experiments/` | 同一天允许多次实验；具体格式可按需要简化 |
| 周复盘 | `W01-review` | `practices/reviews/` | 关联当周真实训练，而非根据日历自动认定已完成 |

不要让两个文档共用同一个 ID。移动文档时更新可点击链接；保留稳定 ID。

## 3. YAML 字段（首版建议）

### 案例卡：`materials/classic/*.md` 或 `materials/personal/*.md`

```yaml
---
id: case-0001
title: "作品名称（示例）"
creator: "作者或未知"
domain: painting
tags: [visual-focus, lighting]
related_concepts: [visual-focus, lighting]
related_sessions: [W01-D01]
source_url: "https://example.org/artwork"
license: unknown
local_media: ["local-assets/classic/case-0001/original.jpg"]
status: draft
---
```

这里的 URL、媒体路径与关联只是**结构演示**，不对应已经入库的真实作品。

### 知识卡：`knowledge/*.md`

```yaml
---
id: visual-focus
name: "视觉焦点"
tags: [composition, attention]
domain_tags: [painting, photography, graphic-design]
cases: [case-0001]
sessions: [W01-D01]
status: draft
---
```

### 每日训练：`practices/daily/*.md`

```yaml
---
id: W01-D01
date: YYYY-MM-DD
week: W01
day: D01
topic: "视觉焦点"
tags: [visual-focus, composition]
main_case_id: case-0001
compare_case_id: case-0002
related_concepts: [visual-focus]
practice_level: L1
local_media: []
status: draft
---
```

**注意**：YAML 中的 ID 和关联数组便于检索，不能自动保证 GitHub 能点击跳转；正文还应为**已存在的**案例卡、知识卡和训练记录补充相对 Markdown 链接。

## 4. 标签约束（初版建议）

- **领域维度**使用 `domain`（单值）：`painting`、`photography`、`film`、`illustration`、`graphic-design`、`advertising`、`architecture`、`product-design`、`fashion` 等。主案例与对照案例领域不同是课堂选材规则，不意味着一个作品只能涉及单一表达形式。
- **知识点维度**使用 `related_concepts`（稳定知识点 ID）：如 `visual-focus`、`negative-space`、`lighting`。
- **自由分类**使用 `tags`（数组）：只用于作品风格、构图、情绪等额外关键词，不重复塞入大量无关词；优先复用已存在词汇。
- **关联对象**使用 `related_sessions`、`cases`、`sessions` 和训练卡中的 `main_case_id`、`compare_case_id`，均填 **ID 而非文件路径**。
- **本机媒体路径**使用 `local_media`，填写相对于仓库根目录的路径，限制在本机使用；不当成 GitHub 图片 URL。
- **状态**建议 `draft` / `reviewed` 等，训练记录的正式归档须先经学员审核（D-012）；具体状态机待后续如有必要再定。

如出现新概念或跨领域术语，以一个新知识点 ID 为准；另名和中英文译法可写入知识卡正文，不任意产生重复概念卡。

## 5. 双向关联维护

当 `case-0001` 被用于 `W01-D01` 的主案例且涉及 `visual-focus` 时：

1. **训练卡**填 `main_case_id: case-0001` 和 `related_concepts: [visual-focus]`；正文链接已创建的对应案例卡与知识卡。
2. **案例卡**填 `related_concepts: [visual-focus]`、`related_sessions: [W01-D01]`；在“关联练习”里链接真实训练文件。
3. **知识卡**填 `cases: [case-0001]`、`sessions: [W01-D01]`，并在正文附指向实际案例与训练的 Markdown 链接。
4. **索引页**按领域、知识点和周次登记一条可点击的链接，避免搜索时只能靠记忆标题。

这套维护流程目前可由 AI 根据真实文件和学员审核后的笔记**提出修改草稿**；最终归档仍遵循 D-012 的审核约束。不要在训练尚未完成时预写所谓“学习成果”。

## 6. 索引入口

- [案例索引](../materials/index.md)：经典/个人作品，按领域、知识点链接。
- [知识点索引](../knowledge/index.md)：可从概念反查作品与练习。
- [训练索引](../practices/index.md)：按 Wxx-Dxx 查找真实练习和复盘。

初期手工维护即可，本地编辑器或 GitHub 搜索可使用 `case-0001`、`visual-focus`、`W01-D01` 等关键词。**未入库前不填虚构索引项**。等出现实际规模和检索痛点时，再考虑以脚本生成索引；这不是当前强制任务。

## 7. 数据质量与边界

- 不因来源链接可访问就认定有权公开上传图片；第三方媒体版权规则仍以 D-015/D-016 为准。
- 不把 AI 的艺术分析当成用户说过的话，也不虚构训练已完成。
- GitHub 远程只保留可公开的文字信息、本地路径的可公开相对表示；不得将本机私密绝对路径与含敏感信息的文件名放入公开文档。
- 某张作品反复练习时继续使用原案例 ID；若不同版本本身作为研究对象，明确记录其来源和关系。
- 字段定义、标签规范、索引自动生成脚本与 UI 仍可在真实素材增长后迭代。

## 8. 后续依赖

**Q-008** 将讨论如何开始、继续、补课并进入每周复盘；训练的进度与完成状态需要通过本规范的稳定 ID 和可验证练习记录追踪。
