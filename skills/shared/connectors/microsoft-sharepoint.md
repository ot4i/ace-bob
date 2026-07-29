# Microsoft SharePoint

## Purpose
Connector-specific rules for Microsoft SharePoint Request and Input nodes.

## When to use
Use this document when the requested ACE flow includes a Microsoft SharePoint Request node or Microsoft SharePoint Input node.

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

## Schema file requirements
For Microsoft SharePoint Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Microsoft SharePoint Request nodes:

- `displayName="Retrieve all folders"` `action="RETRIEVEALL"` `businessObject="FolderCollection"`
- `displayName="Retrieve all files"` `action="RETRIEVEALL"` `businessObject="FileCollection"`
- `displayName="Retrieve all sites"` `action="RETRIEVEALL"` `businessObject="SiteCollection"`
- `displayName="Retrieve all lists"` `action="RETRIEVEALL"` `businessObject="ListCollection"`
- `displayName="Retrieve all list items"` `action="RETRIEVEALL"` `businessObject="ListItemCollection"`
- `displayName="Retrieve all list item attachments"` `action="RETRIEVEALL"` `businessObject="ListItemAttachmentCollection"`
- `displayName="Create file"` `action="CREATE"` `businessObject="File"`
- `displayName="Retrieve files"` `action="RETRIEVEALL"` `businessObject="File"`
- `displayName="Delete file"` `action="DELETEALL"` `businessObject="File"`
- `displayName="Update file"` `action="UPDATEALL"` `businessObject="File"`
- `displayName="Download file"` `action="DOWNLOADFILE"` `businessObject="File"`
- `displayName="Rename file"` `action="RENAMEFILE"` `businessObject="File"`
- `displayName="Share file"` `action="SHAREFILE"` `businessObject="File"`
- `displayName="Create folder"` `action="CREATE"` `businessObject="Folder"`
- `displayName="Retrieve folders"` `action="RETRIEVEALL"` `businessObject="Folder"`
- `displayName="Delete folder"` `action="DELETEALL"` `businessObject="Folder"`
- `displayName="Update folder"` `action="UPDATEALL"` `businessObject="Folder"`
- `displayName="Create site"` `action="CREATE"` `businessObject="Site"`
- `displayName="Retrieve sites"` `action="RETRIEVEALL"` `businessObject="Site"`
- `displayName="Delete site"` `action="DELETEALL"` `businessObject="Site"`
- `displayName="Update site"` `action="UPDATEALL"` `businessObject="Site"`
- `displayName="Create list"` `action="CREATE"` `businessObject="List"`
- `displayName="Retrieve lists"` `action="RETRIEVEALL"` `businessObject="List"`
- `displayName="Delete list"` `action="DELETEALL"` `businessObject="List"`
- `displayName="Update list"` `action="UPDATEALL"` `businessObject="List"`
- `displayName="Create list item"` `action="CREATE"` `businessObject="ListItem"`
- `displayName="Retrieve list items"` `action="RETRIEVEALL"` `businessObject="ListItem"`
- `displayName="Delete list item"` `action="DELETEALL"` `businessObject="ListItem"`
- `displayName="Update list item"` `action="UPDATEALL"` `businessObject="ListItem"`
- `displayName="Create list item attachment"` `action="CREATE"` `businessObject="ListItemAttachment"`
- `displayName="Retrieve all the list item attachments"` `action="RETRIEVEALL"` `businessObject="ListItemAttachment"`
- `displayName="Delete all the list item attachments"` `action="DELETEALL"` `businessObject="ListItemAttachment"`
- `displayName="Update list item attachment"` `action="UPDATEALL"` `businessObject="ListItemAttachment"`
- `displayName="Download list item attachment"` `action="DOWNLOADLISTITEMATTACHMENT"` `businessObject="ListItemAttachment"`
- `displayName="Retrieve all the folder items"` `action="RETRIEVEALL"` `businessObject="FolderItem"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Retrieve Acl"` `action="RETRIEVEALL"` `businessObject="Acl"`
- `displayName="Retrieve shared links"` `action="RETRIEVEALL"` `businessObject="SharedLinks"`
- `displayName="Search files"` `action="RETRIEVEALL"` `businessObject="SearchFiles"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:MicrosoftSharePoint1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="MicrosoftSharePoint1" policyTemplate="online_v1_basic_oauth" policyType="mssharepoint" shortDescription="" version="">
     <credentialName>MicrosoftSharePointCredential</credentialName>
     <applicationVersion>2019</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC_OAUTH</authenticationMethod>
     <endpointUrl>https://YourSharePointHost:8443</endpointUrl>
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
