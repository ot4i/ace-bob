# IBM Planning Analytics

## Purpose
Connector-specific rules for IBM Planning Analytics Request nodes.

## When to use
Use this document when the requested ACE flow includes an IBM Planning Analytics Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- IBM Planning Analytics Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_planninganalytics.msgnode`
- `applicationConnectorType="planninganalytics"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For IBM Planning Analytics Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for IBM Planning Analytics Request nodes:

- `displayName="Retrieve all users"` `action="RETRIEVEALL"` `businessObject="Users"`
- `displayName="Create user"` `action="CREATE"` `businessObject="Users"`
- `displayName="Retrieve user by name"` `action="RETRIEVE"` `businessObject="Users"`
- `displayName="Delete user"` `action="DELETEALL"` `businessObject="Users"`
- `displayName="Retrieve all groups"` `action="RETRIEVEALL"` `businessObject="Groups"`
- `displayName="Create group"` `action="CREATE"` `businessObject="Groups"`
- `displayName="Retrieve group by name"` `action="RETRIEVE"` `businessObject="Groups"`
- `displayName="Delete group"` `action="DELETEALL"` `businessObject="Groups"`
- `displayName="Retrieve all cubes"` `action="RETRIEVEALL"` `businessObject="Cubes"`
- `displayName="Retrieve all files and folders"` `action="RETRIEVEALL"` `businessObject="Files"`
- `displayName="Retrieve file details by name"` `action="RETRIEVE"` `businessObject="Files"`
- `displayName="Delete file"` `action="DELETEALL"` `businessObject="Files"`
- `displayName="Create file"` `action="CREATE"` `businessObject="Files"`
- `displayName="Retrieve file content by name"` `action="RETRIEVE"` `businessObject="Files"`
- `displayName="Retrieve dimensions"` `action="RETRIEVEALL"` `businessObject="Dimensions"`
- `displayName="Retrieve hierarchies"` `action="RETRIEVEALL"` `businessObject="Hierarchies"`
- `displayName="Retrieve elements"` `action="RETRIEVEALL"` `businessObject="Elements"`
- `displayName="Create element"` `action="CREATE"` `businessObject="Elements"`
- `displayName="Delete element"` `action="DELETEALL"` `businessObject="Elements"`
- `displayName="Retrieve cell"` `action="readCell"` `businessObject="Cell"`
- `displayName="Update cell"` `action="updateCell"` `businessObject="Cell"`
- `displayName="Retrieve all processes"` `action="getProcesses"` `businessObject="ListProcesses"`
- `displayName="Retrieve process"` `action="getApiV1Process"` `businessObject="Process"`
- `displayName="Run process asynchronously"` `action="postApiV1ExecuteProcess"` `businessObject="Process"`
- `displayName="Retrieve status of triggered process by Async ID"` `action="getApiV1ProcessStatus"` `businessObject="Process"`
- `displayName="Retrieve all chores"` `action="getChores"` `businessObject="ListChores"`
- `displayName="Activate chore"` `action="postApiV1ActivateChore"` `businessObject="Chores"`
- `displayName="Deactivate chore"` `action="postApiV1DeactivateChore"` `businessObject="Chores"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Planninganalytics1`.
- This connector uses `applicationType="online"` and `authenticationMethod="BASIC_API_KEY"`. The policy includes an `<apiUrl>` field for the Planning Analytics API server URL.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Planninganalytics1" policyTemplate="online_v1_basic_api_key" policyType="planninganalytics" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_API_KEY</authenticationMethod>
        <apiUrl/>
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
