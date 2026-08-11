# Microsoft SharePoint

## Purpose
Connector-specific rules for Microsoft SharePoint Request and Input nodes.

## When to use
Use this document when the requested ACE flow includes a Microsoft SharePoint Request node or a Microsoft SharePoint Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Microsoft SharePoint Request node
- Microsoft SharePoint Input node

## Required node attributes
### Microsoft SharePoint Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_mssharepoint.msgnode`
- `applicationConnectorType="mssharepoint"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Microsoft SharePoint Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_mssharepoint.msgnode`
- `applicationConnectorType="mssharepoint"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Microsoft SharePoint Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

For Microsoft SharePoint Input nodes:
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Microsoft SharePoint Request nodes:

- `displayName="Create site"` `action="CREATE"` `businessObject="Site"`
- `displayName="Retrieve sites"` `action="RETRIEVEALL"` `businessObject="Site"`
- `displayName="Retrieve site"` `action="RETRIEVE"` `businessObject="Site"`
- `displayName="Update site"` `action="UPDATEALL"` `businessObject="Site"`
- `displayName="Delete site"` `action="DELETEALL"` `businessObject="Site"`
- `displayName="Create list"` `action="CREATE"` `businessObject="List"`
- `displayName="Retrieve lists"` `action="RETRIEVEALL"` `businessObject="List"`
- `displayName="Retrieve list"` `action="RETRIEVE"` `businessObject="List"`
- `displayName="Update list"` `action="UPDATEALL"` `businessObject="List"`
- `displayName="Delete list"` `action="DELETEALL"` `businessObject="List"`
- `displayName="Create list item"` `action="CREATE"` `businessObject="ListItem"`
- `displayName="Retrieve list items"` `action="RETRIEVEALL"` `businessObject="ListItem"`
- `displayName="Retrieve list item"` `action="RETRIEVE"` `businessObject="ListItem"`
- `displayName="Update list item"` `action="UPDATEALL"` `businessObject="ListItem"`
- `displayName="Delete list item"` `action="DELETEALL"` `businessObject="ListItem"`
- `displayName="Create list item attachment"` `action="CREATE"` `businessObject="ListItemAttachment"`
- `displayName="Retrieve list item attachments"` `action="RETRIEVEALL"` `businessObject="ListItemAttachment"`
- `displayName="Retrieve list item attachment"` `action="RETRIEVE"` `businessObject="ListItemAttachment"`
- `displayName="Update list item attachment"` `action="UPDATEALL"` `businessObject="ListItemAttachment"`
- `displayName="Delete list item attachment"` `action="DELETEALL"` `businessObject="ListItemAttachment"`
- `displayName="Create folder"` `action="CREATE"` `businessObject="Folder"`
- `displayName="Retrieve folders"` `action="RETRIEVEALL"` `businessObject="Folder"`
- `displayName="Retrieve folder"` `action="RETRIEVE"` `businessObject="Folder"`
- `displayName="Update folder"` `action="UPDATEALL"` `businessObject="Folder"`
- `displayName="Delete folder"` `action="DELETEALL"` `businessObject="Folder"`
- `displayName="Create file"` `action="CREATE"` `businessObject="File"`
- `displayName="Retrieve files"` `action="RETRIEVEALL"` `businessObject="File"`
- `displayName="Retrieve file"` `action="RETRIEVE"` `businessObject="File"`
- `displayName="Update file"` `action="UPDATEALL"` `businessObject="File"`
- `displayName="Delete file"` `action="DELETEALL"` `businessObject="File"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Retrieve folder items"` `action="RETRIEVEALL"` `businessObject="FolderItem"`
- `displayName="Search files"` `action="RETRIEVEALL"` `businessObject="SearchFile"`

The following combinations are allowed for Microsoft SharePoint Input nodes:

- `displayName="New list"` `action="CREATED"` `businessObject="List"`
- `displayName="Updated list"` `action="UPDATED"` `businessObject="List"`
- `displayName="New or updated list"` `action="CREATED"` `businessObject="List"`
- `displayName="New list item"` `action="CREATED"` `businessObject="ListItem"`
- `displayName="Updated list item"` `action="UPDATED"` `businessObject="ListItem"`
- `displayName="New or updated list item"` `action="CREATED"` `businessObject="ListItem"`
- `displayName="New site"` `action="CREATED"` `businessObject="Site"`
- `displayName="Updated site"` `action="UPDATED"` `businessObject="Site"`
- `displayName="New or updated site"` `action="CREATED"` `businessObject="Site"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:MSSharePoint1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="MSSharePoint1" policyTemplate="online_v1_basic_oauth" policyType="mssharepoint" shortDescription="" version="">
        <credentialName/>
        <applicationVersion/>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <endpointUrl/>
        <siteCollectionUrl/>
        <domainName/>
        <workstationName/>
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
