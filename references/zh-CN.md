# Agent Compass 中文复刻版

## 概览

使用本 Skill 在一个项目进入实质性工作之前，先初始化项目级 Agent 操作契约。它要建立一层简洁的导航规则：这个项目是什么，哪些资料最权威，哪些工具和 Skill 负责哪些任务，未来 Agent 必须避免什么，以及根目录 `AGENTS.md` 如何引导 Agent 读取项目规则。

本 Skill 不是功能开发、论文写作、资料检索或代码审查 Skill。它负责准备项目规则和工具边界，后续具体任务再交给对应的专门 Skill 或工具执行。

## 适用场景

当用户正在启动或重组一个项目，并且出现以下需求时使用：

- 为软件、数据、研究、内容、原型、产品或混合项目设置 Agent 行为规则；
- 选择、复用或安装 Skill、MCP server、浏览器工作流、CLI、脚本或本地工具；
- 定义多个工具在同一个项目中的职责分工；
- 创建项目级 Skill/MCP/tool 使用政策文档；
- 创建简洁的 Agent master guideline；
- 让未来 Agent 能通过 `AGENTS.md` 稳定发现项目规则。

不要仅因为用户要完成一个已经明确的实现任务、写一个文档段落、运行一个现成命令，或调用一个已经定义好的工具，就使用本 Skill。

## 核心流程

### 1. 识别项目形态

先确定项目类型、目标产物、受众、成功标准、现有材料、交付压力和证据来源。软件、研究、数据、写作、设计、运营和混合项目都应作为一等场景处理。

### 2. 先检查，再提问

在提问前，先阅读现有仓库、文档、配置、prompt、规则、schema、模板、脚本、旧 `AGENTS.md` 和项目笔记。不要询问可以从本地环境中直接发现的信息。

检查后，只问会实质改变项目规则或工具选择的问题，例如：

- 这个项目最终要产出什么：app、package、dataset、report、paper、dashboard、prototype、automation、documentation，还是混合交付物？
- 哪些文件、文档、数据集、设计稿、评论、ticket 或对话是权威来源？
- 哪些材料已经过时、借用自其他项目、不完整、由 AI 生成、仅作示例，或不应被信任？
- 哪些工具被允许使用：web search、本地脚本、浏览器自动化、MCP server、付费服务、subagents、私有 API 或外部账号？
- 未来 Agent 绝不能声称、修改、发布、删除、推断或假设什么？
- 声称任务完成前，需要哪些验证证据？

尽量一次只问一个高影响问题。

### 3. 盘点现有环境

在推荐新工具之前，先检查已有资源：

- 已安装的 Codex/Claude skills、`superpowers` 和项目本地 skills；
- 已启用的 MCP server、浏览器插件、CLI、本地脚本、运行时和服务配置；
- 项目文档、模板、草稿、数据集、设计稿、issue 引用和已有规则；
- 当前 `AGENTS.md`、policy 文档、workflow 文档和生成式指导；
- 构建、测试、浏览器、文档、PDF、表格、数据处理或部署所需的本地运行时。

先总结已经可用的工具。若已有工具可以通过项目级 policy 管好，就不要重复安装同类工具。

### 4. 评估新增或复用工具

当某个 Skill、MCP、CLI、脚本、浏览器工作流、API 或 app 可能有帮助时，按以下维度评估：

- 是否匹配项目类型、目标产物和成功标准；
- 维护状态、文档质量、license 和信任边界；
- 安装方式和运行成本；
- 需要哪些权限、凭证、网络访问和数据暴露；
- 是否与已安装或已信任的工具重叠；
- 应作为主工作流负责人，还是只作为窄范围辅助工具。

优先使用官方文档、主仓库和本地证据。清楚区分“有证据支持的事实”和“基于上下文的推断”。

### 5. 编写项目级工具政策

对每个新安装或重要复用的 Skill/MCP/tool，创建项目级 policy 文档。policy 只定义该工具在本项目中的使用方式，不改变它的全局行为。

最小 policy 模板：

