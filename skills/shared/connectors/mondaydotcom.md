# Monday.com

## Purpose
Connector-specific rules for Monday.com Request and Monday.com Input nodes.

## When to use
Use this document when the requested ACE flow includes a Monday.com Request node or Monday.com Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Monday.com Request node
- Monday.com Input node

## Required node attributes
### Monday.com Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_mondaydotcom.msgnode`
- `applicationConnectorType="mondaydotcom"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Monday.com Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_mondaydotcom.msgnode`
- `applicationConnectorType="mondaydotcom"`

## Schema file requirements
For Monday.com Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Monday.com Request nodes:

- `displayName="Retrieve boards"` `action="RETRIEVEALL"` `businessObject="Board"`
- `displayName="Create board"` `action="CREATE_BOARD"` `businessObject="Board"`
- `displayName="Update board"` `action="UPDATE_BOARD"` `businessObject="Board"`
- `displayName="Archive board"` `action="ARCHIVE_BOARD"` `businessObject="Board"`
- `displayName="Delete board"` `action="DELETE_BOARD"` `businessObject="Board"`
- `displayName="Retrieve groups"` `action="RETRIEVEALL"` `businessObject="Group"`
- `displayName="Create group"` `action="CREATE_GROUP"` `businessObject="Group"`
- `displayName="Archive group"` `action="ARCHIVE_GROUP"` `businessObject="Group"`
- `displayName="Delete group"` `action="DELETE_GROUP"` `businessObject="Group"`
- `displayName="Retrieve items"` `action="RETRIEVEALL"` `businessObject="Item"`
- `displayName="Create item"` `action="CREATE_ITEM"` `businessObject="Item"`
- `displayName="Update item"` `action="UPDATEALL"` `businessObject="Item"`
- `displayName="Delete item"` `action="DELETE_ITEM"` `businessObject="Item"`
- `displayName="Archive item"` `action="ARCHIVE_ITEM"` `businessObject="Item"`
- `displayName="Move item to group"` `action="MOVE_ITEM_TO_GROUP"` `businessObject="Item"`
- `displayName="Create subitem"` `action="CREATE_SUBITEM"` `businessObject="Item"`
- `displayName="Clear item updates"` `action="CLEAR_ITEM_UPDATES"` `businessObject="Item"`
- `displayName="Retrieve item updates"` `action="RETRIEVEALL"` `businessObject="Update"`
- `displayName="Create update"` `action="CREATE_UPDATE"` `businessObject="Update"`
- `displayName="Delete update"` `action="DELETE_UPDATE"` `businessObject="Update"`
- `displayName="Add file to update"` `action="ADD_FILE_TO_UPDATE"` `businessObject="ItemUpdateFile"`
- `displayName="Download update file"` `action="DOWNLOADUPDATEFILE"` `businessObject="ItemUpdateFile"`
- `displayName="Add file to column"` `action="ADD_FILE_TO_COLUMN"` `businessObject="ItemFile"`
- `displayName="Download file"` `action="DOWNLOADFILE"` `businessObject="ItemFile"`
- `displayName="Retrieve teams"` `action="RETRIEVEALL"` `businessObject="Team"`
- `displayName="Add teams to workspace"` `action="ADD_TEAMS_TO_WORKSPACE"` `businessObject="Team"`
- `displayName="Delete teams from workspace"` `action="DELETE_TEAMS_FROM_WORKSPACE"` `businessObject="Team"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Add users to workspace"` `action="ADD_USERS_TO_WORKSPACE"` `businessObject="User"`
- `displayName="Delete users from workspace"` `action="DELETE_USERS_FROM_WORKSPACE"` `businessObject="User"`
- `displayName="Add subscribers to board"` `action="ADD_SUBSCRIBERS_TO_BOARD"` `businessObject="User"`
- `displayName="Delete subscribers from board"` `action="DELETE_SUBSCRIBERS_FROM_BOARD"` `businessObject="User"`
- `displayName="Create workspace"` `action="CREATE_WORKSPACE"` `businessObject="Workspace"`
- `displayName="Retrieve activity logs"` `action="RETRIEVEALL"` `businessObject="ActivityLog"`

The following combinations are allowed for Monday.com Input nodes:

- `displayName="New item"` `action="CREATED"` `businessObject="Item"`
- `displayName="Updated item"` `action="UPDATED"` `businessObject="Item"`
- `displayName="Deleted item"` `action="DELETED"` `businessObject="Item"`
- `displayName="New subitem"` `action="CREATED"` `businessObject="Subitem"`
- `displayName="Updated subitem"` `action="UPDATED"` `businessObject="Subitem"`
- `displayName="Deleted subitem"` `action="DELETED"` `businessObject="Subitem"`
- `displayName="New board"` `action="CREATED"` `businessObject="Board"`
- `displayName="Updated board"` `action="UPDATED"` `businessObject="Board"`
- `displayName="Deleted board"` `action="DELETED"` `businessObject="Board"`
- `displayName="New subitem board"` `action="CREATED"` `businessObject="SubitemBoard"`
- `displayName="Updated subitem board"` `action="UPDATED"` `businessObject="SubitemBoard"`
- `displayName="Deleted subitem board"` `action="DELETED"` `businessObject="SubitemBoard"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Mondaydotcom1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Mondaydotcom1" policyTemplate="online_v1_basic" policyType="mondaydotcom" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
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
