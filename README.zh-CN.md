# Security Review Workflow

[English](./README.md) | 简体中文

Use when the current branch or PR needs a focused security review that minimizes false positives and only reports concrete, exploit-relevant issues.

## 这个技能是做什么的

Security Review Workflow 把 Claude Code 中可复用的一类工作流提取成独立 skill 仓库，方便在不同智能体环境里直接安装、复用和持续维护。

## 核心特点

- 聚焦单一能力边界，适合公开分发
- 仓库根目录就是 skill 根目录
- 内置 `agents/openai.yaml` 元数据
- 保留来源说明，便于追踪提取依据
- 提供中英文双语 README

## 擅长场景

- Run a high-signal security review on diffs
- 执行 `SKILL.md` 中定义的标准工作流
- 为智能体或操作者提供稳定、可复用的输出

## 示例请求

- Review this branch only for concrete security bugs.
- Find high-confidence vulnerabilities in the current diff and ignore noise.

## 工作流程

1. Collect git status, changed files, commit list, and full diff against the target base.
2. Research the codebase's existing security patterns.
3. Inspect only newly introduced attack surfaces in the diff.
4. Filter out speculative, low-signal, or excluded finding classes.
5. Report only concrete, actionable findings with file, severity, exploit path, and recommendation.

## 输入

- Diff against base
- Changed files
- Relevant security context

## 输出

- High-signal security findings
- Severity and exploit path
- Fix recommendations

## 成功标准

- Only concrete issues are reported.
- False positives are aggressively filtered.
- Each finding is actionable.

## 不适用场景

- General style review
- Speculative low-confidence security commentary

## 安装方式

### 作为独立 skill 使用

克隆本仓库，并将仓库根目录放入兼容的 skill 目录即可。

### 从合集仓库使用

该 skill 也收录在总仓库中：

- [claude-code-skills-extract](https://github.com/wimi321/claude-code-skills-extract)

## 仓库结构

- `SKILL.md`：技能主定义
- `README.md`：英文说明
- `README.zh-CN.md`：中文说明
- `agents/openai.yaml`：面向智能体 UI 的元数据
- `references/`：来源与补充说明
- `LICENSE`：开源许可证

## 来源说明

Derived from `src/commands/security-review.ts`.

## 相关项目

- 总仓库：[claude-code-skills-extract](https://github.com/wimi321/claude-code-skills-extract)
- 当前仓库：[security-review-workflow-skill](https://github.com/wimi321/security-review-workflow-skill)
