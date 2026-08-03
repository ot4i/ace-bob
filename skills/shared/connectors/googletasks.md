# Google Tasks

## Purpose
Connector-specific rules for Google Tasks Request nodes.

## When to use
Use this document when the requested ACE flow includes a Google Tasks Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Google Tasks Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_googletasks.msgnode`
- `applicationConnectorType="googletasks"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Google Tasks Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Google Tasks Request nodes:

- `displayName="Retrieve task lists"` `action="RETRIEVEWITHWHERE"` `businessObject="Task lists"`
- `displayName="Create task list"` `action="CREATE"` `businessObject="Task lists"`
- `displayName="Retrieve task list by ID"` `action="RETRIEVE"` `businessObject="Task lists"`
- `displayName="Update task list"` `action="UPDATE"` `businessObject="Task lists"`
- `displayName="Delete task list"` `action="DELETE"` `businessObject="Task lists"`
- `displayName="Retrieve tasks"` `action="RETRIEVEWITHWHERE"` `businessObject="Tasks"`
- `displayName="Create task"` `action="CREATE"` `businessObject="Tasks"`
- `displayName="Retrieve task by ID"` `action="RETRIEVE"` `businessObject="Tasks"`
- `displayName="Update task"` `action="UPDATE"` `businessObject="Tasks"`
- `displayName="Delete task"` `action="DELETE"` `businessObject="Tasks"`
- `displayName="Clear completed tasks"` `action="CUSTOM"` `businessObject="Tasks"`
- `displayName="Reorder task"` `action="CUSTOM"` `businessObject="Tasks"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:googletasks`.
- The policy file is available at `EveryPolicy/googletasks.policyxml`.
- Note: this connector uses `authenticationMethod="BASIC_API_KEY"` with service account credentials (user email, service account email, and private key). It also supports `BASIC_OAUTH` and `OAUTH2_WEB` authentication.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="googletasks" policyTemplate="online_v1_basic_api_key" policyType="googletasks" shortDescription="" version="">
     <credentialName/>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC_API_KEY</authenticationMethod>
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
- [`loopback-connector-googletasks/descriptors/googletasks.json`](../loopback-connector-googletasks/descriptors/googletasks.json)
- [`loopback-connector-googletasks/descriptors/googletasks.yaml`](../loopback-connector-googletasks/descriptors/googletasks.yaml)
- [`loopback-connector-googletasks/lib/openapi/connector.json`](../loopback-connector-googletasks/lib/openapi/connector.json)
- [`loopback-connector-googletasks/lib/constants.json`](../loopback-connector-googletasks/lib/constants.json)
- [`appconnect-connector-googletasks/descriptors/googletasks.json`](../appconnect-connector-googletasks/descriptors/googletasks.json)
- [`appconnect-connector-googletasks/descriptors/googletasks.yaml`](../appconnect-connector-googletasks/descriptors/googletasks.yaml)
- [`appconnect-connector-googletasks/lib/openapi/connector.json`](../appconnect-connector-googletasks/lib/openapi/connector.json)
- [`EveryPolicy/googletasks.policyxml`](../EveryPolicy/googletasks.policyxml)
