# ACE Message Flow Rules

## Purpose
This document defines generic rules for creating `.msgflow` files for IBM App Connect Enterprise (ACE) Toolkit.

## When to use
Use this document for generic message flow creation and review before consulting connector-specific guidance.

## Artifact type
- Create ACE Toolkit `.msgflow` files.
- Do not confuse ACE Toolkit `.msgflow` files with ACE Designer YAML artifacts.

## Core rules
- Every node added to a message flow must use the exact validated `xmi:type` value for that node.
- Do not invent namespace prefixes or node type names.
- Do not rely on old example `.msgflow` files as the source of truth for `xmi:type`.
- Validate node type mappings against the ACE Message Flow schema for the relevant ACE version.

## Node type reference
Use [`skills/shared/node-types.md`](node-types.md) for the canonical node mapping list.

## Connector-specific rules
If the requested node is connector-specific, also read:
- [`skills/shared/connector-index.md`](connector-index.md)
- the relevant file under [`skills/shared/connectors/`](connectors)

## Simplicity
Use the minimum set of nodes required to satisfy the user's request.
- Do not add a Compute node or ESQL file unless the user explicitly asked for message transformation or routing logic.
- A direct wire from an Input node to a Reply node is the correct implementation of a pass-through or echo flow.
- Do not add nodes, files, or abstractions "just in case" — every node must trace directly to a stated requirement.

## Required inputs
If a node requires a value that the user has not provided, ask for it unless there is an obvious safe default.
For example:
- MQ Input nodes require a queue name.

## Validation
Before returning generated `.msgflow` content:
- confirm the node types are valid
- confirm connector-specific rules were applied where relevant
- confirm any required supporting artifacts were also created or identified
- apply the common checks in [`skills/shared/review-checklist.md`](review-checklist.md)

## Related files
- [`skills/shared/ace-versions.md`](ace-versions.md)
- [`skills/shared/node-types.md`](node-types.md)
- [`skills/shared/review-checklist.md`](review-checklist.md)
