# Microsoft To Do

## Purpose
Connector-specific rules for Microsoft To Do Request nodes.

## When to use
Use this document when the requested ACE flow includes a Microsoft To Do Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Microsoft To Do Request node

## Required node attributes
### Microsoft To Do Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_mstodo.msgnode`
- `applicationConnectorType="mstodo"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Microsoft To Do Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Microsoft To Do Request nodes:

- `displayName="Create list"` `action="CREATE"` `businessObject="List"`
- `displayName="Retrieve lists"` `action="RETRIEVEALL"` `businessObject="List"`
- `displayName="Retrieve list"` `action="RETRIEVE"` `businessObject="List"`
- `displayName="Update list"` `action="UPDATEALL"` `businessObject="List"`
- `displayName="Delete list"` `action="DELETEALL"` `businessObject="List"`
- `displayName="Create task"` `action="CREATE"` `businessObject="Task"`
- `displayName="Retrieve tasks"` `action="RETRIEVEALL"` `businessObject="Task"`
- `displayName="Retrieve task"` `action="RETRIEVE"` `businessObject="Task"`
- `displayName="Update task"` `action="UPDATEALL"` `businessObject="Task"`
- `displayName="Delete task"` `action="DELETEALL"` `businessObject="Task"`
- `displayName="Create file attachment"` `action="CREATE"` `businessObject="FileAttachment"`
- `displayName="Retrieve file attachments"` `action="RETRIEVEALL"` `businessObject="FileAttachment"`
- `displayName="Retrieve file attachment"` `action="RETRIEVE"` `businessObject="FileAttachment"`
- `displayName="Delete file attachment"` `action="DELETEALL"` `businessObject="FileAttachment"`
- `displayName="Create checklist item"` `action="CREATE"` `businessObject="ChecklistItem"`
- `displayName="Retrieve checklist items"` `action="RETRIEVEALL"` `businessObject="ChecklistItem"`
- `displayName="Retrieve checklist item"` `action="RETRIEVE"` `businessObject="ChecklistItem"`
- `displayName="Update checklist item"` `action="UPDATEALL"` `businessObject="ChecklistItem"`
- `displayName="Delete checklist item"` `action="DELETEALL"` `businessObject="ChecklistItem"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:MSToDo1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="MSToDo1" policyTemplate="online_v1_basic_oauth" policyType="mstodo" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <proxyId/>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
