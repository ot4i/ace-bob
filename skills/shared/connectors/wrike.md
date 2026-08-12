# Wrike

## Purpose
Connector-specific rules for Wrike Request nodes.

## When to use
Use this document when the requested ACE flow includes a Wrike Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Wrike Request node

## Connector type
Wrike uses the `LoopbackNative` discovery protocol with an OpenAPI spec. Operations are expressed using `summary`, `action`, and `model` attributes on the node.

## Allowed operations
The following combinations are allowed for Wrike Request nodes:

- `displayName="Retrieve all tasks"` `action="retrievewithwhere"` `businessObject="Tasks"`
- `displayName="Create task"` `action="create"` `businessObject="Tasks"`
- `displayName="Retrieve tasks in a folder"` `action="retrievewithwhere"` `businessObject="Tasks"`
- `displayName="Retrieve task by ID"` `action="retrieve"` `businessObject="Tasks"`
- `displayName="Update task"` `action="update"` `businessObject="Tasks"`
- `displayName="Delete task"` `action="delete"` `businessObject="Tasks"`
- `displayName="Retrieve all folders or projects"` `action="retrievewithwhere"` `businessObject="Folders or projects"`
- `displayName="Retrieve folder or project by ID"` `action="retrieve"` `businessObject="Folders or projects"`
- `displayName="Create sub folder or project"` `action="create"` `businessObject="Folders or projects"`
- `displayName="Update folder or project"` `action="update"` `businessObject="Folders or projects"`
- `displayName="Delete folder or project"` `action="delete"` `businessObject="Folders or projects"`
- `displayName="Create work schedule"` `action="create"` `businessObject="Work schedules"`
- `displayName="Retrieve all work schedules"` `action="retrievewithwhere"` `businessObject="Work schedules"`
- `displayName="Retrieve work schedule by ID"` `action="retrieve"` `businessObject="Work schedules"`
- `displayName="Update work schedule"` `action="update"` `businessObject="Work schedules"`
- `displayName="Delete work schedule"` `action="delete"` `businessObject="Work schedules"`
- `displayName="Create space"` `action="create"` `businessObject="Spaces"`
- `displayName="Retrieve all spaces"` `action="retrievewithwhere"` `businessObject="Spaces"`
- `displayName="Retrieve space by ID"` `action="retrieve"` `businessObject="Spaces"`
- `displayName="Update space"` `action="update"` `businessObject="Spaces"`
- `displayName="Delete space"` `action="delete"` `businessObject="Spaces"`
- `displayName="Retrieve all time logs"` `action="retrievewithwhere"` `businessObject="Time logs"`
- `displayName="Create time log"` `action="create"` `businessObject="Time logs"`
- `displayName="Retrieve time logs for a task"` `action="retrievewithwhere"` `businessObject="Time logs"`
- `displayName="Retrieve time logs for a folder"` `action="retrievewithwhere"` `businessObject="Time logs"`
- `displayName="Retrieve time log by ID"` `action="retrieve"` `businessObject="Time logs"`
- `displayName="Update time log"` `action="update"` `businessObject="Time logs"`
- `displayName="Delete time log"` `action="delete"` `businessObject="Time logs"`
- `displayName="Retrieve all comments"` `action="retrievewithwhere"` `businessObject="Comments"`
- `displayName="Create comment in a task"` `action="create"` `businessObject="Comments"`
- `displayName="Retrieve comments in a task"` `action="retrievewithwhere"` `businessObject="Comments"`
- `displayName="Create comment in a folder"` `action="create"` `businessObject="Comments"`
- `displayName="Retrieve comments in a folder"` `action="retrievewithwhere"` `businessObject="Comments"`
- `displayName="Retrieve comment by ID"` `action="retrieve"` `businessObject="Comments"`
- `displayName="Update comment"` `action="update"` `businessObject="Comments"`
- `displayName="Delete comment"` `action="delete"` `businessObject="Comments"`
- `displayName="Create group"` `action="create"` `businessObject="Groups"`
- `displayName="Retrieve all groups"` `action="retrievewithwhere"` `businessObject="Groups"`
- `displayName="Retrieve group by ID"` `action="retrieve"` `businessObject="Groups"`
- `displayName="Update group"` `action="update"` `businessObject="Groups"`
- `displayName="Delete group"` `action="delete"` `businessObject="Groups"`
- `displayName="Retrieve all approvals"` `action="retrievewithwhere"` `businessObject="Approvals"`
- `displayName="Create folder or project approval"` `action="create"` `businessObject="Approvals"`
- `displayName="Retrieve approvals in a folder or project"` `action="retrievewithwhere"` `businessObject="Approvals"`
- `displayName="Create task approval"` `action="create"` `businessObject="Approvals"`
- `displayName="Retrieve approvals in a task"` `action="retrievewithwhere"` `businessObject="Approvals"`
- `displayName="Retrieve approval by ID"` `action="retrieve"` `businessObject="Approvals"`
- `displayName="Update approval"` `action="update"` `businessObject="Approvals"`
- `displayName="Delete approval"` `action="delete"` `businessObject="Approvals"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Wrike1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Wrike1" policyTemplate="online_v1_basic_bearer" policyType="wrike" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_BEARER</authenticationMethod>
        <apiUrl>https://www.wrike.com/api/v4</apiUrl>
        <isTlsEnabled>false</isTlsEnabled>
        <endpointUrl/>
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
