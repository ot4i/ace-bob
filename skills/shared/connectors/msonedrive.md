# Microsoft OneDrive for Business

## Purpose
Connector-specific rules for Microsoft OneDrive for Business Request nodes.

## When to use
Use this document when the requested ACE flow includes a Microsoft OneDrive for Business Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Microsoft OneDrive for Business Request node

## Required node attributes
### Microsoft OneDrive for Business Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_msonedrive.msgnode`
- `applicationConnectorType="msonedrive"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Microsoft OneDrive for Business Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Microsoft OneDrive for Business Request nodes:

- `displayName="Retrieve drives"` `action="RETRIEVEALL"` `businessObject="Drive"`
- `displayName="Create file"` `action="CREATE"` `businessObject="File"`
- `displayName="Retrieve files"` `action="RETRIEVEALL"` `businessObject="File"`
- `displayName="Retrieve file"` `action="RETRIEVE"` `businessObject="File"`
- `displayName="Update file"` `action="UPDATEALL"` `businessObject="File"`
- `displayName="Delete file"` `action="DELETEALL"` `businessObject="File"`
- `displayName="Retrieve folder items"` `action="RETRIEVEALL"` `businessObject="FolderItem"`
- `displayName="Create folder"` `action="CREATE"` `businessObject="Folder"`
- `displayName="Retrieve folders"` `action="RETRIEVEALL"` `businessObject="Folder"`
- `displayName="Retrieve folder"` `action="RETRIEVE"` `businessObject="Folder"`
- `displayName="Delete folder"` `action="DELETEALL"` `businessObject="Folder"`
- `displayName="Create permission"` `action="CREATE"` `businessObject="Permission"`
- `displayName="Retrieve permissions"` `action="RETRIEVEALL"` `businessObject="Permission"`
- `displayName="Retrieve permission"` `action="RETRIEVE"` `businessObject="Permission"`
- `displayName="Update permission"` `action="UPDATEALL"` `businessObject="Permission"`
- `displayName="Delete permission"` `action="DELETEALL"` `businessObject="Permission"`
- `displayName="Create shared link"` `action="CREATE"` `businessObject="SharedLink"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:MSOneDrive1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="MSOneDrive1" policyTemplate="online_v1_basic_oauth" policyType="msonedrive" shortDescription="" version="">
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
