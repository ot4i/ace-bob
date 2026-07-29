# IBM Cloudant

## Purpose
Connector-specific rules for IBM Cloudant Request nodes.

## When to use
Use this document when the requested ACE flow includes an IBM Cloudant Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- IBM Cloudant Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_cloudantdb.msgnode`
- `applicationConnectorType="cloudantdb"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For IBM Cloudant Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for IBM Cloudant Request nodes:

- `displayName="Create database"` `action="CREATE"` `businessObject="database"`
- `displayName="Retrieve databases"` `action="RETRIEVEALL"` `businessObject="database"`
- `displayName="Delete database"` `action="DELETEALL"` `businessObject="database"`
- `displayName="Create document"` `action="CREATE"` `businessObject="document"`
- `displayName="Retrieve documents"` `action="RETRIEVEALL"` `businessObject="document"`
- `displayName="Retrieve document"` `action="RETRIEVE"` `businessObject="document"`
- `displayName="Update document"` `action="UPDATEALL"` `businessObject="document"`
- `displayName="Update document"` `action="UPDATE"` `businessObject="document"`
- `displayName="Update or create document"` `action="UPSERTWITHWHERE"` `businessObject="document"`
- `displayName="Delete document"` `action="DELETEALL"` `businessObject="document"`
- `displayName="Create attachment"` `action="CREATE"` `businessObject="attachment"`
- `displayName="Retrieve attachments"` `action="RETRIEVEALL"` `businessObject="attachment"`
- `displayName="Retrieve attachment"` `action="RETRIEVE"` `businessObject="attachment"`
- `displayName="Update attachment"` `action="UPDATEALL"` `businessObject="attachment"`
- `displayName="Update attachment"` `action="UPDATE"` `businessObject="attachment"`
- `displayName="Update or create attachment"` `action="UPSERTWITHWHERE"` `businessObject="attachment"`
- `displayName="Delete attachment"` `action="DELETEALL"` `businessObject="attachment"`
- `displayName="Retrieve design documents"` `action="RETRIEVEALL"` `businessObject="design_document"`
- `displayName="Retrieve views"` `action="RETRIEVEALL"` `businessObject="view"`
- `displayName="Apply view"` `action="APPLYVIEW"` `businessObject="view"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:IBMCloudant1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="IBMCloudant1" policyTemplate="online_v1_basic" policyType="cloudantdb" shortDescription="" version="">
     <credentialName>IBMCloudantCredential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC</authenticationMethod>
     <hostname/>
  </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
