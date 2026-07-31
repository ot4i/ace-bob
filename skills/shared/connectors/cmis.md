# CMIS

## Purpose
Connector-specific rules for CMIS Request nodes.

## When to use
Use this document when the requested ACE flow includes a CMIS Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- CMIS Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_cmis.msgnode`
- `applicationConnectorType="cmis"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For CMIS Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for CMIS Request nodes:

- `displayName="Retrieve repositories"` `action="RETRIEVEALL"` `businessObject="repository"`
- `displayName="Create folder"` `action="CREATE"` `businessObject="Folder"`
- `displayName="Retrieve folders"` `action="RETRIEVEALL"` `businessObject="Folder"`
- `displayName="Delete folder"` `action="DELETEALL"` `businessObject="Folder"`
- `displayName="Update folder metadata"` `action="UPDATEFOLDER"` `businessObject="Folder"`
- `displayName="Create document"` `action="CREATE"` `businessObject="Document"`
- `displayName="Retrieve documents"` `action="RETRIEVEALL"` `businessObject="Document"`
- `displayName="Delete document"` `action="DELETEALL"` `businessObject="Document"`
- `displayName="Update document metadata"` `action="UPDATEMETADATA"` `businessObject="Document"`
- `displayName="Download document content"` `action="DOWNLOADFILE"` `businessObject="Document"`
- `displayName="Retrieve document ACL"` `action="RETRIEVEALL"` `businessObject="acl_document"`
- `displayName="Retrieve folder ACL"` `action="RETRIEVEALL"` `businessObject="acl_folder"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:cmis1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="cmis1" policyTemplate="default_v1_basic" policyType="cmis" shortDescription="" version="">
        <credentialName>CmisCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>default</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
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
