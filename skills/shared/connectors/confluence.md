# Confluence

## Purpose
Connector-specific rules for Confluence Request nodes.

## When to use
Use this document when the requested ACE flow includes a Confluence Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Confluence Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_confluence.msgnode`
- `applicationConnectorType="confluence"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Confluence Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Confluence Request nodes:

- `displayName="Create space"` `action="CREATE"` `businessObject="Space"`
- `displayName="Retrieve spaces"` `action="RETRIEVEALL"` `businessObject="Space"`
- `displayName="Update space"` `action="UPDATEALL"` `businessObject="Space"`
- `displayName="Delete space"` `action="DELETEALL"` `businessObject="Space"`
- `displayName="Download homepage content"` `action="DOWNLOADSPACECONTENT"` `businessObject="Space"`
- `displayName="Add space watcher"` `action="ADDSPACEWATCHER"` `businessObject="Space"`
- `displayName="Get space watch status"` `action="GETSPACEWATCHSTATUS"` `businessObject="Space"`
- `displayName="Remove space watcher"` `action="REMOVESPACEWATCHER"` `businessObject="Space"`
- `displayName="Create page"` `action="CREATE"` `businessObject="Page"`
- `displayName="Retrieve pages"` `action="RETRIEVEALL"` `businessObject="Page"`
- `displayName="Update page"` `action="UPDATEALL"` `businessObject="Page"`
- `displayName="Delete page"` `action="DELETEALL"` `businessObject="Page"`
- `displayName="Download page content"` `action="DOWNLOADPAGECONTENT"` `businessObject="Page"`
- `displayName="Add page watcher"` `action="ADDPAGEWATCHER"` `businessObject="Page"`
- `displayName="Get page watch status"` `action="GETPAGEWATCHSTATUS"` `businessObject="Page"`
- `displayName="Remove page watcher"` `action="REMOVEPAGEWATCHER"` `businessObject="Page"`
- `displayName="Copy page hierarchy"` `action="COPYPAGEHIERARCHY"` `businessObject="Page"`
- `displayName="Publish shared draft"` `action="PUBLISHSHAREDDRAFT"` `businessObject="Page"`
- `displayName="Publish legacy draft"` `action="PUBLISHLEGACYDRAFT"` `businessObject="Page"`
- `displayName="Create blog post"` `action="CREATE"` `businessObject="Blogpost"`
- `displayName="Retrieve blog posts"` `action="RETRIEVEALL"` `businessObject="Blogpost"`
- `displayName="Update blog post"` `action="UPDATEALL"` `businessObject="Blogpost"`
- `displayName="Delete blog post"` `action="DELETEALL"` `businessObject="Blogpost"`
- `displayName="Download blog post content"` `action="DOWNLOADBLOGPOSTCONTENT"` `businessObject="Blogpost"`
- `displayName="Add blog post watcher"` `action="ADDBLOGPOSTWATCHER"` `businessObject="Blogpost"`
- `displayName="Get blog post watch status"` `action="GETBLOGPOSTWATCHSTATUS"` `businessObject="Blogpost"`
- `displayName="Remove blog post watcher"` `action="REMOVEBLOGPOSTWATCHER"` `businessObject="Blogpost"`
- `displayName="Create comment"` `action="CREATE"` `businessObject="Comment"`
- `displayName="Retrieve comments"` `action="RETRIEVEALL"` `businessObject="Comment"`
- `displayName="Update comment"` `action="UPDATEALL"` `businessObject="Comment"`
- `displayName="Delete comment"` `action="DELETEALL"` `businessObject="Comment"`
- `displayName="Download comment content"` `action="DOWNLOADCOMMENTCONTENT"` `businessObject="Comment"`
- `displayName="Create attachment"` `action="CREATE"` `businessObject="Attachment"`
- `displayName="Retrieve attachments"` `action="RETRIEVEALL"` `businessObject="Attachment"`
- `displayName="Update attachment"` `action="UPDATEALL"` `businessObject="Attachment"`
- `displayName="Delete attachment"` `action="DELETEALL"` `businessObject="Attachment"`
- `displayName="Download attachment content"` `action="DOWNLOADATTACHMENTCONTENT"` `businessObject="Attachment"`
- `displayName="Create property"` `action="CREATE"` `businessObject="Property"`
- `displayName="Retrieve properties"` `action="RETRIEVEALL"` `businessObject="Property"`
- `displayName="Update property"` `action="UPDATEALL"` `businessObject="Property"`
- `displayName="Delete property"` `action="DELETEALL"` `businessObject="Property"`
- `displayName="Create restriction"` `action="CREATE"` `businessObject="Restriction"`
- `displayName="Retrieve restrictions"` `action="RETRIEVEALL"` `businessObject="Restriction"`
- `displayName="Update restriction"` `action="UPDATEALL"` `businessObject="Restriction"`
- `displayName="Delete restriction"` `action="DELETEALL"` `businessObject="Restriction"`
- `displayName="Retrieve versions"` `action="RETRIEVEALL"` `businessObject="Version"`
- `displayName="Retrieve groups"` `action="RETRIEVEALL"` `businessObject="Group"`
- `displayName="Retrieve group members"` `action="RETRIEVEALL"` `businessObject="GroupMembers"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Retrieve Anonymous Users"` `action="RETRIEVEALL"` `businessObject="AnonymousUser"`
- `displayName="Create label"` `action="CREATE"` `businessObject="Label"`
- `displayName="Retrieve labels"` `action="RETRIEVEALL"` `businessObject="Label"`
- `displayName="Delete label"` `action="DELETEALL"` `businessObject="Label"`
- `displayName="Add label watcher"` `action="ADDLABELWATCHER"` `businessObject="Label"`
- `displayName="Get label watch status"` `action="GETLABELWATCHSTATUS"` `businessObject="Label"`
- `displayName="Remove label watcher"` `action="REMOVELABELWATCHER"` `businessObject="Label"`
- `displayName="Change retention period"` `action="CHANGERETENTIONPERIOD"` `businessObject="AuditLog"`
- `displayName="Get retention period"` `action="GETRETENTIONPERIOD"` `businessObject="AuditLog"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Confluence1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Confluence1" policyTemplate="online_v1_basic" policyType="confluence" shortDescription="" version="">
        <credentialName>ConfluenceCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <endpointUrl/>
        <contextUrl/>
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
