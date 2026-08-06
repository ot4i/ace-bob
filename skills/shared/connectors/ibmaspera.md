# IBM Aspera

## Purpose
Connector-specific rules for IBM Aspera Request and IBM Aspera Input nodes.

## When to use
Use this document when the requested ACE flow includes an IBM Aspera Request node or IBM Aspera Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- IBM Aspera Request node
- IBM Aspera Input node

## Required node attributes
### IBM Aspera Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_ibmaspera.msgnode`
- `applicationConnectorType="ibmaspera"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### IBM Aspera Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_ibmaspera.msgnode`
- `applicationConnectorType="ibmaspera"`

## Schema file requirements
For IBM Aspera Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for IBM Aspera Request nodes:

- `displayName="Create transfer"` `action="CREATE"` `businessObject="Transfers"`
- `displayName="Retrieve transfer information"` `action="RETRIEVEWITHWHERE"` `businessObject="Transfers"`
- `displayName="Retrieve transfer information by ID"` `action="RETRIEVE"` `businessObject="Transfers"`
- `displayName="Update transfer"` `action="UPDATE"` `businessObject="Transfers"`
- `displayName="Create permission"` `action="CREATE"` `businessObject="Permissions"`
- `displayName="Retrieve permission information"` `action="RETRIEVEWITHWHERE"` `businessObject="Permissions"`
- `displayName="Retrieve permission information by ID"` `action="RETRIEVE"` `businessObject="Permissions"`
- `displayName="Update permission"` `action="UPDATE"` `businessObject="Permissions"`
- `displayName="Delete permission"` `action="DELETE"` `businessObject="Permissions"`
- `displayName="Retrieve file metadata by ID"` `action="RETRIEVEWITHWHERE"` `businessObject="Files"`
- `displayName="Search files"` `action="RETRIEVEWITHWHERE"` `businessObject="Files"`
- `displayName="Create upload token"` `action="CREATE"` `businessObject="Tokens"`
- `displayName="Create download token"` `action="CREATE"` `businessObject="Tokens"`
- `displayName="Retrieve node configuration information"` `action="RETRIEVE"` `businessObject="Node configuration"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:IBMAspera1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="IBMAspera1" policyTemplate="online_v1_basic" policyType="ibmaspera" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <apiUrl/>
        <endpointUrl/>
        <acceptSelfSignedCerts>false</acceptSelfSignedCerts>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
