# Asana

## Purpose
Connector-specific rules for Asana Request nodes.

## When to use
Use this document when the requested ACE flow includes an Asana Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Asana Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_asana.msgnode`
- `applicationConnectorType="asana"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Asana Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Asana Request nodes:

- `displayName="Create task"` `action="CREATE"` `businessObject="Tasks"`
- `displayName="Retrieve tasks"` `action="RETRIEVEALL"` `businessObject="Tasks"`
- `displayName="Update task"` `action="UPDATEALL"` `businessObject="Tasks"`
- `displayName="Delete task"` `action="DELETEALL"` `businessObject="Tasks"`
- `displayName="Create project"` `action="CREATE"` `businessObject="Projects"`
- `displayName="Retrieve projects"` `action="RETRIEVEALL"` `businessObject="Projects"`
- `displayName="Update project"` `action="UPDATEALL"` `businessObject="Projects"`
- `displayName="Create attachment"` `action="CREATE"` `businessObject="Attachments"`
- `displayName="Retrieve attachments"` `action="RETRIEVEALL"` `businessObject="Attachments"`
- `displayName="Create tag"` `action="CREATE"` `businessObject="Tags"`
- `displayName="Update tag"` `action="UPDATEALL"` `businessObject="Tags"`
- `displayName="Create story"` `action="CREATE"` `businessObject="Stories"`
- `displayName="Retrieve stories"` `action="RETRIEVEALL"` `businessObject="Stories"`
- `displayName="Update story"` `action="UPDATEALL"` `businessObject="Stories"`
- `displayName="Delete story"` `action="DELETEALL"` `businessObject="Stories"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="Users"`
- `displayName="Retrieve teams"` `action="RETRIEVEALL"` `businessObject="Teams"`
- `displayName="Retrieve workspaces"` `action="RETRIEVEALL"` `businessObject="Workspaces"`
- `displayName="Update workspace"` `action="UPDATEALL"` `businessObject="Workspaces"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Asana1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="Asana1" policyTemplate="online_v1_basic_oauth" policyType="asana" shortDescription="" version="">
     <credentialName>AsanaCredential</credentialName>
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
