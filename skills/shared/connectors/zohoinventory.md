# Zoho Inventory

## Purpose
Connector-specific rules for Zoho Inventory Request nodes.

## When to use
Use this document when the requested ACE flow includes a Zoho Inventory Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Zoho Inventory Request node

## Connector type
Zoho Inventory uses the `LoopbackNative` discovery protocol with an OpenAPI spec. Operations are expressed using `summary`, `action`, and `model` attributes on the node.

## Allowed operations
The following combinations are allowed for Zoho Inventory Request nodes:

- `displayName="Create item"` `action="create"` `businessObject="Items"`
- `displayName="Retrieve items"` `action="retrievewithwhere"` `businessObject="Items"`
- `displayName="Create sales order"` `action="create"` `businessObject="Sales orders"`
- `displayName="Retrieve sales orders"` `action="retrievewithwhere"` `businessObject="Sales orders"`
- `displayName="Create contact"` `action="create"` `businessObject="Contacts"`
- `displayName="Retrieve contacts"` `action="retrievewithwhere"` `businessObject="Contacts"`
- `displayName="Create package"` `action="create"` `businessObject="Packages"`
- `displayName="Create contact person"` `action="create"` `businessObject="Contact persons"`
- `displayName="Retrieve contact persons"` `action="retrievewithwhere"` `businessObject="Contact persons"`
- `displayName="Retrieve taxes"` `action="retrievewithwhere"` `businessObject="Taxes"`
- `displayName="Retrieve currencies"` `action="retrievewithwhere"` `businessObject="Currencies"`
- `displayName="Create purchase order"` `action="create"` `businessObject="Purchase orders"`
- `displayName="Retrieve purchase orders"` `action="retrievewithwhere"` `businessObject="Purchase orders"`
- `displayName="Retrieve warehouses"` `action="retrievewithwhere"` `businessObject="Warehouses"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Zohoinventory1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Zohoinventory1" policyTemplate="online_v1_basic_oauth" policyType="zohoinventory" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <apiUrl>https://www.zohoapis.com/inventory/v1</apiUrl>
        <tokenUrl>https://accounts.zoho.com/oauth/v2</tokenUrl>
        <domainName/>
        <isTlsEnabled>false</isTlsEnabled>
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
