---
name: ace-project-setup
description: Use when the user wants to create IBM App Connect Enterprise Toolkit application or policy project scaffolding with the correct Eclipse metadata and descriptors.
---

# ACE Project Setup Skill

## Purpose
Use this skill when the user asks to create or modify ACE Toolkit Application projects or Policy projects.

## When not to use this skill
- If the main request is to implement message flow logic, use [`skills/ace-message-flow/SKILL.md`](../ace-message-flow/SKILL.md) or [`skills/ace-connector-flows/SKILL.md`](../ace-connector-flows/SKILL.md).
- If the main request is to implement Compute node logic, use [`skills/ace-esql/SKILL.md`](../ace-esql/SKILL.md) or [`skills/ace-java-compute/SKILL.md`](../ace-java-compute/SKILL.md).

## Required reading order
1. [`skills/shared/skill-composition.md`](../shared/skill-composition.md)
2. [`skills/shared/ace-versions.md`](../shared/ace-versions.md)
3. [`skills/shared/ace-projects.md`](../shared/ace-projects.md)
4. [`skills/shared/policy-projects.md`](../shared/policy-projects.md)
5. [`skills/shared/review-checklist.md`](../shared/review-checklist.md)

## Critical rules
- Create the correct ACE Toolkit project type for the requested task.
- Do not omit required Eclipse metadata files.
- Use the validated `.project`, `.settings`, and descriptor structures from the shared guidance.
- If the request also includes message flow or Compute implementation work, continue with the relevant implementation skill after establishing the required project scaffolding.
- If version-specific behavior matters and the ACE version is not known, ask the user.

## Output requirements
- Create or update the requested project scaffolding artifacts.
- Provide a concise summary of what was created or changed.
- If a new Application project was created, include the ACE Toolkit import guidance.
