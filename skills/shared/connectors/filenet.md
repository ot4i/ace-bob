# IBM FileNet Content Manager

## Purpose
Connector-specific rules for IBM FileNet Content Manager Request nodes.

## When to use
Use this document when the requested ACE flow includes an IBM FileNet Content Manager Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- IBM FileNet Content Manager Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_filenet.msgnode`
- `applicationConnectorType="filenet"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For IBM FileNet Content Manager Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for IBM FileNet Content Manager Request nodes:

- `displayName="Create document"` `action="CREATE"` `businessObject="document"`
- `displayName="Retrieve documents"` `action="RETRIEVEALL"` `businessObject="document"`
- `displayName="Update document"` `action="UPDATEALL"` `businessObject="document"`
- `displayName="Delete document"` `action="DELETEALL"` `businessObject="document"`
- `displayName="Check out document"` `action="CHECKOUTDOCUMENT"` `businessObject="document"`
- `displayName="Cancel document check out"` `action="CANCELDOCUMENTCHECKOUT"` `businessObject="document"`
- `displayName="Check in document"` `action="CHECKINDOCUMENT"` `businessObject="document"`
- `displayName="Download content"` `action="DOWNLOADCONTENT"` `businessObject="document"`
- `displayName="Create folder"` `action="CREATE"` `businessObject="folder"`
- `displayName="Retrieve folders"` `action="RETRIEVEALL"` `businessObject="folder"`
- `displayName="Update folder"` `action="UPDATEALL"` `businessObject="folder"`
- `displayName="Delete folder"` `action="DELETEALL"` `businessObject="folder"`
- `displayName="Retrieve ACL of document"` `action="RETRIEVEALL"` `businessObject="documentacl"`
- `displayName="Retrieve ACL of folder"` `action="RETRIEVEALL"` `businessObject="folderacl"`
- `displayName="Retrieve group members"` `action="RETRIEVEALL"` `businessObject="groupmembers"`
- `displayName="Retrieve role members"` `action="RETRIEVEALL"` `businessObject="rolemembers"`
- `displayName="Retrieve users"` `action="LISTUSERS"` `businessObject="users"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Filenet1`.
- This connector uses `applicationType="online"` and `authenticationMethod="BASIC"`. The policy includes an `<endpointUrl>` field for the FileNet GraphQL server URL.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Filenet1" policyTemplate="online_v1_basic" policyType="filenet" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
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