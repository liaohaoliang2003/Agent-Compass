---
name: agent-compass
description: 用于项目启动或重组时建立项目级 Agent 规则、Skill/MCP/tool 选择、工具使用约束、可复用指南、AGENTS.md 入口与协作边界；适用于软件、数据、研究、内容、原型、产品和团队项目。
---

# Agent Compass

中文用户可阅读完整中文复刻版：`references/zh-CN.md`。

## Overview

Use this skill to initialize the Agent operating contract for a project before substantial work begins. It creates a compact navigation layer: what the project is, which sources are authoritative, which tools and Skills own which work, what future Agents must avoid, and how the root `AGENTS.md` points them to project rules.

This is not a feature-building, writing, research, or code-review skill. It prepares the project rules and tool boundaries that later task-specific skills must follow.

## When to Use

Use when the user is starting or reorganizing a project that may involve:

- setting up Agent behavior for a software, data, research, content, prototype, product, or mixed project;
- selecting, reusing, or installing Skills, MCP servers, browser workflows, CLIs, scripts, or local tools;
- defining how multiple tools should divide responsibility inside one project;
- creating project-level Skill/MCP/tool policy documents;
- creating a concise Agent master guideline;
- making future Agents reliably discover project rules through `AGENTS.md`.

Do not use this skill merely to complete an already-scoped implementation task, write one document section, run one existing command, or invoke an already-defined tool.

## Core Workflow

### 1. Identify the project shape

Establish the project type, target outputs, audience, success criteria, current materials, delivery pressure, and evidence sources. Treat software, research, data, writing, design, operations, and mixed projects as equal first-class cases.

### 2. Inspect before asking

Read the existing repository, docs, configs, prompts, rules, schemas, templates, scripts, prior `AGENTS.md`, and project notes before asking questions that can be answered locally.

After inspection, ask only questions that materially change project rules or tool selection:

- What output must this project produce: app, package, dataset, report, paper, dashboard, prototype, automation, documentation, or mixed deliverable?
- Which files, docs, datasets, designs, comments, tickets, or conversations are authoritative?
- Which materials are outdated, borrowed, partial, generated, examples only, or unsafe to trust?
- Which tools are allowed: web search, local scripts, browser automation, MCP servers, paid services, subagents, private APIs, or external accounts?
- What must future Agents never claim, modify, publish, delete, infer, or assume?
- What verification evidence is required before work can be called done?

Ask one high-impact question at a time when possible.

### 3. Inventory the existing environment

Before recommending new tools, inspect what already exists:

- installed Codex/Claude skills, `superpowers`, and project-local skills;
- enabled MCP servers, browser plugins, CLIs, local scripts, runtimes, and service configs;
- project docs, templates, drafts, datasets, designs, issue references, and existing rules;
- current `AGENTS.md`, policy docs, workflow docs, and generated guidance;
- local runtime needs for builds, tests, browsers, documents, PDFs, spreadsheets, data processing, or deployment.

Summarize usable existing tools first. Avoid installing duplicates when an existing tool can be governed by a project-level policy.

### 4. Evaluate new or reused tools

When a Skill, MCP, CLI, script, browser workflow, API, or app may help, evaluate it by:

- fit to the project type, target output, and success criteria;
- maintenance state, documentation quality, license, and trust surface;
- install shape and operational cost;
- permissions, credentials, network access, and data exposure required;
- overlap with tools already installed or already trusted;
- whether it should be a main workflow owner or a narrow auxiliary tool.

Prefer official documentation, primary repositories, and local evidence. Clearly distinguish evidence from inference.

### 5. Write project-level tool policies

For every newly installed or important reused Skill/MCP/tool, create a project-level policy document. The policy defines how that tool is used in this project without changing its global behavior.

Minimum policy sections:

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

If a tool touches paid services, restricted content, private data, production systems, credentials, downloads, publishing, or destructive operations, record lawful-access and approval requirements. Never make bypassing restrictions the default.

### 6. Write the Agent master guideline and `AGENTS.md` entry

Create a short master guideline for future Agents. Keep it principle-level; do not duplicate every tool policy.

The master guideline should contain only:

- project identity and target outputs;
- core facts or assumptions future Agents must lock;
- source-of-truth priority;
- forbidden claims, actions, shortcuts, and unsafe assumptions;
- Agent working principles;
- Skill/MCP/tool division of labor;
- default file locations for outputs;
- final verification principles;
- when to stop and ask the user.

Then create or update the repository root `AGENTS.md` with a short entry rule:

```markdown
## Project Agent Entry Rule

For any task related to this project, its code, data, documents, designs, workflows, tools, automation, or Agent setup, first read and follow:

`docs/agent_guidelines/<master-guideline>.md`

Then consult the relevant project-level Skill/MCP/tool policy under:

`docs/agent_policies/`
```

`AGENTS.md` should be the doorway, not the warehouse.

## Research Project Variant

For research, thesis, dissertation, paper, literature review, or lab projects, keep the core workflow above and add only the research-specific boundaries needed for the project:

- identify the research object, discipline, venue or institution requirements, advisor feedback, and expected academic output;
- distinguish templates, drafts, code, data, PDFs, lab notes, reference papers, review comments, and examples by authority level;
- document evidence rules for claims, citations, experiments, figures, and reproduced results;
- record legal-access boundaries for CNKI, publisher sites, library accounts, Zotero libraries, downloaded PDFs, private datasets, and collaborator materials;
- prevent literature tools from inferring conclusions from titles or abstracts alone.

Research projects may add paths such as `docs/research_references/`, `docs/research_drafts/`, and `docs/research_figures/` when useful, but the general Agent guideline and policy structure still apply.

## Output Conventions

Use stable project paths such as:

```text
docs/agent_guidelines/
docs/agent_policies/
docs/project_context/
docs/project_checks/
```

Adapt names to local conventions. Avoid scattering temporary outputs in the project root.

## Common Mistakes

- Installing tools before understanding the project and existing environment.
- Letting multiple Skills or MCP tools become competing project managers.
- Treating a tool's global default behavior as more authoritative than project facts.
- Writing policy docs that say what a tool can do globally instead of how it is allowed to act here.
- Writing a master guideline so long that future Agents skip it.
- Forgetting the root `AGENTS.md` entry, so future Agents never discover the guideline.
- Leaving destructive, production, credential, privacy, or copyright boundaries implicit.
- Assigning overlapping main ownership without a clear handoff rule.

## Completion Checklist

Before claiming setup is complete, verify:

- the project type, target outputs, source priorities, and success criteria are recorded;
- chosen Skills/MCP/tools are installed, reused, or explicitly out of scope;
- each important tool has a project-level policy document;
- the master guideline is concise and contains the key facts, boundaries, tool division, file locations, and verification principles;
- root `AGENTS.md` points future Agents to the master guideline and policy directory;
- no tool is assigned overlapping main ownership without a clear boundary;
- restricted access, credentials, privacy, copyright, production, and destructive-action limits are documented;
- all created files are readable and free of mojibake or replacement characters.
