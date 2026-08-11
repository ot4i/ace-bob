# Microsoft Dynamics 365 for Sales

## Purpose
Connector-specific rules for Microsoft Dynamics 365 for Sales Request nodes.

## When to use
Use this document when the requested ACE flow includes a Microsoft Dynamics 365 for Sales Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Microsoft Dynamics 365 for Sales Request node

## Required node attributes
### Microsoft Dynamics 365 for Sales Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_msdynamicscrmrest.msgnode`
- `applicationConnectorType="msdynamicscrmrest"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Microsoft Dynamics 365 for Sales Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Microsoft Dynamics 365 for Sales Request nodes:

- `displayName="Create lead"` `action="CREATE"` `businessObject="Lead"`
- `displayName="Retrieve leads"` `action="RETRIEVEALL"` `businessObject="Lead"`
- `displayName="Retrieve lead"` `action="RETRIEVE"` `businessObject="Lead"`
- `displayName="Update lead"` `action="UPDATEALL"` `businessObject="Lead"`
- `displayName="Upsert lead"` `action="UPSERT"` `businessObject="Lead"`
- `displayName="Delete lead"` `action="DELETEALL"` `businessObject="Lead"`
- `displayName="Create account"` `action="CREATE"` `businessObject="Account"`
- `displayName="Retrieve accounts"` `action="RETRIEVEALL"` `businessObject="Account"`
- `displayName="Retrieve account"` `action="RETRIEVE"` `businessObject="Account"`
- `displayName="Update account"` `action="UPDATEALL"` `businessObject="Account"`
- `displayName="Upsert account"` `action="UPSERT"` `businessObject="Account"`
- `displayName="Delete account"` `action="DELETEALL"` `businessObject="Account"`
- `displayName="Create contact"` `action="CREATE"` `businessObject="Contact"`
- `displayName="Retrieve contacts"` `action="RETRIEVEALL"` `businessObject="Contact"`
- `displayName="Retrieve contact"` `action="RETRIEVE"` `businessObject="Contact"`
- `displayName="Update contact"` `action="UPDATEALL"` `businessObject="Contact"`
- `displayName="Upsert contact"` `action="UPSERT"` `businessObject="Contact"`
- `displayName="Delete contact"` `action="DELETEALL"` `businessObject="Contact"`
- `displayName="Create opportunity"` `action="CREATE"` `businessObject="Opportunity"`
- `displayName="Retrieve opportunities"` `action="RETRIEVEALL"` `businessObject="Opportunity"`
- `displayName="Retrieve opportunity"` `action="RETRIEVE"` `businessObject="Opportunity"`
- `displayName="Update opportunity"` `action="UPDATEALL"` `businessObject="Opportunity"`
- `displayName="Upsert opportunity"` `action="UPSERT"` `businessObject="Opportunity"`
- `displayName="Delete opportunity"` `action="DELETEALL"` `businessObject="Opportunity"`
- `displayName="Create product"` `action="CREATE"` `businessObject="Product"`
- `displayName="Retrieve products"` `action="RETRIEVEALL"` `businessObject="Product"`
- `displayName="Retrieve product"` `action="RETRIEVE"` `businessObject="Product"`
- `displayName="Update product"` `action="UPDATEALL"` `businessObject="Product"`
- `displayName="Upsert product"` `action="UPSERT"` `businessObject="Product"`
- `displayName="Delete product"` `action="DELETEALL"` `businessObject="Product"`
- `displayName="Create order"` `action="CREATE"` `businessObject="Order"`
- `displayName="Retrieve orders"` `action="RETRIEVEALL"` `businessObject="Order"`
- `displayName="Retrieve order"` `action="RETRIEVE"` `businessObject="Order"`
- `displayName="Update order"` `action="UPDATEALL"` `businessObject="Order"`
- `displayName="Upsert order"` `action="UPSERT"` `businessObject="Order"`
- `displayName="Delete order"` `action="DELETEALL"` `businessObject="Order"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:MSDynamicsCRMREST1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="MSDynamicsCRMREST1" policyTemplate="online_v1_basic_oauth" policyType="msdynamicscrmrest" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <endpointUrl/>
        <apiVersion>v9.1</apiVersion>
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
