# Security Review Workflow

[![Repo](https://img.shields.io/badge/github-security-review-workflow-skill-181717?logo=github)](https://github.com/wimi321/security-review-workflow-skill)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](./LICENSE)
[![Collection](https://img.shields.io/badge/collection-claude--code--skills--extract-blue)](https://github.com/wimi321/claude-code-skills-extract)

Use when the current branch or PR needs a focused security review that minimizes false positives and only reports concrete, exploit-relevant issues.

English | [简体中文](./README.zh-CN.md)

## Why This Skill Exists

Security Review Workflow packages a reusable Claude Code workflow as a standalone public skill repository. It is designed for agent teams that want a well-documented, installable, and maintainable capability rather than an internal prompt fragment.

## Highlights

- Focused, reusable workflow with a clear trigger boundary
- Standalone skill root that works well in agent workspaces
- Agent metadata in `agents/openai.yaml`
- Public provenance back to the extracted Claude Code source
- Bilingual documentation for English and Chinese readers

## What It Is Good At

- Run a high-signal security review on diffs
- Running the workflow described in `SKILL.md` with explicit boundaries
- Producing repeatable outputs for operators and agent runtimes

## Example Requests

- Review this branch only for concrete security bugs.
- Find high-confidence vulnerabilities in the current diff and ignore noise.

## Workflow

1. Collect git status, changed files, commit list, and full diff against the target base.
2. Research the codebase's existing security patterns.
3. Inspect only newly introduced attack surfaces in the diff.
4. Filter out speculative, low-signal, or excluded finding classes.
5. Report only concrete, actionable findings with file, severity, exploit path, and recommendation.

## Inputs

- Diff against base
- Changed files
- Relevant security context

## Outputs

- High-signal security findings
- Severity and exploit path
- Fix recommendations

## Success Criteria

- Only concrete issues are reported.
- False positives are aggressively filtered.
- Each finding is actionable.

## Non-Goals

- General style review
- Speculative low-confidence security commentary

## Installation

### Use as a standalone skill

Clone this repository and place the repository root in a compatible skill directory.

### Use from a larger collection

This skill is also included in the parent collection:

- [claude-code-skills-extract](https://github.com/wimi321/claude-code-skills-extract)

## Repository Layout

- `SKILL.md`: canonical skill instructions
- `README.md`: English project overview
- `README.zh-CN.md`: Simplified Chinese project overview
- `agents/openai.yaml`: UI-facing metadata for agent runtimes
- `references/`: provenance and support notes
- `LICENSE`: repository license

## Provenance

Derived from `src/commands/security-review.ts`.

## Related Projects

- Parent collection: [claude-code-skills-extract](https://github.com/wimi321/claude-code-skills-extract)
- GitHub repository: [security-review-workflow-skill](https://github.com/wimi321/security-review-workflow-skill)
