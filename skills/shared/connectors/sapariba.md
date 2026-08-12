# SAP Ariba

## Purpose
Connector-specific rules for SAP Ariba Request nodes.

## When to use
Use this document when the requested ACE flow includes a SAP Ariba Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- SAP Ariba Request node

## Required node attributes
### SAP Ariba Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_sapariba.msgnode`
- `applicationConnectorType="sapariba"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For SAP Ariba Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for SAP Ariba Request nodes.
All operations are custom actions (`type="customActions"`); there are no standard CRUD `action`/`businessObject` pairs.

- `displayName="Add users to group"` `businessObject="User"`
- `displayName="Update or create users"` `businessObject="User"`
- `displayName="Remove users from group"` `businessObject="User"`
- `displayName="Remove users"` `businessObject="User"`
- `displayName="Create sourcing project"` `businessObject="SourcingProject"`
- `displayName="Update sourcing project"` `businessObject="SourcingProject"`
- `displayName="Download award document"` `businessObject="SourcingProject"`
- `displayName="Update or create supplier"` `businessObject="Supplier"`
- `displayName="Download supplier profiles data"` `businessObject="Supplier"`
- `displayName="Create contract workspace"` `businessObject="ContractWorkspace"`
- `displayName="Update contract workspace"` `businessObject="ContractWorkspace"`
- `displayName="Download organizations data"` `businessObject="Organization"`
- `displayName="Update or create organizations"` `businessObject="Organization"`
- `displayName="Remove organizations"` `businessObject="Organization"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:SapAriba1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="SapAriba1" policyTemplate="online_v1_basic" policyType="sapariba" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <endpointUrl/>
        <tenantId/>
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
