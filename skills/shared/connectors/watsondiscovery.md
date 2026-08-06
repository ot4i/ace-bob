# Watson Discovery

## Purpose
Connector-specific rules for Watson Discovery Request nodes.

## When to use
Use this document when the requested ACE flow includes a Watson Discovery Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Watson Discovery Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_watsondiscovery.msgnode`
- `applicationConnectorType="watsondiscovery"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Watson Discovery Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The connector supports two API versions. The version is selected at account connection time.

### v1 operations
The following combinations are allowed for Watson Discovery Request nodes using API v1:

- `displayName="Add document"` `action="CREATE"` `businessObject="Document"`
- `displayName="Retrieve documents"` `action="RETRIEVEALL"` `businessObject="Document"`
- `displayName="Retrieve documents"` `action="RETRIEVE"` `businessObject="Document"`
- `displayName="Update or create document"` `action="UPSERTWITHWHERE"` `businessObject="Document"`
- `displayName="Update document"` `action="UPDATEALL"` `businessObject="Document"`
- `displayName="Update document"` `action="UPDATE"` `businessObject="Document"`
- `displayName="Delete document"` `action="DELETEALL"` `businessObject="Document"`
- `displayName="Retrieve collections"` `action="RETRIEVEALL"` `businessObject="Collection"`
- `displayName="Retrieve environments"` `action="RETRIEVEALL"` `businessObject="Environment"`

### v2 operations
The following combinations are allowed for Watson Discovery Request nodes using API v2:

- `displayName="Add project"` `action="CREATE"` `businessObject="Project"`
- `displayName="Retrieve projects"` `action="RETRIEVEALL"` `businessObject="Project"`
- `displayName="Update project"` `action="UPDATEALL"` `businessObject="Project"`
- `displayName="Delete project"` `action="DELETEALL"` `businessObject="Project"`
- `displayName="Add collection"` `action="CREATE"` `businessObject="Collection"`
- `displayName="Retrieve collections"` `action="RETRIEVEALL"` `businessObject="Collection"`
- `displayName="Update collection"` `action="UPDATEALL"` `businessObject="Collection"`
- `displayName="Delete collection"` `action="DELETEALL"` `businessObject="Collection"`
- `displayName="Add document"` `action="CREATE"` `businessObject="Document"`
- `displayName="Retrieve documents"` `action="RETRIEVEALL"` `businessObject="Document"`
- `displayName="Retrieve documents"` `action="RETRIEVE"` `businessObject="Document"`
- `displayName="Update or create document"` `action="UPSERTWITHWHERE"` `businessObject="Document"`
- `displayName="Update document"` `action="UPDATEALL"` `businessObject="Document"`
- `displayName="Update document"` `action="UPDATE"` `businessObject="Document"`
- `displayName="Delete document"` `action="DELETEALL"` `businessObject="Document"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Watsondiscovery1`.
- This connector uses `applicationType="online"` and `authenticationMethod="BASIC"`. The policy includes an `<endpointUrl>` field for the Watson Discovery service base URL.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Watsondiscovery1" policyTemplate="online_v1_basic" policyType="watsondiscovery" shortDescription="" version="">
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
