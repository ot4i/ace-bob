# ACE Subflow Rules

## Purpose
This document defines generic rules for creating `.subflow` files for IBM App Connect Enterprise (ACE) Toolkit.

## When to use
Use this document for generic subflow creation and review before consulting connector-specific guidance.

## Artifact type
- Create ACE Toolkit `.subflow` files.
- Do not confuse ACE Toolkit `.subflow` files with ACE Designer YAML artifacts.

## Core rules
- If a subflow is being created inside a shared library it MUST NOT be placed in the root of the shared library project (known as the ACE default broker schema). Instead, create the subflow in a named schema (subdirectory) in the shared library.
- Every subflow must contain at least one Input node which has an xmi:type of value eflow:FCMSource
- Every subflow must contain at least one Output node which has an xmi:type of value eflow:FCMSink
- Subflows are not allowed to just contain an Input node connected to an Output node
- If no further content has been requested, include a Passthrough node in the subflow (connected between the Input and Output) with xmi:type of ComIbmPassthru.msgnode:FCMComposite_1
- Every node added to a subflow must use the exact validated `xmi:type` value for that node.
- When an ACE Toolkit `.msgflow` file references a subflow, if the subflow is located in a separate shared library then the xmi:type of the subflow node in the .msgflow must incorporate the name of the shared library.
- For example if the subflow is named MySubflow.subflow and is located in shared library called MySharedLibrary then the xmi:type of the subflow node in the .msgflow should be `MySharedLibrary/MySubflow.subflow:FCMComposite_1`
- Do not invent namespace prefixes or node type names.
- Do not rely on old example `.subflow` files as the source of truth for `xmi:type`.
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
Before returning generated `.subflow` content:
- confirm the subflow contains an Input node which has an xmi:type of value eflow:FCMSource
- confirm the subflow contains an Output node which has an xmi:type of value eflow:FCMSink
- confirm that if the subflow is being created in a shared library it should not be placed in the default broker schema
- confirm the node types are valid
- confirm connector-specific rules were applied where relevant
- confirm any required supporting artifacts were also created or identified
- apply the common checks in [`skills/shared/review-checklist.md`](review-checklist.md)

## Examples 
When creating `.msgflow` content in an Application project note the example [`skills/shared/ExampleApplication/Example.msgflow`](Example.msgflow)
When creating `.msgflow` content in a REST API project note the example [`skills/shared/ExampleAPI/gen/ExampleAPI.msgflow`](ExampleAPI.msgflow)
When creating `.subflow` content in a REST API project note the example [`skills/shared/ExampleAPI/createWidget.subflow`](createWidget.subflow), [`skills/shared/ExampleAPI/retrieveWidget.subflow`](retrieveWidget.subflow), [`skills/shared/ExampleAPI/updateWidget.subflow`](updateWidget.subflow), [`skills/shared/ExampleAPI/deleteWidget.subflow`](deleteWidget.subflow)

## Related files
- [`skills/shared/ace-versions.md`](ace-versions.md)
- [`skills/shared/node-types.md`](node-types.md)
- [`skills/shared/review-checklist.md`](review-checklist.md)
- [`skills/shared/ExampleApplication/Example.msgflow`]
- [`skills/shared/ExampleAPI/gen/ExampleAPI.msgflow`]
- [`skills/shared/ExampleAPI/createWidget.subflow`]
- [`skills/shared/ExampleAPI/retrieveWidget.subflow`]
- [`skills/shared/ExampleAPI/updateWidget.subflow`]
- [`skills/shared/ExampleAPI/deleteWidget.subflow`]