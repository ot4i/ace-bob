# Box

## Purpose
Connector-specific rules for Box Request nodes.

## When to use
Use this document when the requested ACE flow includes a Box Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Box Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_box.msgnode`
- `applicationConnectorType="box"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Box Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Box Request nodes:

- `displayName="Create file"` `action="CREATE"` `businessObject="File"`
- `displayName="Retrieve file metadata"` `action="RETRIEVEALL"` `businessObject="File"`
- `displayName="Update files"` `action="UPDATEALL"` `businessObject="File"`
- `displayName="Delete files"` `action="DELETEALL"` `businessObject="File"`
- `displayName="Retrieve file content"` `action="DOWNLOADFILE"` `businessObject="File"`
- `displayName="Copy file"` `action="COPYFILE"` `businessObject="File"`
- `displayName="Retrieve trashed file"` `action="RETRIEVETRASHEDFILE"` `businessObject="File"`
- `displayName="Retrieve file versions"` `action="RETRIEVEALL"` `businessObject="FileVersions"`
- `displayName="Create folder"` `action="CREATE"` `businessObject="Folder"`
- `displayName="Retrieve folders"` `action="RETRIEVEALL"` `businessObject="Folder"`
- `displayName="Update folders"` `action="UPDATEALL"` `businessObject="Folder"`
- `displayName="Delete folders"` `action="DELETEALL"` `businessObject="Folder"`
- `displayName="Copy folder"` `action="COPYFOLDER"` `businessObject="Folder"`
- `displayName="Create bookmark"` `action="CREATE"` `businessObject="Web_Link"`
- `displayName="Retrieve bookmarks"` `action="RETRIEVEALL"` `businessObject="Web_Link"`
- `displayName="Update bookmarks"` `action="UPDATEALL"` `businessObject="Web_Link"`
- `displayName="Delete bookmarks"` `action="DELETEALL"` `businessObject="Web_Link"`
- `displayName="Retrieve folder items"` `action="RETRIEVEALL"` `businessObject="FolderItem"`
- `displayName="Create group"` `action="CREATE"` `businessObject="Group"`
- `displayName="Retrieve groups"` `action="RETRIEVE"` `businessObject="Group"`
- `displayName="Retrieve groups"` `action="RETRIEVEALL"` `businessObject="Group"`
- `displayName="Update groups"` `action="UPDATEALL"` `businessObject="Group"`
- `displayName="Delete groups"` `action="DELETEALL"` `businessObject="Group"`
- `displayName="Create user"` `action="CREATE"` `businessObject="User"`
- `displayName="Update users"` `action="UPDATEALL"` `businessObject="User"`
- `displayName="Retrieve users"` `action="RETRIEVE"` `businessObject="User"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Delete users"` `action="DELETEALL"` `businessObject="User"`
- `displayName="Create comment"` `action="CREATE"` `businessObject="Comment"`
- `displayName="Retrieve comments"` `action="RETRIEVEALL"` `businessObject="Comment"`
- `displayName="Update comments"` `action="UPDATEALL"` `businessObject="Comment"`
- `displayName="Delete comments"` `action="DELETEALL"` `businessObject="Comment"`
- `displayName="Create task"` `action="CREATE"` `businessObject="Task"`
- `displayName="Retrieve tasks"` `action="RETRIEVEALL"` `businessObject="Task"`
- `displayName="Update tasks"` `action="UPDATEALL"` `businessObject="Task"`
- `displayName="Delete tasks"` `action="DELETEALL"` `businessObject="Task"`
- `displayName="Create group membership"` `action="CREATE"` `businessObject="GroupMembership"`
- `displayName="Retrieve group memberships"` `action="RETRIEVEALL"` `businessObject="GroupMembership"`
- `displayName="Update group memberships"` `action="UPDATEALL"` `businessObject="GroupMembership"`
- `displayName="Delete group memberships"` `action="DELETEALL"` `businessObject="GroupMembership"`
- `displayName="Create task assignment"` `action="CREATE"` `businessObject="TaskAssignment"`
- `displayName="Retrieve task assignments"` `action="RETRIEVEALL"` `businessObject="TaskAssignment"`
- `displayName="Update task assignments"` `action="UPDATEALL"` `businessObject="TaskAssignment"`
- `displayName="Delete task assignments"` `action="DELETEALL"` `businessObject="TaskAssignment"`
- `displayName="Create collaboration"` `action="CREATE"` `businessObject="Collaboration"`
- `displayName="Retrieve collaborations"` `action="RETRIEVEALL"` `businessObject="Collaboration"`
- `displayName="Update collaborations"` `action="UPDATEALL"` `businessObject="Collaboration"`
- `displayName="Delete collaborations"` `action="DELETEALL"` `businessObject="Collaboration"`
- `displayName="Retrieve shared links"` `action="RETRIEVEALL"` `businessObject="SharedLink"`
- `displayName="Create or update shared link"` `action="UPSERTSHAREDLINK"` `businessObject="SharedLink"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Box1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="Box1" policyTemplate="admin_v1_basic_oauth" policyType="box" shortDescription="" version="">
     <credentialName>BoxCredential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>admin</applicationType>
     <authenticationMethod>BASIC_OAUTH</authenticationMethod>
  </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
