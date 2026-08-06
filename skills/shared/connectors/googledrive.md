# Google Drive

## Purpose
Connector-specific rules for Google Drive Request nodes.

## When to use
Use this document when the requested ACE flow includes a Google Drive Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Google Drive Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_googledrive.msgnode`
- `applicationConnectorType="googledrive"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Google Drive Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Google Drive Request nodes:

- `displayName="Create file"` `action="CREATE"` `businessObject="Files"`
- `displayName="Retrieve files metadata"` `action="RETRIEVEALL"` `businessObject="Files"`
- `displayName="Retrieve file metadata"` `action="RETRIEVE"` `businessObject="Files"`
- `displayName="Update files"` `action="UPDATEALL"` `businessObject="Files"`
- `displayName="Delete files"` `action="DELETEALL"` `businessObject="Files"`
- `displayName="Delete file"` `action="DELETE"` `businessObject="Files"`
- `displayName="Download file content"` `action="DOWNLOADCONTENT"` `businessObject="Files"`
- `displayName="Create folder"` `action="CREATE"` `businessObject="Folder"`
- `displayName="Retrieve folders"` `action="RETRIEVEALL"` `businessObject="Folder"`
- `displayName="Update folders"` `action="UPDATEALL"` `businessObject="Folder"`
- `displayName="Delete folders"` `action="DELETEALL"` `businessObject="Folder"`
- `displayName="Delete folder"` `action="DELETE"` `businessObject="Folder"`
- `displayName="Create permission"` `action="CREATE"` `businessObject="Permission"`
- `displayName="Retrieve permissions"` `action="RETRIEVEALL"` `businessObject="Permission"`
- `displayName="Update permissions"` `action="UPDATEALL"` `businessObject="Permission"`
- `displayName="Delete permissions"` `action="DELETEALL"` `businessObject="Permission"`
- `displayName="Delete permission"` `action="DELETE"` `businessObject="Permission"`
- `displayName="Retrieve changes"` `action="RETRIEVEALL"` `businessObject="Change"`
- `displayName="Create comment"` `action="CREATE"` `businessObject="Comment"`
- `displayName="Retrieve comments"` `action="RETRIEVEALL"` `businessObject="Comment"`
- `displayName="Update comments"` `action="UPDATEALL"` `businessObject="Comment"`
- `displayName="Delete comments"` `action="DELETEALL"` `businessObject="Comment"`
- `displayName="Delete comment"` `action="DELETE"` `businessObject="Comment"`
- `displayName="Create reply"` `action="CREATE"` `businessObject="Reply"`
- `displayName="Retrieve replies"` `action="RETRIEVEALL"` `businessObject="Reply"`
- `displayName="Update replies"` `action="UPDATEALL"` `businessObject="Reply"`
- `displayName="Delete replies"` `action="DELETEALL"` `businessObject="Reply"`
- `displayName="Delete reply"` `action="DELETE"` `businessObject="Reply"`
- `displayName="Retrieve revisions"` `action="RETRIEVEALL"` `businessObject="Revision"`
- `displayName="Update revisions"` `action="UPDATEALL"` `businessObject="Revision"`
- `displayName="Delete revisions"` `action="DELETEALL"` `businessObject="Revision"`
- `displayName="Delete revision"` `action="DELETE"` `businessObject="Revision"`
- `displayName="Retrieve user information"` `action="RETRIEVEALL"` `businessObject="About"`
- `displayName="Retrieve all files"` `action="RETRIEVEALL"` `businessObject="filecollection"`
- `displayName="Retrieve all folders"` `action="RETRIEVEALL"` `businessObject="foldercollection"`
- `displayName="Retrieve all revisions"` `action="RETRIEVEALL"` `businessObject="revisioncollection"`
- `displayName="Retrieve all comments"` `action="RETRIEVEALL"` `businessObject="commentcollection"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="users"`
- `displayName="Retrieve folder items"` `action="RETRIEVEALL"` `businessObject="folderitem"`
- `displayName="Download file"` `action="DOWNLOADCONTENT"` `businessObject="Files"`
- `displayName="Generate page token"` `action="GENERATETOKEN"` `businessObject="generatetoken"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="users"`
- `displayName="Create user"` `action="CREATE"` `businessObject="users"`
- `displayName="Update user"` `action="UPDATEALL"` `businessObject="users"`
- `displayName="Delete user"` `action="DELETEALL"` `businessObject="users"`
- `displayName="Retrieve groups"` `action="RETRIEVEALL"` `businessObject="groups"`
- `displayName="Create group"` `action="CREATE"` `businessObject="groups"`
- `displayName="Update group"` `action="UPDATEALL"` `businessObject="groups"`
- `displayName="Delete group"` `action="DELETEALL"` `businessObject="groups"`
- `displayName="Retrieve members"` `action="RETRIEVEALL"` `businessObject="members"`
- `displayName="Create group member"` `action="CREATE"` `businessObject="members"`
- `displayName="Update group member"` `action="UPDATEALL"` `businessObject="members"`
- `displayName="Delete group member"` `action="DELETEALL"` `businessObject="members"`
- `displayName="Retrieve user photo"` `action="RETRIEVEALL"` `businessObject="photos"`
- `displayName="Update user photo"` `action="UPDATEALL"` `businessObject="photos"`
- `displayName="Delete user photo"` `action="DELETEALL"` `businessObject="photos"`
- `displayName="Retrieve calendars"` `action="RETRIEVEALL"` `businessObject="calendars"`
- `displayName="Create calendar"` `action="CREATE"` `businessObject="calendars"`
- `displayName="Update calendar"` `action="UPDATEALL"` `businessObject="calendars"`
- `displayName="Delete calendar"` `action="DELETEALL"` `businessObject="calendars"`
- `displayName="Create role"` `action="CREATE"` `businessObject="roles"`
- `displayName="Retrieve roles"` `action="RETRIEVEALL"` `businessObject="roles"`
- `displayName="Delete role"` `action="DELETEALL"` `businessObject="roles"`
- `displayName="Create role assignment"` `action="CREATE"` `businessObject="roleassignments"`
- `displayName="Retrieve role assignments"` `action="RETRIEVEALL"` `businessObject="roleassignments"`
- `displayName="Delete role assignment"` `action="DELETEALL"` `businessObject="roleassignments"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Googledrive1`.
- Note: this connector uses `applicationType="business"` and `policyTemplate="business_v1_basic_oauth"`, which differs from most other Google connectors. The policy also includes an `<apiVersion>` field (default `v3`).

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="Googledrive1" policyTemplate="business_v1_basic_oauth" policyType="googledrive" shortDescription="" version="">
     <credentialName/>
     <applicationVersion>v1</applicationVersion>
     <applicationType>business</applicationType>
     <authenticationMethod>BASIC_OAUTH</authenticationMethod>
     <apiVersion>v3</apiVersion>
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