```markdown
# <tool-name> 项目级使用约束

适用项目：<project>
目标产物：<deliverable>
生成日期：<date>

## 1. 安装状态
- source
- install path or config location
- restart / credential notes

## 2. 本项目中的定位
- what it is responsible for
- what it is not responsible for

## 3. 使用边界
- access, privacy, copyright, safety, production, or data limits
- when to stop and ask the user

## 4. 与其他 Skill/MCP/工具的分工
- main owner for each task type
- overlap prevention

## 5. 推荐产物与验证
- where outputs should be saved
- required evidence, tests, citations, screenshots, logs, or review checks
```

如果工具涉及付费服务、受限内容、私有数据、生产系统、凭证、下载、发布或破坏性操作，必须记录合法访问和审批要求。不要把绕过限制当成默认路径。

### 6. 编写 Agent master guideline 和 `AGENTS.md` 入口

为未来 Agent 创建一份简短的 master guideline。它应该保持原则级别，不要重复每个工具 policy 的全部内容。

master guideline 只包含：

- 项目身份和目标产物；
- 未来 Agent 必须锁定的核心事实或假设；
- source-of-truth 优先级；
- 禁止的声明、操作、捷径和不安全假设；
- Agent 工作原则；
- Skill/MCP/tool 职责分工；
- 输出文件的默认位置；
- 最终验证原则；
- 何时必须停止并询问用户。

然后在仓库根目录创建或更新 `AGENTS.md`，加入简短入口规则：

```markdown
## Project Agent Entry Rule

For any task related to this project, its code, data, documents, designs, workflows, tools, automation, or Agent setup, first read and follow:

`docs/agent_guidelines/<master-guideline>.md`

Then consult the relevant project-level Skill/MCP/tool policy under:

`docs/agent_policies/`
```

`AGENTS.md` 应该是入口，不是仓库。它只负责让未来 Agent 知道先读哪里。

## 研究项目变体

对于研究、毕业论文、学位论文、paper、literature review 或实验室项目，仍然使用上面的通用流程，只额外补充研究项目需要的边界：

- 明确研究对象、学科、投稿 venue 或学校要求、导师反馈和预期学术产物；
- 区分模板、草稿、代码、数据、PDF、实验笔记、参考论文、审稿意见和示例材料的权威级别；
- 记录学术声明、引用、实验、图表和复现结果所需的证据规则；
- 记录 CNKI、出版社网站、图书馆账号、Zotero library、下载 PDF、私有数据集和合作者材料的合法访问边界；
- 防止文献工具仅根据标题或摘要推断论文结论。

研究项目可以按需增加 `docs/research_references/`、`docs/research_drafts/`、`docs/research_figures/` 等路径，但通用 Agent guideline 和 policy 结构仍然适用。

## 输出路径约定

优先使用稳定路径：

```text
docs/agent_guidelines/
docs/agent_policies/
docs/project_context/
docs/project_checks/
```

可以根据项目已有约定调整命名。避免把临时输出散落在项目根目录。

## 常见错误

- 在理解项目和现有环境之前就安装工具。
- 让多个 Skill 或 MCP tool 变成相互竞争的项目管理者。
- 把工具的全局默认行为看得比项目事实更权威。
- policy 文档只写工具“全局能做什么”，没有写“在本项目中允许怎么做”。
- master guideline 写得太长，导致未来 Agent 不愿阅读。
- 忘记根目录 `AGENTS.md` 入口，导致未来 Agent 找不到 guideline。
- 没有显式记录破坏性操作、生产环境、凭证、隐私或版权边界。
- 给多个工具分配重叠主责，却没有清楚的交接规则。

## 完成检查清单

声称项目 Agent 设置完成前，确认：

- 已记录项目类型、目标产物、source-of-truth 优先级和成功标准；
- 选定的 Skill/MCP/tool 已安装、已复用，或明确标记为不在范围内；
- 每个重要工具都有项目级 policy 文档；
- master guideline 简洁，并包含关键事实、边界、工具分工、文件位置和验证原则；
- 根目录 `AGENTS.md` 指向 master guideline 和 policy 目录；
- 没有工具被分配重叠主责，除非有清楚边界；
- 已记录受限访问、凭证、隐私、版权、生产环境和破坏性操作限制；
- 所有创建文件都可读，并且没有 mojibake 或 replacement character。
