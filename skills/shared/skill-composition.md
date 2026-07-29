# ACE Skill Composition Guidance

## Purpose
This document defines how ACE skills must be combined when a request spans multiple artifact types.

## Routing by requested artifact
- Use [`skills/ace-project-setup/SKILL.md`](../ace-project-setup/SKILL.md) when the requested work includes Application or Policy project scaffolding.
- Use [`skills/ace-message-flow/SKILL.md`](../ace-message-flow/SKILL.md) when the requested work includes non-connector ACE Toolkit `.msgflow` files.
- Use [`skills/ace-connector-flows/SKILL.md`](../ace-connector-flows/SKILL.md) when the requested work includes connector-specific message flow nodes.
- Use [`skills/ace-esql/SKILL.md`](../ace-esql/SKILL.md) when the requested work includes `.esql` files, Compute node logic, or XMLNSC-to-JSON transformation logic.
- Use [`skills/ace-java-compute/SKILL.md`](../ace-java-compute/SKILL.md) when the requested work includes JavaCompute implementation.

## Composition rules
- If the request includes both `.msgflow` and `.esql` work, use both the relevant message flow skill and [`skills/ace-esql/SKILL.md`](../ace-esql/SKILL.md).
- If the request includes connector-specific flow work and Compute node implementation, use both [`skills/ace-connector-flows/SKILL.md`](../ace-connector-flows/SKILL.md) and the relevant compute skill.
- If the request includes project scaffolding and implementation artifacts, use [`skills/ace-project-setup/SKILL.md`](../ace-project-setup/SKILL.md) together with the relevant implementation skill or skills.
- Do not stop after creating only one artifact type when the request requires multiple related ACE artifacts.

## Precedence rules
- Connector-specific flow guidance takes precedence over generic message flow guidance when connector nodes are involved.
- Compute implementation guidance takes precedence over generic message flow guidance for `.esql` or JavaCompute artifacts.
- Project setup guidance applies whenever the required ACE Toolkit project structure or policy project artifacts do not yet exist.

## Workflow guidance
- Establish the required project or policy scaffolding first when it is missing.
- Apply the relevant message flow skill for `.msgflow` structure.
- Apply the relevant compute skill for Compute node implementation.
- Ensure the final output includes all requested and required supporting artifacts.
