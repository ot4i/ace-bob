# Businessmap

## Purpose
Connector-specific rules for Businessmap Request nodes.

## When to use
Use this document when the requested ACE flow includes a Businessmap Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Businessmap Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_businessmap.msgnode`
- `applicationConnectorType="businessmap"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Businessmap Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Businessmap Request nodes:

- `displayName="Retrieve all workspaces"` `action="RETRIEVEWITHWHERE"` `businessObject="Workspaces"`
- `displayName="Create workspace"` `action="CREATE"` `businessObject="Workspaces"`
- `displayName="Update workspace"` `action="UPDATE"` `businessObject="Workspaces"`
- `displayName="Retrieve workspace by ID"` `action="RETRIEVE"` `businessObject="Workspaces"`
- `displayName="Retrieve all boards"` `action="RETRIEVEWITHWHERE"` `businessObject="Boards"`
- `displayName="Create board"` `action="CREATE"` `businessObject="Boards"`
- `displayName="Retrieve board by ID"` `action="RETRIEVE"` `businessObject="Boards"`
- `displayName="Update board"` `action="UPDATE"` `businessObject="Boards"`
- `displayName="Delete board"` `action="DELETE"` `businessObject="Boards"`
- `displayName="Retrieve board tags"` `action="RETRIEVEWITHWHERE"` `businessObject="Board tags"`
- `displayName="Delete board tag"` `action="DELETE"` `businessObject="Board tags"`
- `displayName="Add tag to board"` `action="CUSTOM"` `businessObject="Board tags"`
- `displayName="Retrieve board tag by ID"` `action="CUSTOM"` `businessObject="Board tags"`
- `displayName="Retrieve board assignees"` `action="RETRIEVEWITHWHERE"` `businessObject="Board assignees"`
- `displayName="Assign user to board"` `action="CUSTOM"` `businessObject="Board assignees"`
- `displayName="Delete board assignee"` `action="DELETE"` `businessObject="Board assignees"`
- `displayName="Retrieve columns"` `action="RETRIEVEWITHWHERE"` `businessObject="Columns"`
- `displayName="Create column"` `action="CREATE"` `businessObject="Columns"`
- `displayName="Retrieve column by ID"` `action="RETRIEVE"` `businessObject="Columns"`
- `displayName="Update column"` `action="UPDATE"` `businessObject="Columns"`
- `displayName="Delete column"` `action="DELETE"` `businessObject="Columns"`
- `displayName="Retrieve lanes"` `action="RETRIEVEWITHWHERE"` `businessObject="Lanes"`
- `displayName="Create lane"` `action="CREATE"` `businessObject="Lanes"`
- `displayName="Retrieve lane by ID"` `action="RETRIEVE"` `businessObject="Lanes"`
- `displayName="Update lane"` `action="UPDATE"` `businessObject="Lanes"`
- `displayName="Delete lane"` `action="DELETE"` `businessObject="Lanes"`
- `displayName="Retrieve all users"` `action="RETRIEVEWITHWHERE"` `businessObject="Users"`
- `displayName="Retrieve user by ID"` `action="RETRIEVE"` `businessObject="Users"`
- `displayName="Update user"` `action="UPDATE"` `businessObject="Users"`
- `displayName="Delete user"` `action="DELETE"` `businessObject="Users"`
- `displayName="Invite new user"` `action="CUSTOM"` `businessObject="Users"`
- `displayName="Resend invitation to user"` `action="CUSTOM"` `businessObject="Users"`
- `displayName="Retrieve all stickers"` `action="RETRIEVEWITHWHERE"` `businessObject="Stickers"`
- `displayName="Create sticker"` `action="CREATE"` `businessObject="Stickers"`
- `displayName="Retrieve sticker by ID"` `action="RETRIEVE"` `businessObject="Stickers"`
- `displayName="Update sticker"` `action="UPDATE"` `businessObject="Stickers"`
- `displayName="Delete sticker"` `action="DELETE"` `businessObject="Stickers"`
- `displayName="Retrieve all tags"` `action="RETRIEVEWITHWHERE"` `businessObject="Tags"`
- `displayName="Create tag"` `action="CREATE"` `businessObject="Tags"`
- `displayName="Retrieve tag by ID"` `action="RETRIEVE"` `businessObject="Tags"`
- `displayName="Update tag"` `action="UPDATE"` `businessObject="Tags"`
- `displayName="Delete tag"` `action="DELETE"` `businessObject="Tags"`
- `displayName="Retrieve all teams"` `action="RETRIEVEWITHWHERE"` `businessObject="Teams"`
- `displayName="Create team"` `action="CREATE"` `businessObject="Teams"`
- `displayName="Retrieve team by ID"` `action="RETRIEVE"` `businessObject="Teams"`
- `displayName="Update team"` `action="UPDATE"` `businessObject="Teams"`
- `displayName="Delete team"` `action="DELETE"` `businessObject="Teams"`
- `displayName="Retrieve team users"` `action="RETRIEVEWITHWHERE"` `businessObject="Team users"`
- `displayName="Add user to team"` `action="CUSTOM"` `businessObject="Team users"`
- `displayName="Delete team user"` `action="DELETE"` `businessObject="Team users"`
- `displayName="Retrieve all cards"` `action="RETRIEVEWITHWHERE"` `businessObject="Cards"`
- `displayName="Create card"` `action="CREATE"` `businessObject="Cards"`
- `displayName="Retrieve card by ID"` `action="RETRIEVE"` `businessObject="Cards"`
- `displayName="Update card"` `action="UPDATE"` `businessObject="Cards"`
- `displayName="Delete card"` `action="DELETE"` `businessObject="Cards"`
- `displayName="Retrieve card comments"` `action="RETRIEVEWITHWHERE"` `businessObject="Card comments"`
- `displayName="Create card comment"` `action="CREATE"` `businessObject="Card comments"`
- `displayName="Retrieve card comment by ID"` `action="RETRIEVE"` `businessObject="Card comments"`
- `displayName="Update card comment"` `action="UPDATE"` `businessObject="Card comments"`
- `displayName="Delete card comment"` `action="DELETE"` `businessObject="Card comments"`
- `displayName="Retrieve card subtasks"` `action="RETRIEVEWITHWHERE"` `businessObject="Card subtasks"`
- `displayName="Create card subtask"` `action="CREATE"` `businessObject="Card subtasks"`
- `displayName="Retrieve card subtask by ID"` `action="RETRIEVE"` `businessObject="Card subtasks"`
- `displayName="Update card subtask"` `action="UPDATE"` `businessObject="Card subtasks"`
- `displayName="Delete card subtask"` `action="DELETE"` `businessObject="Card subtasks"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:businessmap1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="businessmap1" policyTemplate="online_v1_basic_api_key" policyType="businessmap" shortDescription="" version="">
        <credentialName>BusinessmapCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_API_KEY</authenticationMethod>
        <apiUrl/>
        <isTlsEnabled>false</isTlsEnabled>
        <endpointUrl/>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
