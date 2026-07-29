---
name: ace-java-compute
description: Use when the user wants to create or refine IBM App Connect Enterprise JavaCompute classes and related Java artifacts.
---

# ACE JavaCompute Skill

## Purpose
Use this skill when the user asks to create or modify Java artifacts for ACE JavaCompute nodes.

## When not to use this skill
- If the main request is to create or modify `.msgflow` structure, use [`skills/ace-message-flow/SKILL.md`](../ace-message-flow/SKILL.md) or [`skills/ace-connector-flows/SKILL.md`](../ace-connector-flows/SKILL.md).
- If the main request is ESQL Compute logic, use [`skills/ace-esql/SKILL.md`](../ace-esql/SKILL.md).

## Required reading order
1. [`skills/shared/java-guidelines.md`](../shared/java-guidelines.md)
2. [`skills/shared/review-checklist.md`](../shared/review-checklist.md)

## Critical rules
- Generate ACE-compatible Java code.
- Use clear package and class naming.
- Keep implementations simple and focused on the requested behavior.
- Do not introduce unnecessary abstractions.

## Output requirements
- Create or update the requested Java artifacts.
- Provide a concise summary of what was created or changed.
