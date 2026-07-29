---
name: ace-esql
description: Use when the user wants to create or refine IBM App Connect Enterprise ESQL for Compute nodes using ACE-focused best practices.
---

# ACE ESQL Skill

## Purpose
Use this skill when the user asks to create or modify `.esql` files for ACE Compute nodes.

## When not to use this skill
- If the main request is to create or modify `.msgflow` structure, use [`skills/ace-message-flow/SKILL.md`](../ace-message-flow/SKILL.md) or [`skills/ace-connector-flows/SKILL.md`](../ace-connector-flows/SKILL.md).
- If the main request is JavaCompute logic, use [`skills/ace-java-compute/SKILL.md`](../ace-java-compute/SKILL.md).

## Required reading order
1. [`skills/shared/esql-guidelines.md`](../shared/esql-guidelines.md)
2. [`skills/shared/review-checklist.md`](../shared/review-checklist.md)

## Critical rules
- Generate ACE-compatible ESQL.
- Prefer simple, efficient, and maintainable ESQL.
- Avoid inventing nonexistent ESQL functions.
- Keep the response focused on the requested ESQL change.
- Preserve the requested transformation contract exactly; do not substitute a different output schema, domain, or business behavior.
- When the user provides a target pattern, expected output shape, or reference ESQL, follow that pattern instead of generating a generic example transformation.
- Preserve valid ACE ESQL constructs unless the requested change or the shared guidance requires otherwise.
- Do not invent compiler, parser, or unresolved identifier errors for valid ACE ESQL built-ins.
- Treat `FIELDVALUE(...)`, `LASTMOVE(...)`, `MOVE ... NEXTSIBLING NAME '...'`, `TYPE JSON.Object`, and `CREATE FIELD ... IDENTITY (JSON.Array)` as valid ACE ESQL constructs.
- Do not invent ACE JSON scalar type syntax such as `TYPE JSON.String`, `TYPE JSON.Number`, or `TYPE JSON.Boolean`.
- Create JSON scalar values with `SET` assignments rather than by inventing typed scalar nodes.
- Do not describe ACE ESQL fixes as replacing "SQL-like syntax" when the original syntax is valid ACE ESQL.
- For XMLNSC-to-JSON transformations, follow [`skills/shared/esql-guidelines.md`](../shared/esql-guidelines.md) exactly.
- For XMLNSC repeating elements, map every repeating element to a JSON array; do not flatten repeated values into concatenated strings.
- For XMLNSC-to-JSON array traversal, use `DECLARE ... REFERENCE TO ...[1]` with `WHILE LASTMOVE(...)` and `MOVE ... NEXTSIBLING NAME '...'`; do not use `FOR ... AS path[] DO`.
- Before populating any JSON array, create it explicitly with `CREATE FIELD ... IDENTITY (JSON.Array)`.
- When reading scalar values from XMLNSC for output to JSON, always use `FIELDVALUE(...)` rather than assigning the XML field reference directly.

## Output requirements
- Create or update the requested ESQL artifacts.
- Provide a concise summary of what was created or changed.
