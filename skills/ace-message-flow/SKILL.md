---
name: ace-message-flow
description: Use when the user wants to create or modify IBM App Connect Enterprise Toolkit .msgflow files using validated node types and ACE Toolkit conventions.
---

# ACE Message Flow Skill

## Purpose
Use this skill when the user asks to create or modify ACE Toolkit `.msgflow` files that do not require connector-specific policy guidance.

## When not to use this skill
- If the request includes connector-specific nodes, use [`skills/ace-connector-flows/SKILL.md`](../ace-connector-flows/SKILL.md).
- If the request is primarily about project scaffolding, use [`skills/ace-project-setup/SKILL.md`](../ace-project-setup/SKILL.md).

## Required reading order
1. [`skills/shared/skill-composition.md`](../shared/skill-composition.md)
2. [`skills/shared/ace-versions.md`](../shared/ace-versions.md)
3. [`skills/shared/message-flow-rules.md`](../shared/message-flow-rules.md)
4. [`skills/shared/node-types.md`](../shared/node-types.md)
5. [`skills/shared/review-checklist.md`](../shared/review-checklist.md)

## Critical rules
- Create ACE Toolkit `.msgflow` files, not ACE Designer YAML.
- Do not invent `xmi:type` values or namespace prefixes.
- Validate node types using the ACE version guidance and shared node type reference.
- Ask for missing required node values when there is no obvious safe default.
- Do not use this skill alone when the request also requires Compute node implementation.
- If the request includes Compute node ESQL creation or modification, also use [`skills/ace-esql/SKILL.md`](../ace-esql/SKILL.md) and apply its guidance for the `.esql` artifact.

## Output requirements
- Create or update the requested message flow artifacts.
- Provide a concise summary of what was created or changed.
- State any important assumptions that were required.
